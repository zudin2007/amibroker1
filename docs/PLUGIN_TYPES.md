# AmiBroker Plugin Types

Panduan untuk berbagai tipe plugin yang bisa dibuat menggunakan .NET SDK.

## 📊 Available Plugin Types

### 1. Data Feed Plugins (Quote Plugins)

**Purpose:** Provide price and volume data

```
Data Source → Plugin → AmiBroker Database
```

**Entry Point:** `GetQuotesEx()`

**What You Provide:**
- Opening price
- High price
- Low price
- Closing price
- Volume
- OpenInterest (optional)

**Data Sources:**
- CSV/Excel files
- REST APIs
- Databases
- Real-time tickers
- Custom data formats

**Example Use Cases:**
```
✓ CSV Data Importer
  - Read from CSV file
  - Parse into OHLCV
  - Store in AmiBroker

✓ REST API Data Puller
  - Call API endpoint
  - Parse JSON response
  - Convert to quotes
  - Update database

✓ Real-time Feed
  - Connect to broker API
  - Receive live quotes
  - Update in real-time

✓ Custom Format Reader
  - Parse proprietary format
  - Convert to standard format
  - Import into AmiBroker
```

**Implementation Template:**

```csharp
public override AmiVar GetQuotesEx(
    string ticker,
    PluginStatus status,
    Quotation quote)
{
    try
    {
        // 1. Connect to data source
        var source = ConnectToDataSource();
        
        // 2. Fetch data for symbol
        var data = source.GetData(ticker);
        
        // 3. Parse and populate quotes
        foreach (var record in data)
        {
            quote.Date = AmiDate.FromString(record.Date);
            quote.Open = record.Open;
            quote.High = record.High;
            quote.Low = record.Low;
            quote.Close = record.Close;
            quote.Volume = record.Volume;
            
            // 4. Add to database
            status.AddQuote(quote);
        }
        
        return AmiVar.Success();
    }
    catch (Exception ex)
    {
        return AmiVar.Error();
    }
}
```

**Advantages:**
- ✅ Most common plugin type
- ✅ Easiest to implement
- ✅ Direct data integration
- ✅ Real-time capability

**Challenges:**
- ❌ Data format conversion
- ❌ API integration complexity
- ❌ Error handling
- ❌ Performance optimization

---

### 2. Information Plugins

**Purpose:** Provide security/company information

```
External Data → Plugin → AmiBroker Info Database
```

**Entry Point:** `SetData()`

**What You Provide:**
- Company name
- Full name
- Exchange
- Currency
- Security type
- Custom data fields

**Data Sources:**
- Company databases
- Exchange listings
- Fundamental data APIs
- Custom datasources

**Example Use Cases:**
```
✓ Company Information
  - Fetch company details
  - Store exchange/sector
  - Update financial metrics

✓ Dividend/Split Data
  - Get corporate actions
  - Store split ratios
  - Track dividends

✓ Exchange Data
  - List available symbols
  - Get exchange info
  - Trading hours info

✓ Fundamental Data
  - P/E ratios
  - Market cap
  - Industry classification
```

**Implementation Template:**

```csharp
public override AmiVar SetData(
    string ticker,
    StockInfo info)
{
    try
    {
        // 1. Fetch security information
        var companyData = FetchCompanyInfo(ticker);
        
        // 2. Populate StockInfo
        info.Name = companyData.Symbol;
        info.FullName = companyData.Name;
        info.Exchange = companyData.Exchange;
        info.Currency = companyData.Currency;
        
        return AmiVar.Success();
    }
    catch (Exception ex)
    {
        return AmiVar.Error();
    }
}
```

---

### 3. Analysis Plugins

**Purpose:** Perform custom analysis on data

```
AmiBroker Data → Plugin Analysis → Results
```

**Entry Point:** `Analyze()`

**What You Analyze:**
- Price patterns
- Volume analysis
- Risk calculations
- Portfolio metrics
- Custom indicators

