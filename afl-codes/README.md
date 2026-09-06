# AmiBroker AFL Code Library

Koleksi lengkap **AmiBroker Formula Language (AFL)** trading strategies, indicators, dan tools untuk trader dari semua level. Repository ini dibuat untuk membantu trader mengotomatisasi strategi trading mereka menggunakan AmiBroker platform.

## 📚 Apa itu AFL?

**AmiBroker Formula Language (AFL)** adalah bahasa pemrograman yang dirancang khusus untuk AmiBroker - platform analisis teknis dan backtesting yang powerful. Dengan AFL, Anda bisa:

- Membuat custom trading strategies
- Develop custom indicators
- Automate trading signals
- Backtest strategi dengan data real
- Optimize trading parameters

## 🗂️ Struktur Repository

```
amibroker-afl-codes/
├── README.md                          # File ini
├── SETUP_GUIDE.md                     # Panduan setup AmiBroker
├── TRADING_GUIDE.md                   # Panduan dasar trading dengan AmiBroker
│
├── strategies/                        # Trading Strategies
│   ├── trend-following/              # Strategi mengikuti trend
│   │   ├── simple_moving_average.afl
│   │   ├── ema_crossover.afl
│   │   └── README.md
│   ├── mean-reversion/               # Strategi mean reversion
│   │   ├── bollinger_band_reversal.afl
│   │   ├── rsi_oversold.afl
│   │   └── README.md
│   ├── momentum/                     # Strategi momentum
│   │   ├── rsi_momentum.afl
│   │   ├── macd_momentum.afl
│   │   └── README.md
│   └── support-resistance/           # Strategi support/resistance
│       ├── level_breakout.afl
│       ├── pivot_point_trading.afl
│       └── README.md
│
├── indicators/                        # Custom Indicators
│   ├── moving_averages.afl
│   ├── oscillators.afl
│   └── volatility.afl
│
├── tools/                             # Utility Tools
│   ├── position_sizing.afl
│   ├── risk_management.afl
│   └── performance_analysis.afl
│
├── docs/                              # Dokumentasi
│   ├── AFL_BASICS.md                 # Dasar-dasar AFL
│   ├── COMMON_PATTERNS.md            # Pattern AFL yang sering digunakan
│   ├── BACKTESTING_GUIDE.md          # Panduan backtesting
│   └── OPTIMIZATION_TIPS.md          # Tips optimization parameter
│
└── examples/                          # Contoh-contoh
    ├── simple_strategy.afl
    ├── complete_system.afl
    └── indicator_integration.afl
```

## 🎯 Jenis Strategi

### 1. **Trend Following** 📈
Strategi yang mengikuti trend pasar dengan menggunakan moving averages dan breakouts.
- Cocok untuk: Medium-term & long-term trading
- Risk: Lower (mengikuti trend yang jelas)
- Example: EMA Crossover, Moving Average Systems

### 2. **Mean Reversion** 🔄
Strategi yang mengasumsikan harga akan kembali ke rata-rata setelah pergerakan ekstrem.
- Cocok untuk: Short-term & swing trading
- Risk: Medium-High (bet against trend)
- Example: Bollinger Bands, RSI Oversold/Overbought

### 3. **Momentum** 🚀
Strategi berbasis momentum indikator yang menangkap pergerakan harga yang kuat.
- Cocok untuk: Day trading & swing trading
- Risk: Medium (volatile)
- Example: MACD, RSI, Stochastic

### 4. **Support/Resistance** 🎯
Strategi berbasis level support dan resistance untuk entry dan exit points.
- Cocok untuk: All timeframes
- Risk: Medium (tergantung setup)
- Example: Breakout Trading, Pivot Points

## 🚀 Quick Start

### Langkah 1: Setup AmiBroker
Lihat [SETUP_GUIDE.md](SETUP_GUIDE.md) untuk instalasi dan konfigurasi AmiBroker.

### Langkah 2: Belajar AFL Basics
Baca [docs/AFL_BASICS.md](docs/AFL_BASICS.md) untuk memahami dasar-dasar AFL.

### Langkah 3: Pilih Strategi
Browse strategies di folder `strategies/` dan pilih yang sesuai dengan style trading Anda.

### Langkah 4: Backtest & Optimize
Ikuti [docs/BACKTESTING_GUIDE.md](docs/BACKTESTING_GUIDE.md) untuk backtest strategi.

### Langkah 5: Deploy & Monitor
Mulai gunakan strategi dengan uang real atau paper trading terlebih dahulu.

## 📖 Dokumentasi

- **[SETUP_GUIDE.md](SETUP_GUIDE.md)** - Panduan instalasi dan konfigurasi
- **[TRADING_GUIDE.md](TRADING_GUIDE.md)** - Panduan trading dasar
- **[docs/AFL_BASICS.md](docs/AFL_BASICS.md)** - Pengenalan AFL
- **[docs/COMMON_PATTERNS.md](docs/COMMON_PATTERNS.md)** - Pattern AFL yang sering digunakan
- **[docs/BACKTESTING_GUIDE.md](docs/BACKTESTING_GUIDE.md)** - Cara melakukan backtesting
- **[docs/OPTIMIZATION_TIPS.md](docs/OPTIMIZATION_TIPS.md)** - Tips optimize parameter

## 💡 Tips Menggunakan Repository

1. **Read Documentation First** - Pahami konsep sebelum menggunakan strategi
2. **Always Backtest** - Jangan langsung trade real money, backtest dulu
3. **Start Small** - Mulai dengan position size kecil saat paper trading
4. **Understand Your Strategy** - Ketahui cara kerja strategi yang Anda gunakan
5. **Risk Management** - Selalu set stop loss dan manage risk dengan baik
6. **Monitor Performance** - Pantau hasil trading dan optimize strategi

## ⚠️ Disclaimer

- Repository ini hanya untuk educational purposes
- Semua strategi adalah historical testing results, tidak menjamin profit di masa depan
- Past performance does not guarantee future results
- Gunakan paper trading/demo account sebelum real trading
- Konsultasi dengan financial advisor jika diperlukan

## 🤝 Kontribusi

Kami menerima kontribusi dalam bentuk:
- New strategies
- Improvements pada existing strategies
- Bug fixes
- Documentation improvements
- Examples dan tutorials

## 📝 License

Repository ini menggunakan **Apache License 2.0** - bebas digunakan untuk personal dan commercial use.

## 📞 Support & Feedback

- Buka **Issues** untuk bug reports atau feature requests
- Diskusi strategi di **Discussions**
- Ikuti **AmiBroker Documentation** untuk referensi resmi

---

**Happy Trading! 📊**

*Last Updated: August 2026*
