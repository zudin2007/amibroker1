# AmiBroker Plugin Development Best Practices

Collection of best practices untuk mengembangkan reliable dan maintainable AmiBroker plugins.

## 📋 Daftar Isi

1. [Code Quality](#code-quality)
2. [Error Handling](#error-handling)
3. [Performance](#performance)
4. [Testing](#testing)
5. [Documentation](#documentation)
6. [Deployment](#deployment)

---

## ✨ Code Quality

### Naming Conventions

**DO:**
```csharp
// Clear, descriptive names
public class StockDataImporter { }
public AmiVar LoadQuotesFromCSV(string filePath) { }
private bool ValidateQuoteData(Quotation quote) { }
private List<Quotation> _cachedQuotes;
```

**DON'T:**
```csharp
// Ambiguous names
public class Plugin1 { }
public AmiVar Process(object x) { }
private bool Check(Quotation q) { }
private List<Quotation> temp;
```

### Code Organization

**DO:**
```csharp
public class MyPlugin : Plugin
{
    // 1. Fields/Properties
    private Dictionary<string, List<Quotation>> _cache;
    
    // 2. Constructor
    public MyPlugin() { }
    
    // 3. Override methods (in logical order)
    public override void GetPluginInfo(PluginInfo info) { }
    public override AmiVar GetQuotesEx(...) { }
    
    // 4. Private helper methods
    private bool LoadData(string source) { }
    private void UpdateCache(string key, List<Quotation> quotes) { }
}
```

**DON'T:**
```csharp
// Jumbled organization
public class MyPlugin : Plugin
{
    private void RandomHelper() { }
    public override AmiVar GetQuotesEx(...) { }
    private Dictionary<string> _cache;
    public override void GetPluginInfo(...) { }
    private void AnotherHelper() { }
}
```

### Comments & Documentation

**DO:**
```csharp
/// <summary>
/// Loads quote data from CSV file.
/// </summary>
/// <param name="filePath">Path to CSV file</param>
/// <returns>List of parsed quotations</returns>
public List<Quotation> LoadQuotesFromCSV(string filePath)
{
    // Implementation
}
```

**DON'T:**
```csharp
// Load quotes from file (too obvious)
public List<Quotation> LoadQuotesFromCSV(string filePath)
{
    // Implementation
}
```

---

## 🛡️ Error Handling

### Exception Handling Pattern

**DO:**
```csharp
public override AmiVar GetQuotesEx(
    string ticker,
    PluginStatus status,
    Quotation quote)
{
    try
    {
        ValidateInput(ticker);
        var quotes = FetchQuotes(ticker);
        
        foreach (var q in quotes)
        {
            if (!IsValidQuote(q))
                continue;
                
            status.AddQuote(q);
        }
        
        return AmiVar.Success();
    }
    catch (ArgumentException ex)
    {
        _lastError = $"Invalid input: {ex.Message}";
        Debug.WriteLine(_lastError);
        return AmiVar.Error();
    }
    catch (Exception ex)
    {
        _lastError = $"Unexpected error: {ex.Message}";
        Debug.WriteLine(_lastError);
        return AmiVar.Error();
    }
}
```

**DON'T:**
```csharp
// Silent failures
public override AmiVar GetQuotesEx(...)
{
    try
    {
        var quotes = FetchQuotes(ticker);
        foreach (var q in quotes)
            status.AddQuote(q);
        return AmiVar.Success();
    }
    catch { }  // Catch all, no error info
    return AmiVar.Error();
}
```

### Error Message Management

**DO:**
```csharp
private string _lastError = "";

public override void GetErrorMessage(ref StringBuilder errorMsg)
{
    if (!string.IsNullOrEmpty(_lastError))
    {
        errorMsg.Clear();
        errorMsg.Append(_lastError);
    }
}

private void LogError(string message)
{
    _lastError = message;
    System.Diagnostics.Debug.WriteLine($"Error: {message}");
}
```

**DON'T:**
```csharp
// No error tracking
public override void GetErrorMessage(ref StringBuilder errorMsg)
{
    // Empty implementation
}
```

---

## ⚡ Performance

### Caching Strategy

**DO:**
```csharp
private Dictionary<string, CachedData> _cache = 
    new Dictionary<string, CachedData>();
private DateTime _lastCacheUpdate = DateTime.MinValue;
private TimeSpan _cacheExpiry = TimeSpan.FromMinutes(60);

public AmiVar GetQuotesEx(string ticker, ...)
{
    // Check cache first
    if (_cache.ContainsKey(ticker) && 
        DateTime.Now - _lastCacheUpdate < _cacheExpiry)
    {
        return AmiVar.Success();  // Return cached
    }
    
    // Fetch fresh data
    var quotes = FetchFreshQuotes(ticker);
    _cache[ticker] = quotes;
    _lastCacheUpdate = DateTime.Now;
    
    return AmiVar.Success();
}
```

**DON'T:**
```csharp
// Always fetch, no caching
public AmiVar GetQuotesEx(string ticker, ...)
{
    var quotes = FetchQuotes(ticker);  // Always hits API
    return AmiVar.Success();
}
```

### Async Operations

**DO:**
```csharp
private async Task<List<Quotation>> FetchQuotesAsync(string ticker)
{
    using (var client = new HttpClient())
    {
        var response = await client.GetAsync($"api/quotes/{ticker}");
        response.EnsureSuccessStatusCode();
        
        var json = await response.Content.ReadAsStringAsync();
        return ParseQuotes(json);
    }
}
```

**DON'T:**
```csharp
// Blocking I/O (bad for performance)
private List<Quotation> FetchQuotes(string ticker)
{
    using (var client = new WebClient())
    {
        var json = client.DownloadString($"api/quotes/{ticker}");
        return ParseQuotes(json);
    }
}
```

### Resource Management

**DO:**
```csharp
public override void Release()
{
    // Clean up resources
    if (_fileStream != null)
    {
        _fileStream.Dispose();
        _fileStream = null;
    }
    
    if (_connection != null)
    {
        _connection.Close();
        _connection = null;
    }
    
    _cache.Clear();
}
```

**DON'T:**
```csharp
// No cleanup
public override void Release()
{
    // Empty
}
```

---

## 🧪 Testing

### Unit Testing Template

```csharp
[TestClass]
public class PluginTests
{
    private MyPlugin _plugin;
    
    [TestInitialize]
    public void Setup()
    {
        _plugin = new MyPlugin();
    }
    
    [TestCleanup]
    public void Cleanup()
    {
        _plugin?.Release();
    }
    
    [TestMethod]
    public void GetPluginInfo_ReturnsValidInfo()
    {
        // Arrange
        var info = new PluginInfo();
        
        // Act
        _plugin.GetPluginInfo(info);
        
        // Assert
        Assert.IsNotNull(info.Name);
        Assert.IsTrue(info.Version > 0);
    }
    
    [TestMethod]
    [ExpectedException(typeof(ArgumentNullException))]
    public void GetQuotesEx_WithNullTicker_ThrowsException()
    {
        _plugin.GetQuotesEx(null, null, null);
    }
}
```

### Integration Testing Checklist

```
□ Build plugin successfully
□ Deploy to AmiBroker Plugins folder
□ AmiBroker recognizes plugin
□ Load test data
□ Verify data in database
□ Check charts display correctly
□ Test error scenarios
□ Monitor performance
□ Check logs for errors
□ Test with different data sources
```

---

## 📚 Documentation

### README Template

```markdown
# My Plugin

Brief description of what plugin does.

## Features
- Feature 1
- Feature 2
- Feature 3

## Installation
1. Build plugin
2. Copy DLL to AmiBroker Plugins folder
3. Restart AmiBroker

## Usage
Explain how to use plugin.

## Configuration
Document any settings/configuration.

## Troubleshooting
Common issues and solutions.

## Requirements
- AmiBroker 6.0+
- .NET Framework 4.5+
```

### Code Documentation

```csharp
/// <summary>
/// Plugin for importing CSV stock data
/// </summary>
public class CSVImporterPlugin : Plugin
{
    /// <summary>
    /// Gets information about this plugin
    /// </summary>
    /// <param name="info">PluginInfo to populate</param>
    public override void GetPluginInfo(PluginInfo info)
    {
        // Implementation
    }
}
```

---

## 🚀 Deployment

### Release Checklist

```
Code Quality:
□ Code reviewed
□ All tests passing
□ No warnings in build
□ Performance tested

Documentation:
□ README updated
□ API documented
□ Examples provided
□ Troubleshooting guide

Testing:
□ Unit tests pass
□ Integration tests pass
□ Manual testing done
□ Edge cases handled

Release:
□ Version number updated
□ Release notes written
□ DLL signed (optional)
□ Setup created (if needed)
```

### Version Numbering

```
Version = Major.Minor.Patch

100 = 1.00
105 = 1.05
110 = 1.10
200 = 2.00

In code:
info.Version = 100;  // Version 1.00
info.Version = 105;  // Version 1.05
```

---

## 🎯 Common Anti-Patterns to Avoid

### Anti-Pattern 1: Silent Failures
```csharp
❌ try { } catch { }  // No error handling
✅ try { } catch (Exception ex) { LogError(ex.Message); }
```

### Anti-Pattern 2: No Input Validation
```csharp
❌ public void Process(string input) { DoSomething(input); }
✅ public void Process(string input) 
   { 
       if (string.IsNullOrEmpty(input)) throw new ArgumentException();
       DoSomething(input); 
   }
```

### Anti-Pattern 3: Blocking UI Thread
```csharp
❌ var data = FetchFromAPI();  // Synchronous, blocks UI
✅ await FetchFromAPIAsync();  // Asynchronous, doesn't block
```

### Anti-Pattern 4: Memory Leaks
```csharp
❌ public override void Release() { }  // No cleanup
✅ public override void Release() { _resource?.Dispose(); }
```

### Anti-Pattern 5: Hardcoded Values
```csharp
❌ private string _apiUrl = "http://myapi.com/quotes";
✅ private string _apiUrl = GetConfigValue("ApiUrl");
```

---

## 📊 Code Review Checklist

- [ ] Code follows naming conventions
- [ ] Error handling comprehensive
- [ ] No obvious bugs or logical errors
- [ ] Performance acceptable
- [ ] Thread-safe if needed
- [ ] Resources properly disposed
- [ ] Input validated
- [ ] Documented adequately
- [ ] Tests passing
- [ ] Version updated

---

## 🔗 Related Documentation

- [Getting Started](../docs/GETTING_STARTED.md)
- [Architecture](../docs/ARCHITECTURE.md)
- [API Reference](../docs/API_REFERENCE.md)

---

*Last Updated: August 2026*
