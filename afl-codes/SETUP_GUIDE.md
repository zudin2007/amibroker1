# AmiBroker Setup Guide

Panduan lengkap untuk menginstal, mengkonfigurasi, dan mulai menggunakan AmiBroker dengan AFL strategies dari repository ini.

## 📋 Daftar Isi

1. [System Requirements](#system-requirements)
2. [Instalasi AmiBroker](#instalasi-amibroker)
3. [Konfigurasi Awal](#konfigurasi-awal)
4. [Import Data Historis](#import-data-historis)
5. [Setup Data Broker](#setup-data-broker)
6. [Menggunakan AFL Strategies](#menggunakan-afl-strategies)
7. [Troubleshooting](#troubleshooting)

## 💻 System Requirements

### Minimum Requirements:
- **OS**: Windows 7, 10, 11, atau Server editions
- **RAM**: 2 GB minimum (4 GB recommended)
- **Storage**: 500 MB free space untuk AmiBroker
- **Internet**: Koneksi internet yang stabil

### Recommended Setup:
- **OS**: Windows 10/11 (latest build)
- **RAM**: 8 GB atau lebih
- **CPU**: Multi-core processor
- **SSD**: Untuk faster data loading

## 🔧 Instalasi AmiBroker

### Step 1: Download AmiBroker

1. Buka website resmi: https://www.amibroker.com/download.html
2. Download versi terbaru (gratis untuk trial 45 hari)
3. Untuk full version, beli lisensi di: https://www.amibroker.com/buy.html

### Step 2: Install AmiBroker

```
1. Double-click installer (.exe)
2. Pilih folder instalasi (default: C:\Program Files\AmiBroker)
3. Follow installation wizard
4. Restart komputer (recommended)
```

### Step 3: Launch AmiBroker

```
1. Buka AmiBroker dari Start Menu atau desktop shortcut
2. Akan muncul welcome dialog
3. AmiBroker siap digunakan
```

## ⚙️ Konfigurasi Awal

### 1. Set Default Database Path

```
Menu: File → Database Locations
- Pilih folder untuk menyimpan database
- Default: C:\Program Files\AmiBroker\Databases\Default
```

### 2. Konfigurasi Symbol Lists

```
Menu: Tools → Symbol Information
- Tambah symbols yang ingin Anda trade
- Bisa import dari file CSV
- Atau add manual one by one
```

### 3. Setup Quotes Provider

```
Menu: Tools → Database Integrity
- Pilih provider data (Yahoo Finance, Finam, dll)
- Configure API key jika diperlukan
- Test connection
```

### 4. Konfigurasi Chart Settings

```
Menu: View → Preferences
- Bar Settings: Pilih timeframe default
- Chart Appearance: Font, color, dll
- Quote Scaling: Adjust untuk visibility
```

## 📊 Import Data Historis

### Option 1: Auto-Import dari Online Provider

```
Menu: Tools → Symbol Information
1. Select symbol(s) yang ingin di-import
2. Klik "Import Quotes" button
3. Pilih provider (Yahoo Finance, Google, dll)
4. Pilih date range
5. Klik Import
```

### Option 2: Import dari File CSV

**Format CSV yang didukung:**
```
Date, Open, High, Low, Close, Volume
2024-08-01, 100.00, 102.50, 99.80, 101.50, 1000000
2024-08-02, 101.50, 103.00, 101.00, 102.50, 900000
```

**Import steps:**
```
Menu: File → Import → ASCII Format
1. Browse file CSV
2. Configure column mapping
3. Set date format
4. Klik Import
```

### Option 3: Menggunakan API Broker

```
Jika broker Anda support AmiBroker plugin:
1. Download plugin dari broker website
2. Install plugin
3. Configure credentials
4. AmiBroker akan auto-sync quotes
```

## 🏦 Setup Data Broker

Untuk live trading atau real-time data:

### Step 1: Pilih Broker

Broker yang support AmiBroker:
- Interactive Brokers
- Finam (Rusia)
- Lainnya - check www.amibroker.com/brokers.html

### Step 2: Install Broker Plugin

```
1. Download plugin dari broker website
2. Copy file .dll ke folder: C:\Program Files\AmiBroker\Brokers\
3. Restart AmiBroker
```

### Step 3: Configure Connection

```
Menu: Tools → Broker Settings
1. Select broker dari dropdown
2. Enter login credentials
3. Configure account settings
4. Test connection
5. Save settings
```

## 📝 Menggunakan AFL Strategies

### Step 1: Copy AFL Files

```
1. Clone atau download repository ini
2. Copy .afl files dari strategies folder
3. Paste ke folder: C:\Program Files\AmiBroker\Formulas\Custom
```

### Step 2: Reload Formulas

```
AmiBroker → Tools → Debug Window
Atau tekan: Ctrl+Alt+D

Di debug window, ketik:
RequestTimedRefresh(1);
```

### Step 3: Aplikasikan Formula ke Chart

```
1. Buka symbol yang ingin dianalisis
2. Klik kanan pada chart
3. Pilih: Add Analysis → AmiBroker
4. Browse formula dari custom folder
5. Klik Add
```

### Step 4: Backtest Strategy

```
Menu: Analysis → Portfolio Backtest
1. Select strategy yang ingin ditest
2. Configure backtest parameters:
   - Portfolio type
   - Symbols
   - Date range
   - Initial capital
   - Position sizing
3. Klik Backtest
4. Lihat hasil di Report tab
```

## 🔍 Troubleshooting

### Problem: "No data available"

**Solution:**
1. Import quotes dulu (lihat [Import Data Historis](#import-data-historis))
2. Check symbol format (harus sesuai dengan database)
3. Verify date range ada data
4. Menu: Tools → Database Integrity → Scan

### Problem: Formula tidak muncul di list

**Solution:**
1. Pastikan .afl file di folder: `C:\Program Files\AmiBroker\Formulas\Custom\`
2. Reload formulas: Ctrl+Alt+D, then `RequestTimedRefresh(1);`
3. Restart AmiBroker
4. Check file permissions (file harus readable)

### Problem: "Error: Unknown variable"

**Solution:**
1. Formula memerlukan data tertentu (OHLCV, dll)
2. Check dokumentasi strategi
3. Verify data tersedia di database
4. Update formula path di code

### Problem: Backtest returns tidak masuk akal

**Solution:**
1. Check initial capital setting
2. Verify commission/slippage settings
3. Review entry/exit conditions dalam code
4. Print debug values: _TRACE() function

### Problem: AmiBroker crash saat backtest

**Solution:**
1. Reduce symbol count atau date range
2. Close other applications (free up RAM)
3. Update ke versi terbaru AmiBroker
4. Check plugin compatibility

## 📚 Useful Resources

- **Official AmiBroker Manual**: https://www.amibroker.com/guide/
- **AFL Reference**: https://www.amibroker.com/guide/aflanguage.html
- **Community Forum**: https://www.amibroker.com/forums/
- **Video Tutorials**: https://www.amibroker.com/video/

## 💡 Best Practices

1. **Backup Database Regularly**
   ```
   Menu: Tools → Database Maintenance → Backup
   ```

2. **Use Version Control untuk AFL files**
   ```
   Simpan .afl files di version control (git)
   Untuk tracking changes dan collaboration
   ```

3. **Document Your Strategies**
   ```
   Buat README untuk setiap strategy
   Jelaskan rules, parameters, dan usage
   ```

4. **Test di Demo Account Dulu**
   ```
   Backtest → Paper Trading → Live Trading
   Jangan langsung live tanpa testing
   ```

5. **Monitor Performance Metrics**
   ```
   - Sharpe Ratio
   - Win Rate
   - Drawdown
   - Risk/Reward Ratio
   ```

## 🎓 Next Steps

Setelah setup selesai:
1. Baca [TRADING_GUIDE.md](TRADING_GUIDE.md) untuk panduan trading dasar
2. Pelajari [docs/AFL_BASICS.md](docs/AFL_BASICS.md) untuk AFL fundamentals
3. Explore strategies di folder `strategies/`
4. Mulai backtest dengan demo strategies

---

**Siap untuk mulai trading? Happy backtesting! 📈**
