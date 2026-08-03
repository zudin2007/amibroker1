# AmiBroker .NET SDK Architecture

Penjelasan lengkap tentang arsitektur dan struktur internal AmiBroker .NET SDK.

## 📋 Daftar Isi

1. [High-Level Architecture](#high-level-architecture)
2. [Core Components](#core-components)
3. [Plugin Lifecycle](#plugin-lifecycle)
4. [Data Flow](#data-flow)
5. [Class Hierarchy](#class-hierarchy)

---

## 🏗️ High-Level Architecture

### System Overview

```
┌──────────────────────────────────────────────────────┐
│              AmiBroker (Main Application)            │
│                                                      │
│  ┌────────────────────────────────────────────────┐ │
│  │      Plugin Manager (Plugin Host)              │ │
│  │  - Load/Unload plugins                         │ │
│  │  - Manage plugin lifecycle                     │ │
│  │  - Route data/requests to plugins              │ │
│  └────────────────────────────────────────────────┘ │
│           ↓          ↓          ↓                   │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐   │
│  │   Plugin 1  │ │   Plugin 2  │ │   Plugin N  │   │
│  │  (Your DLL) │ │  (Your DLL) │ │  (Your DLL) │   │
│  └─────────────┘ └─────────────┘ └─────────────┘   │
│                                                      │
└──────────────────────────────────────────────────────┘
         ↓          ↓          ↓
   ┌──────────┬──────────┬──────────┐
   │ Database │   API    │ External │
   │ (Quotes) │ (Data)   │ Services │
   └──────────┴──────────┴──────────┘
```

### Communication Flow

```
AmiBroker
  ↓
[Calls Plugin Method]
  ↓
Plugin (Your Code)
  ↓
[Fetch/Process Data]
  ↓
[Return Results via AmiVar/Structures]
  ↓
AmiBroker
  ↓
[Update Database/UI]
```

---

## 🔧 Core Components

### 1. Plugin Base Class

```
┌─────────────────────────────────────┐
│      Plugin (Base Class)            │
├─────────────────────────────────────┤
│ Methods:                            │
│ • GetPluginInfo()                  │
│ • GetQuotesEx()                    │
│ • SetData()                        │
│ • Init()                           │
│ • Release()                        │
└─────────────────────────────────────┘
         ↓
  ┌──────────────────────────────┐
  │   Your Plugin Class          │
  │  (Inherits from Plugin)      │
  └──────────────────────────────┘
```

**Key Methods:**

```csharp
public abstract class Plugin
{
    // Required to override
    public abstract void GetPluginInfo(PluginInfo info);
    public abstract AmiVar GetQuotesEx(...);
    
    // Optional to override
    public virtual void Init();
    public virtual void Release();
    public virtual void GetErrorMessage(ref StringBuilder msg);
}
```

### 2. Data Models

**Main Data Structures:**

```
PluginInfo
├─ Name
├─ Author
├─ Version
├─ Copyright
└─ Flags

Quotation (Price Data)
├─ Date
├─ Open
├─ High
├─ Low
├─ Close
└─ Volume

PluginStatus (Processing Status)
├─ AddQuote()
├─ NotifyProgress()
└─ GetUser Data()

StockInfo (Security Info)
├─ Name
├─ Full Name
├─ Exchange
├─ Currency
└─ Type
```

### 3. Return Value System (AmiVar)

```csharp
public class AmiVar
{
    // Success
    public static AmiVar Success() { }
    
    // Error
    public static AmiVar Error() { }
    
    // Information
    public int GetInt()
    public double GetDouble()
    public string GetString()
}
```

**Usage:**

```csharp
// Return success
return AmiVar.Success();

// Return error
return AmiVar.Error();

// Return data
return new AmiVar(123);  // Integer
return new AmiVar(123.45);  // Double
return new AmiVar("Text");  // String
```

---

## 🔄 Plugin Lifecycle

### Plugin Loading & Initialization

```
1. [Startup]
   AmiBroker starts, scans Plugins folder
   ↓
2. [Discovery]
   Finds your Plugin.dll
   ↓
3. [Load Assembly]
   .NET Runtime loads DLL into memory
   ↓
4. [Create Instance]
   Reflection creates Plugin class instance
   ↓
5. [GetPluginInfo()]
   Your plugin provides info (name, version, etc)
   ↓
6. [Init()]
   Your plugin initializes resources
   ↓
7. [Ready]
   Plugin ready to receive requests
```

### Plugin Runtime

```
┌─────────────────────────────────────┐
│      Plugin Running                 │
│                                     │
│  GetQuotesEx() calls               │
│  ↓                                 │
│  Process data                      │
│  ↓                                 │
│  Return results                    │
│  ↓                                 │
│  Repeat...                         │
└─────────────────────────────────────┘
```

### Plugin Unloading

```
1. [Request Unload]
   User closes AmiBroker or disables plugin
   ↓
2. [Release()]
   Your plugin cleanup code called
   ↓
3. [Cleanup]
   Close files, disconnect APIs, free resources
   ↓
4. [Unload Assembly]
   .NET unloads DLL from memory
   ↓
5. [Done]
   Plugin completely removed
```

---

## 📊 Data Flow Examples

### Example 1: Load Price Data

```
User Request
  ↓
AmiBroker: "Get quotes for AAPL"
  ↓
Plugin.GetQuotesEx(ticker="AAPL", status, quote)
  ↓
Plugin Logic:
  1. Load data from source
  2. Parse into Quotation structure
  3. Call status.AddQuote(quote)
  4. Repeat for each quote
  5. Return success
  ↓
AmiBroker: Receives quotes
  ↓
Database: Store quotes
  ↓
UI: Display chart
```

### Example 2: Get Security Information

```
User Request
  ↓
AmiBroker: "Get info for AAPL"
  ↓
Plugin.SetData(ticker, StockInfo info)
  ↓
Plugin Logic:
  1. Fetch company info
  2. Fill StockInfo structure
  3. Return success/failure
  ↓
AmiBroker: Update security database
  ↓
UI: Show security details
```

---

## 🗂️ Class Hierarchy

### Plugin Classes (Models)

```
AmiVar
├─ Value: variant data
├─ IsValid: validity flag
└─ Methods:
   ├─ GetInt()
   ├─ GetDouble()
   └─ GetString()

AmiDate
├─ Date: date value
└─ Methods:
   ├─ FromString()
   └─ ToOLE()

AmiTime
├─ Time: time value
└─ Methods:
   ├─ FromString()
   └─ ToOLE()

Quotation
├─ Date: AmiDate
├─ Time: AmiTime
├─ Open: double
├─ High: double
├─ Low: double
├─ Close: double
├─ Volume: long
├─ OpenInt: long
└─ Bid/Ask: double

StockInfo
├─ Name: string
├─ FullName: string
├─ Exchange: string
├─ Currency: string
└─ Type: int

PluginInfo
├─ Name: string
├─ Author: string
├─ Version: int
├─ Copyright: string
├─ Description: string
├─ Type: PluginType
└─ Flags: PluginFlags

PluginStatus
├─ AddQuote(Quotation)
├─ NotifyProgress(int)
├─ GetUserData()
└─ SetUserData()
```

---

## 🔌 Plugin Types

### Data Feed Plugins
```
Purpose: Provide price/volume data
Entry Point: GetQuotesEx()
Responsibility: 
  - Connect to data source
  - Parse data format
  - Return OHLCV data

Example:
  - CSV File Importer
  - API Data Fetcher
  - Real-time Quote Server
```

### Information Plugins
```
Purpose: Provide security information
Entry Point: SetData()
Responsibility:
  - Fetch company/security info
  - Return StockInfo

Example:
  - Company Details
  - Dividend Information
  - Exchange Data
```

### Analysis Plugins
```
Purpose: Perform custom analysis
Entry Point: Analyze()
Responsibility:
  - Calculate indicators
  - Analyze patterns
  - Return results

Example:
  - Custom Risk Analysis
  - Portfolio Optimizer
  - Pattern Recognition
```

---

## 🔐 Thread Safety

### Threading Considerations

```
⚠️ AmiBroker may call plugin methods from different threads:

Thread 1 (Main UI): GetPluginInfo()
Thread 2 (Worker):  GetQuotesEx()
Thread 3 (Worker):  GetQuotesEx()
Thread N:           GetQuotesEx()

Guidelines:
✓ Use locks untuk shared resources
✓ Make collections thread-safe
✓ Avoid blocking operations
✗ Don't access UI from plugin threads
✗ Don't assume single-threaded access
```

**Thread-Safe Example:**

```csharp
private object _lockObject = new object();
private Dictionary<string, string> _cache = new Dictionary<string, string>();

public void AddToCache(string key, string value)
{
    lock (_lockObject)  // Ensure thread safety
    {
        _cache[key] = value;
    }
}

public string GetFromCache(string key)
{
    lock (_lockObject)  // Ensure thread safety
    {
        if (_cache.ContainsKey(key))
            return _cache[key];
        return null;
    }
}
```

---

## 🎯 Design Patterns

### Pattern 1: Singleton Plugin

```csharp
public class MySingletonPlugin : Plugin
{
    private static MySingletonPlugin _instance;
    
    public static MySingletonPlugin GetInstance()
    {
        if (_instance == null)
            _instance = new MySingletonPlugin();
        return _instance;
    }
    
    private MySingletonPlugin() { }
}
```

### Pattern 2: Data Caching

```csharp
public class CachedDataPlugin : Plugin
{
    private Dictionary<string, List<Quotation>> _cache;
    
    public override AmiVar GetQuotesEx(string ticker, ...)
    {
        if (_cache.ContainsKey(ticker))
        {
            // Return cached data
            return AmiVar.Success();
        }
        
        // Fetch fresh data
        var quotes = FetchData(ticker);
        _cache[ticker] = quotes;
        return AmiVar.Success();
    }
}
```

### Pattern 3: Error Handling

```csharp
public class SafePlugin : Plugin
{
    private string _lastError = "";
    
    public override void GetErrorMessage(ref StringBuilder errorMsg)
    {
        if (!string.IsNullOrEmpty(_lastError))
            errorMsg.Append(_lastError);
    }
    
    private void ReportError(string message)
    {
        _lastError = message;
        Debug.WriteLine($"Error: {message}");
    }
}
```

---

## 🧪 Testing Strategy

### Unit Testing

```csharp
[TestClass]
public class PluginTests
{
    [TestMethod]
    public void TestGetPluginInfo()
    {
        var plugin = new MyPlugin();
        var info = new PluginInfo();
        plugin.GetPluginInfo(info);
        
        Assert.IsNotNull(info.Name);
        Assert.IsTrue(info.Version > 0);
    }
    
    [TestMethod]
    public void TestGetQuotesEx()
    {
        var plugin = new MyPlugin();
        var result = plugin.GetQuotesEx("TEST", null, null);
        
        Assert.IsTrue(result.IsValid);
    }
}
```

### Integration Testing

```
1. Build DLL
2. Copy to AmiBroker Plugins folder
3. Restart AmiBroker
4. Load plugin
5. Request data
6. Verify results in database
7. Check charts display correct data
```

---

## 📈 Performance Optimization

### Tips

1. **Minimize Processing**
   - Cache data when possible
   - Avoid re-computing
   - Use efficient algorithms

2. **Asynchronous Operations**
   - Use async/await untuk I/O
   - Don't block UI thread
   - Report progress

3. **Memory Management**
   - Clean up resources
   - Release large objects
   - Use object pooling jika needed

4. **Database Access**
   - Batch operations
   - Use indexes
   - Optimize queries

---

## 🔗 Related Documentation

- [Getting Started Guide](GETTING_STARTED.md)
- [API Reference](API_REFERENCE.md)
- [Best Practices](../guides/BEST_PRACTICES.md)
- [Official ADK](http://www.amibroker.com/bin/ADK.zip)

---

*Last Updated: August 2026*
