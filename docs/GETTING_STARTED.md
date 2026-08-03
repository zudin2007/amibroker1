# Getting Started with AmiBroker .NET SDK

Complete guide untuk membuat plugin AmiBroker pertama Anda menggunakan C# dan .NET.

## 📋 Daftar Isi

1. [Prerequisites](#prerequisites)
2. [Installation](#installation)
3. [Project Setup](#project-setup)
4. [Your First Plugin](#your-first-plugin)
5. [Testing & Debugging](#testing--debugging)
6. [Deployment](#deployment)

---

## 🔧 Prerequisites

### Required Software

1. **Visual Studio**
   - Version 2012 or later
   - Community Edition (free) is fine
   - [Download](https://visualstudio.microsoft.com/downloads/)

2. **.NET Framework**
   - Version 4.5 or later
   - Recommended: 4.7.2+
   - Usually comes with Visual Studio

3. **AmiBroker**
   - Version 6.0 or later
   - [Download](https://www.amibroker.com/download.html)
   - Can use trial (45 days free)

4. **Git** (optional, untuk clone repository)
   - [Download](https://git-scm.com/download/win)

### System Requirements

- **OS:** Windows 7 or later (Windows 10/11 recommended)
- **RAM:** 4 GB minimum (8 GB recommended)
- **Disk:** 2 GB free space untuk development tools

---

## 📦 Installation

### Step 1: Install Visual Studio

```
1. Download Visual Studio Community/Professional
2. Run installer
3. Select "Desktop development with C++"
   (untuk kompilasi optimized plugins)
4. Also select ".NET desktop development"
5. Complete installation
6. Restart computer
```

### Step 2: Install .NET Framework

Usually already included dengan Visual Studio, tapi verify:

```
1. Open Control Panel → Programs → Programs and Features
2. Click "Turn Windows features on or off"
3. Check: ".NET Framework 4.7.2" or higher
4. Click OK
5. Restart if prompted
```

### Step 3: Install AmiBroker

```
1. Download AmiBroker dari https://www.amibroker.com/download.html
2. Run installer
3. Follow installation wizard
4. Choose default locations (recommended)
5. Restart computer
6. Verify installation by running AmiBroker
```

### Step 4: Clone Repository

```bash
# Using Git
git clone https://github.com/zudin2007/amibroker.git
cd amibroker

# Or download ZIP from GitHub
```

---

## 🎯 Project Setup

### Step 1: Open Solution in Visual Studio

```
1. Navigate ke folder amibroker/
2. Double-click "AmiBroker .NET SDK.sln"
3. Visual Studio akan open solution
4. Wait untuk project loading
```

### Step 2: Restore NuGet Packages

```
1. Tools → NuGet Package Manager → Package Manager Console
2. Run: Update-Package -Reinstall
3. Tunggu packages di-restore
```

### Step 3: Explore Project Structure

```
Plugin/
├── Plugin.cs              ← Main plugin class (START HERE)
├── Models/                ← Data structures
├── Plugin.csproj          ← Project configuration
└── Properties/
    └── AssemblyInfo.cs    ← Plugin metadata

Key files untuk di-modify:
- Plugin.cs - Implement plugin logic here
- Plugin.csproj - Configure .NET version
- AssemblyInfo.cs - Set version info
```

### Step 4: Set .NET Framework Version

Edit `Plugin/Plugin.csproj`:

```xml
<!-- Current setting -->
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>

<!-- Change to latest available (recommended) -->
<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>
```

---

## 🚀 Your First Plugin

### Task: Create Simple CSV Importer Plugin

Mari kita buat simple plugin yang import data dari CSV file.

### Step 1: Update Plugin Info

Edit `Plugin/Plugin.cs`, method `GetPluginInfo()`:

```csharp
public override void GetPluginInfo(PluginInfo info)
{
    info.Name = "CSV Data Importer";
    info.Author = "Your Name";
    info.Version = 100;  // Version 1.00
    info.Copyright = "Copyright 2024";
    info.Description = "Simple CSV file importer for AmiBroker";

    // Set plugin capabilities
    info.Type = PluginType.QuotesFeed;
    info.Flags = PluginFlags.EnableDataPlugin;
}
```

### Step 2: Implement Data Loading

Add method untuk load CSV file:

```csharp
private bool LoadDataFromCSV(string filePath, string ticker, 
    PluginStatus status, Quotation quote)
{
    try
    {
        if (!File.Exists(filePath))
        {
            Debug.WriteLine($"File not found: {filePath}");
            return false;
        }

        var lines = File.ReadAllLines(filePath);
        if (lines.Length < 2)
            return false; // Need header + at least 1 data row

        // Skip header line (line 0)
        for (int i = 1; i < lines.Length; i++)
        {
            var fields = lines[i].Split(',');
            
            if (fields.Length < 6)
                continue; // Invalid line

            try
            {
                // Parse CSV: Date,Open,High,Low,Close,Volume
                quote.Date = AmiDate.FromString(fields[0]);
                quote.Open = double.Parse(fields[1]);
                quote.High = double.Parse(fields[2]);
                quote.Low = double.Parse(fields[3]);
                quote.Close = double.Parse(fields[4]);
                quote.Volume = long.Parse(fields[5]);

                // Add quote to database
                status.AddQuote(quote);
            }
            catch (Exception ex)
            {
                Debug.WriteLine($"Error parsing line {i}: {ex.Message}");
                continue;
            }
        }

        return true;
    }
    catch (Exception ex)
    {
        Debug.WriteLine($"LoadDataFromCSV error: {ex.Message}");
        return false;
    }
}
```

### Step 3: Implement GetQuotesEx Method

Replace default `GetQuotesEx()`:

```csharp
public override AmiVar GetQuotesEx(
    string ticker,
    PluginStatus status,
    Quotation quote)
{
    try
    {
        // Build file path
        string csvFolder = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments),
            "AmiBrokerData");
        
        string csvFile = Path.Combine(csvFolder, $"{ticker}.csv");

        Debug.WriteLine($"Loading data for {ticker} from {csvFile}");

        // Load CSV data
        if (LoadDataFromCSV(csvFile, ticker, status, quote))
        {
            return AmiVar.Success();
        }
        else
        {
            return AmiVar.Error();
        }
    }
    catch (Exception ex)
    {
        Debug.WriteLine($"GetQuotesEx error: {ex.Message}");
        return AmiVar.Error();
    }
}
```

### Step 4: Add Error Handling

Implement error notification:

```csharp
public override void GetErrorMessage(ref StringBuilder errorMessage)
{
    if (!string.IsNullOrEmpty(_lastError))
    {
        errorMessage.Clear();
        errorMessage.Append(_lastError);
    }
}

private string _lastError = "";
```

---

## 🧪 Testing & Debugging

### Step 1: Build Project

```
1. Build → Build Solution (Ctrl+Shift+B)
2. Check Output window untuk compile errors
3. Verify DLL created di: Plugin/bin/Debug/Plugin.dll
```

### Step 2: Prepare Test Data

Create CSV file dengan test data:

```csv
Date,Open,High,Low,Close,Volume
2024-01-01,100.00,102.50,99.50,101.50,1000000
2024-01-02,101.50,103.00,101.00,102.50,900000
2024-01-03,102.50,104.00,101.50,103.50,1100000
2024-01-04,103.50,105.00,102.50,104.50,950000
2024-01-05,104.50,106.00,103.50,105.50,1050000
```

Save as: `Documents/AmiBrokerData/TEST.csv`

### Step 3: Enable Debugging

Di Visual Studio, setup debugging:

```
1. Debug → Exceptions
2. Check "Common Language Runtime Exceptions"
3. Click Close
```

### Step 4: Deploy Plugin untuk Testing

```
1. Find AmiBroker Plugins folder:
   C:\Program Files\AmiBroker\Plugins\

2. Copy DLL:
   Plugin/bin/Debug/Plugin.dll → Plugins/ folder

3. Restart AmiBroker

4. Check Tools → Database Integrity para verify plugin load
```

### Step 5: Test dengan AmiBroker

```
1. Open AmiBroker
2. Right-click symbol list → Add Symbol
3. Add "TEST" ticker
4. Wait untuk data load dari plugin
5. Chart should show test data
```

### Step 6: Debug dalam Visual Studio

```
1. Debug → Attach to Process
2. Find AmiBroker.exe
3. Click Attach
4. Set breakpoints di Plugin.cs
5. Try data load, akan break di breakpoints
6. Use Debug toolbar para step through code
```

---

## 🚀 Deployment

### Step 1: Create Release Build

```
1. Build → Configuration Manager
2. Select "Release" configuration
3. Build → Build Solution
4. DLL created di: Plugin/bin/Release/Plugin.dll
```

### Step 2: Install Plugin

```
1. Copy Plugin.dll ke:
   C:\Program Files\AmiBroker\Plugins\

2. (Optional) Create subfolder:
   C:\Program Files\AmiBroker\Plugins\MyPlugins\

3. Restart AmiBroker

4. Verify di Tools → Database Integrity
```

### Step 3: Test Full Workflow

```
1. Open AmiBroker
2. Add new symbol
3. Request quotes
4. Verify data loaded correctly
5. Check charts display correct data
```

### Step 4: Create Installer (Optional)

Untuk distribute plugin ke users, create installer:

```
1. Tools → Extensions → Add Windows Installer Project
2. Follow wizard
3. Add output dari Release build
4. Create .msi installer
5. Distribute to users
```

---

## 🔍 Troubleshooting

### Problem: Build Errors

**Error:** `.NET Framework 4.5 not found`

**Solution:**
1. Install .NET Framework 4.5+ dari Windows Update
2. Update TargetFrameworkVersion di .csproj

### Problem: Plugin Not Loading

**Error:** "Plugin.dll not found" atau tidak ada di list

**Solution:**
1. Verify DLL di correct folder (C:\Program Files\AmiBroker\Plugins\)
2. Check DLL architecture (x86 vs x64)
3. Restart AmiBroker completely
4. Check event viewer untuk error messages

### Problem: Runtime Crashes

**Error:** AmiBroker crash saat load plugin

**Solution:**
1. Check for null reference exceptions
2. Add try-catch blocks di methods
3. Debug dengan Attach to Process
4. Check event viewer logs

### Problem: Data Not Showing

**Error:** Plugin return success tapi data tidak appear

**Solution:**
1. Verify CSV file format correct
2. Debug GetQuotesEx() method
3. Check PluginStatus.AddQuote() successful
4. Monitor debug output messages

---

## 📚 Next Steps

1. ✅ Complete this guide
2. → Explore [examples/](../examples/) folder
3. → Read [ARCHITECTURE.md](ARCHITECTURE.md) untuk deep understanding
4. → Refer [API_REFERENCE.md](API_REFERENCE.md) untuk methods
5. → Check [BEST_PRACTICES.md](../guides/BEST_PRACTICES.md)

---

## 🎓 Learning Resources

### AmiBroker Official
- [ADK Manual](http://www.amibroker.com/bin/ADK.zip)
- [AmiBroker Guide](https://www.amibroker.com/guide/)
- [Plugin API](https://www.amibroker.com/guide/adk/)

### C# & .NET
- [C# Documentation](https://docs.microsoft.com/dotnet/csharp/)
- [.NET Framework Docs](https://docs.microsoft.com/dotnet/framework/)
- [Visual Studio Docs](https://docs.microsoft.com/visualstudio/)

### Community
- [AmiBroker Forum](https://groups.google.com/forum/#!forum/amidev)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/amibroker)

---

**Congratulations! 🎉 Anda sudah membuat plugin AmiBroker pertama!**

Sekarang explore tutorial lainnya dan create something amazing!

---

*Last Updated: August 2026*