**Example Use Cases:**
```
✓ Risk Analysis
  - Calculate VaR
  - Compute volatility
  - Estimate drawdown

✓ Portfolio Optimizer
  - Optimize weights
  - Maximize Sharpe ratio
  - Minimize risk

✓ Pattern Recognition
  - Identify chart patterns
  - Detect support/resistance
  - Find correlation

✓ Performance Analysis
  - Calculate returns
  - Track metrics
  - Generate reports
```

**Implementation Template:**

```csharp
public override AmiVar Analyze(
    string ticker,
    AnalysisData data)
{
    try
    {
        // 1. Get analysis parameters
        var params = GetAnalysisParams();
        
        // 2. Perform analysis
        var results = PerformAnalysis(data, params);
        
        // 3. Store/return results
        return new AmiVar(results);
    }
    catch (Exception ex)
    {
        return AmiVar.Error();
    }
}
```

---

### 4. Notification/Signal Plugins

**Purpose:** Alert trader tentang market events

```
AmiBroker Events → Plugin Logic → Notifications
```

**Entry Points:**
- `OnOrderFilled()`
- `OnPriceAlert()`
- `OnCustomEvent()`

**What You Can Do:**
- Send email alerts
- Push notifications
- SMS messages
- Webhook calls
- Sound alerts

**Example Use Cases:**
```
✓ Price Alerts
  - Notify on price milestone
  - Support/resistance alerts
  - Breakout notifications

✓ Trade Notifications
  - Order status updates
  - Trade execution alerts
  - Position changes

✓ Market Alerts
  - Economic news alerts
  - Earnings announcements
  - Volatility spike alerts

✓ Custom Signals
  - Strategy signals
  - Risk warnings
  - Portfolio alerts
```

---

## 🎯 Choosing Your Plugin Type

### Decision Matrix

```
Need                          → Best Plugin Type
──────────────────────────────────────────────────
Import data from source       → Data Feed Plugin
Get company information       → Information Plugin
Analyze market data           → Analysis Plugin
Alert on market events        → Notification Plugin
Combine multiple sources      → Hybrid Plugin
```

### Complexity Levels

```
Simple   ▰▰▰░░░  Information Plugin
         ▰▰▰▰░░  Data Feed Plugin (basic)
Medium   ▰▰▰▰▰░  Data Feed Plugin (advanced)
         ▰▰▰▰▰░  Analysis Plugin (basic)
Complex  ▰▰▰▰▰▰  Analysis Plugin (advanced)
         ▰▰▰▰▰▰  Notification Plugin
```

---

## 🔄 Hybrid Plugins

### Combining Multiple Types

```csharp
public class HybridPlugin : Plugin
{
    // Data feed functionality
    public override AmiVar GetQuotesEx(...) { }
    
    // Information functionality
    public override AmiVar SetData(...) { }
    
    // Analysis functionality
    public override AmiVar Analyze(...) { }
}
```

**Benefits:**
- ✅ Unified data source
- ✅ Consistent interfaces
- ✅ Reduced deployment complexity
- ✅ Easier maintenance

---

## 📋 Plugin Checklist

### Before Implementing

- [ ] Decide plugin type
- [ ] Identify data source
- [ ] Plan error handling
- [ ] Design data structures
- [ ] Outline main logic

### During Implementation

- [ ] Implement core methods
- [ ] Add error handling
- [ ] Test with sample data
- [ ] Add logging/debugging
- [ ] Optimize performance

### Before Release

- [ ] Comprehensive testing
- [ ] Error message validation
- [ ] Performance verification
- [ ] Documentation complete
- [ ] Version/metadata set

---

## 🚀 Next Steps

Choose your plugin type and follow:
1. [Getting Started Guide](GETTING_STARTED.md)
2. [Architecture Overview](ARCHITECTURE.md)
3. [API Reference](API_REFERENCE.md)
4. [Examples](../examples/)

---

*Last Updated: August 2026*
