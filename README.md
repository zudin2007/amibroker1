## AmiBroker .NET SDK and Community Plug-ins

Non-official [AmiBroker](http://www.amibroker.com) plug-in SDK for .NET developers. It's a port of the official C++ based [AmiBroker Development Kit](http://www.amibroker.com/download.html) (ADK) to .NET / C#.

**License:** 100% free, no hidden charges. Allowed for both personal and commercial use under [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).

---

## 📚 Quick Navigation

- **[Getting Started Guide](docs/GETTING_STARTED.md)** - Setup and first plugin
- **[Architecture Overview](docs/ARCHITECTURE.md)** - SDK structure and components
- **[API Reference](docs/API_REFERENCE.md)** - Complete API documentation
- **[Examples](examples/)** - Working code examples
- **[Troubleshooting](docs/TROUBLESHOOTING.md)** - Common issues and solutions

---

## ✨ Features

✅ **Full C# Implementation** - Write plugins in C# instead of C++  
✅ **Type-Safe** - Leverage C# type system and compiler checking  
✅ **Managed Code** - No unmanaged memory or pointer manipulation  
✅ **Community Supported** - Active community of developers  
✅ **Free & Open Source** - Apache License 2.0  
✅ **Works with AmiBroker** - Compatible with AmiBroker 6.0+  

---

## 🎯 What You Can Build

### Data Plugins
Fetch real-time or historical price data from custom sources:
```
Your Data Source → Plugin → AmiBroker
Examples:
- Custom CSV/Database importer
- REST API data connector
- Real-time market data feed
- Custom exchange connector
```

### Analysis Plugins
Perform custom analysis and calculations:
```
AmiBroker Data → Plugin Logic → Results back to AmiBroker
Examples:
- Custom indicators
- Portfolio analysis tools
- Risk calculation engine
- Pattern recognition system
```

### Integration Plugins
Connect AmiBroker with external systems:
```
AmiBroker ↔ Plugin ↔ External Systems
Examples:
- Order management system
- Trade notification system
- Account synchronization
- Custom reporting engine
```

---

## 💻 System Requirements

### Minimum
- **OS:** Windows 7 or later
- **Framework:** .NET Framework 4.5+
- **AmiBroker:** 6.0 or later
- **IDE:** Visual Studio 2012 or later (Community Edition OK)

### Recommended
- **OS:** Windows 10/11
- **Framework:** .NET Framework 4.7.2 or later (for better performance)
- **AmiBroker:** Latest version
- **IDE:** Visual Studio 2019 or later

---

## 🚀 Quick Start

### 1. Prerequisites

```
✓ Visual Studio (2012 or later)
✓ .NET Framework 4.5+
✓ AmiBroker (6.0+)
✓ Git (optional, for cloning)
```

### 2. Clone Repository

```bash
git clone https://github.com/zudin2007/amibroker.git
cd amibroker
```

### 3. Open in Visual Studio

```
1. Double-click "AmiBroker .NET SDK.sln"
2. Visual Studio will open the solution
3. Restore NuGet packages if prompted
```

### 4. Configure Your Plugin

Edit `Plugin/Plugin.cs`:

```csharp
// Update plugin information
public override void GetPluginInfo(PluginInfo info)
{
    info.Name = "My Custom Plugin";
    info.Author = "Your Name";
    info.Version = 100;  // Version 1.00
    info.Copyright = "Copyright 2024";
}

// Add your data fetching logic
public override AmiVar GetQuotesEx(...)
{
    // Implement your logic here
}
```

### 5. Build & Deploy

```
1. Build → Build Solution (Ctrl+Shift+B)
2. Copy DLL from bin folder
3. Place in AmiBroker Plugins folder
4. Restart AmiBroker
```

---

## 📂 Project Structure

```
amibroker/
├── README.md (this file)
├── AmiBroker .NET SDK.sln (solution file)
│
├── Plugin/                 # Main plugin project
│   ├── Plugin.cs          # Main plugin class
│   ├── Plugin.csproj      # Project file
│   ├── Models/            # Data models
│   │   ├── PluginInfo.cs
│   │   ├── Quotation.cs
│   │   ├── StockInfo.cs
│   │   └── ...
│   └── Properties/
│
├── docs/                  # Documentation
│   ├── GETTING_STARTED.md
│   ├── ARCHITECTURE.md
│   ├── API_REFERENCE.md
│   ├── TROUBLESHOOTING.md
│   └── PLUGIN_TYPES.md
│
├── examples/              # Working examples
│   ├── SimpleDataPlugin/
│   ├── CSVImporter/
│   ├── APIPuller/
│   └── ...
│
├── guides/                # Development guides
│   ├── BUILDING_PLUGIN.md
│   ├── PLUGIN_LIFECYCLE.md
│   ├── DEBUGGING.md
│   └── BEST_PRACTICES.md
│
└── LICENSE.txt
```

---

## 🔗 Available Resources

### Official AmiBroker
- **Official ADK:** http://www.amibroker.com/bin/ADK.zip
- **AmiBroker Manual:** https://www.amibroker.com/guide/
- **ADK Documentation:** https://www.amibroker.com/guide/adk/

### Community
- **Discussion Forum:** https://groups.google.com/forum/#!forum/amidev
- **AmiBroker Forums:** https://www.amibroker.com/forums/

### .NET Resources
- **Microsoft .NET Docs:** https://docs.microsoft.com/dotnet/
- **C# Reference:** https://docs.microsoft.com/dotnet/csharp/

---

## 📖 Documentation Structure

### For Beginners
1. Start with [GETTING_STARTED.md](docs/GETTING_STARTED.md)
2. Read [ARCHITECTURE.md](docs/ARCHITECTURE.md) untuk understand SDK
3. Explore [examples/](examples/) folder untuk working code
4. Follow [BUILDING_PLUGIN.md](guides/BUILDING_PLUGIN.md)

### For Intermediate Developers
1. Read [PLUGIN_TYPES.md](docs/PLUGIN_TYPES.md) untuk plugin categories
2. Study [examples/](examples/) relevant untuk use case Anda
3. Refer [API_REFERENCE.md](docs/API_REFERENCE.md) untuk detailed API info
4. Check [BEST_PRACTICES.md](guides/BEST_PRACTICES.md)

### For Advanced Developers
1. Deep dive [ARCHITECTURE.md](docs/ARCHITECTURE.md)
2. Study source code di Plugin folder
3. Review [PLUGIN_LIFECYCLE.md](guides/PLUGIN_LIFECYCLE.md)
4. Refer oficial [ADK.zip documentation](http://www.amibroker.com/bin/ADK.zip)

---

## 🛠️ Development Workflow

### 1. Design Phase
- Define plugin requirements
- Choose plugin type (Data, Analysis, etc)
- Design data models and interfaces

### 2. Development Phase
- Create new plugin class (inherit from Plugin)
- Implement required methods
- Add your business logic
- Test with sample data

### 3. Testing Phase
- Local debugging dalam Visual Studio
- Test dengan AmiBroker
- Validate dengan real data
- Check error handling

### 4. Deployment Phase
- Build release version
- Create installer (optional)
- Distribute to users
- Maintain and update

---

## 📝 Example: Simple CSV Data Plugin

```csharp
public override AmiVar GetQuotesEx(
    string ticker,
    PluginStatus status,
    Quotation quote)
{
    try
    {
        // Load data from CSV file
        var csvPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments),
            "MarketData",
            $"{ticker}.csv");

        if (!File.Exists(csvPath))
            return AmiVar.Error();

        // Parse CSV and populate quote
        var lines = File.ReadAllLines(csvPath);
        foreach (var line in lines)
        {
            var fields = line.Split(',');
            // Parse fields and populate quote structure
            quote.Date = AmiDate.FromString(fields[0]);
            quote.Open = double.Parse(fields[1]);
            quote.High = double.Parse(fields[2]);
            quote.Low = double.Parse(fields[3]);
            quote.Close = double.Parse(fields[4]);
            quote.Volume = long.Parse(fields[5]);

            status.AddQuote(quote);
        }

        return AmiVar.Success();
    }
    catch (Exception ex)
    {
        System.Diagnostics.Debug.WriteLine($"Error: {ex.Message}");
        return AmiVar.Error();
    }
}
```

---

## 🤝 Contributing

Contributions are welcome! We accept:
- Bug fixes
- New plugin examples
- Documentation improvements
- Feature enhancements
- Community plugins

### How to Contribute
1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

---

## ⚠️ Troubleshooting

**Common Issues:**

| Issue | Solution |
|-------|----------|
| Plugin not loading | Check DLL in AmiBroker Plugins folder, restart AmiBroker |
| Build errors | Ensure .NET Framework 4.5+ installed, restore NuGet packages |
| Runtime crashes | Check event viewer logs, debug in Visual Studio |
| Data not showing | Verify GetQuotesEx() implementation, check data format |

See [TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) untuk more solutions.

---

## 📊 Known Plugins

### Data Plugins
- **Yahoo Finance Plugin** (planned) - Real-time stock data
- **Finam Plugin** (beta) - Russian market data

### Community Plugins
Check [sourceforge.net/projects/amibroker/files/](https://sourceforge.net/projects/amibroker/files/) untuk downloads.

---

## 📞 Support & Feedback

- **Issues & Bug Reports:** GitHub Issues
- **Questions & Discussions:** [Google Groups](https://groups.google.com/forum/#!forum/amidev)
- **AmiBroker Official:** https://www.amibroker.com/

---

## 📜 License

AmiBroker .NET SDK adalah licensed under [Apache License 2.0](LICENSE.txt).

```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
```

---

## 📚 Additional Resources

- **[Getting Started](docs/GETTING_STARTED.md)** - Complete setup guide
- **[Plugin Development Guide](guides/BUILDING_PLUGIN.md)** - Step-by-step tutorial
- **[API Documentation](docs/API_REFERENCE.md)** - Complete API reference
- **[Examples](examples/)** - Working code examples
- **[Best Practices](guides/BEST_PRACTICES.md)** - Development best practices

---

**Ready to build your first AmiBroker plugin? Start with [GETTING_STARTED.md](docs/GETTING_STARTED.md)!**

---

*Last Updated: August 2026*  
*AmiBroker .NET SDK Version: 2.0*
