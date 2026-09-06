# AmiBroker Trading Guide

Panduan dasar untuk menggunakan AmiBroker dalam aktivitas trading dan analisis pasar.

## 📋 Daftar Isi

1. [Dasar-Dasar AmiBroker](#dasar-dasar-amibroker)
2. [Interface Breakdown](#interface-breakdown)
3. [Timeframes & Symbols](#timeframes--symbols)
4. [Technical Analysis Basics](#technical-analysis-basics)
5. [Strategy Selection](#strategy-selection)
6. [Backtesting Strategies](#backtesting-strategies)
7. [Risk Management](#risk-management)
8. [Common Mistakes](#common-mistakes)

## 🎯 Dasar-Dasar AmiBroker

### Apa itu AmiBroker?

AmiBroker adalah platform untuk:
- **Technical Analysis**: Analisis chart dengan berbagai indicators
- **Backtesting**: Test strategi dengan data historis
- **Paper Trading**: Practice trading tanpa uang real
- **Automated Trading**: Eksekusi trading otomatis
- **Portfolio Management**: Manage multiple securities

### Core Concepts

**1. Symbol (Ticker)**
```
Representasi sekuritas yang diperdagangkan
Contoh: AAPL (Apple), GOOGL (Google), MSFT (Microsoft)
Di Indonesia: BBCA (BCA), TLKM (Telkom), BMRI (BRI)
```

**2. Bar/Candle**
```
Satu periode waktu (1 menit, 5 menit, 1 jam, 1 hari, dll)
Menunjukkan: Open, High, Low, Close, Volume
```

**3. Indicator**
```
Formula mathematis untuk analisis (Moving Average, RSI, MACD, dll)
Membantu identify trends dan entry/exit points
```

**4. Strategy**
```
Set rules untuk entry dan exit
Combine multiple indicators untuk generate signals
```

## 🖥️ Interface Breakdown

### Main Window Components

```
┌─────────────────────────────────────────┐
│  Menu Bar (File, Edit, View, etc)       │
├─────────────────────────────────────────┤
│  Toolbar (Quick access buttons)         │
├──────────────┬──────────────────────────┤
│              │                          │
│   Symbol     │     Chart Area           │
│   List       │  (Main candlestick       │
│   (Left)     │   chart with indicators) │
│              │                          │
│              │                          │
│              ├──────────────────────────┤
│              │ Info Panel (OHLCV, etc)  │
└──────────────┴──────────────────────────┘
```

### Key Areas

**Symbol List (Left)**
- Browse semua symbols di database
- Right-click untuk options
- Double-click untuk open chart

**Chart Area (Center)**
```
Main workspace untuk technical analysis
- Candlestick/Bar display
- Multiple indicators stacked
- Price action visualization
- Support/Resistance levels
```

**Info Panel (Bottom)**
```
Real-time atau historical data:
- Open, High, Low, Close
- Volume, Change %
- MA, RSI, MACD values
- Last update time
```

## ⏰ Timeframes & Symbols

### Timeframes Tersedia

```
Intraday:
- 1 minute    (1M) - For scalping
- 5 minutes   (5M) - Very short-term
- 15 minutes  (15M)- Short-term
- 1 hour      (1H) - Short to medium
- 4 hours     (4H) - Medium-term

Daily:
- 1 day       (D)  - Swing trading
- 1 week      (W)  - Long-term
- 1 month     (M)  - Very long-term
```

### Timeframe Selection Rules

```
Scalping/Day Trading  → Use: 1M, 5M, 15M
Swing Trading         → Use: 1H, 4H, 1D
Position Trading      → Use: 1D, 1W, 1M
Long-term Investing   → Use: 1W, 1M
```

### Symbol Selection

**Untuk US Stocks:**
```
Gunakan ticker resmi: AAPL, MSFT, GOOGL
Data dari: Yahoo Finance, IB, lainnya
```

**Untuk Indonesian Stocks:**
```
Format: BBCA, TLKM, BMRI, BBNI, etc
Data dari: Finam, IDX, broker lokal
```

**Custom Symbol:**
```
Bisa import dari CSV dengan format:
Date,Open,High,Low,Close,Volume
```

## 📊 Technical Analysis Basics

### Candlestick Patterns

**Uptrend Candles:**
```
- White/Green candle: Close > Open (Bullish)
- Increasing volume: Strength confirmation
- Higher highs & higher lows: Trend confirmation
```

**Downtrend Candles:**
```
- Black/Red candle: Close < Open (Bearish)
- Decreasing volume: Weakness confirmation
- Lower highs & lower lows: Trend confirmation
```

### Key Indicators Explained

**1. Moving Average (MA)**
```
Smooths price action to identify trend
- Fast MA (10, 20): Short-term trend
- Slow MA (50, 200): Long-term trend
- Crossover: Entry/exit signal
```

**2. RSI (Relative Strength Index)**
```
Oscillator showing overbought/oversold
- RSI > 70: Overbought (potential sell)
- RSI < 30: Oversold (potential buy)
- Range: 0-100
```

**3. MACD (Moving Average Convergence Divergence)**
```
Momentum indicator combining MAs
- MACD > Signal Line: Bullish
- MACD < Signal Line: Bearish
- Histogram: Strength of momentum
```

**4. Bollinger Bands**
```
Support/Resistance based on volatility
- Price touch upper band: Overbought
- Price touch lower band: Oversold
- Band width: Volatility measure
```

## 🎯 Strategy Selection

### Choose Based on Your Style

**Trend Followers:**
```
Use strategies: EMA Crossover, Moving Average Systems
Timeframe: 1H, 4H, 1D
Risk: Lower (follow strong trends)
```

**Momentum Traders:**
```
Use strategies: MACD, RSI Momentum
Timeframe: 5M, 15M, 1H
Risk: Medium-High (volatile)
```

**Mean Reversion Traders:**
```
Use strategies: Bollinger Bands, RSI Oversold
Timeframe: 15M, 1H, 4H
Risk: Medium-High (bet against trend)
```

**Breakout Traders:**
```
Use strategies: Support/Resistance, Pivot Points
Timeframe: 15M, 1H, 4H, 1D
Risk: Medium (wait for clear breakout)
```

## 🔬 Backtesting Strategies

### Step-by-Step Backtest Process

**1. Prepare Strategy File**
```
Copy .afl file ke: C:\Program Files\AmiBroker\Formulas\Custom\
Reload formulas (Ctrl+Alt+D)
```

**2. Configure Backtest Parameters**
```
Menu: Analysis → Portfolio Backtest

Settings to configure:
- Strategy: Select your AFL
- Symbols: Choose which to test
- Date Range: From - To
- Initial Capital: Starting money
- Position Size: How much per trade
- Commission: Broker fees
- Slippage: Market impact
```

**3. Run Backtest**
```
Click "Backtest" button
Wait for completion
Analysis: 1-5 minutes depending on symbols & timeframe
```

**4. Review Results**
```
Backtest Report shows:
- Total Return %
- Sharpe Ratio
- Max Drawdown
- Win Rate %
- Profit Factor
- Trade List (entry/exit prices)
```

### Key Metrics Explained

```
Total Return = (Ending Value - Starting Value) / Starting Value × 100%
  Good: > 20% annually

Sharpe Ratio = (Return - Risk-free Rate) / Standard Deviation
  Good: > 1.0

Drawdown = Peak to trough decline during holding period
  Acceptable: < 30-40%

Win Rate = (Winning Trades / Total Trades) × 100%
  Good: > 50%

Profit Factor = Gross Profit / Gross Loss
  Good: > 1.5
```

## 💰 Risk Management

### Position Sizing

**Fixed Amount per Trade:**
```
Risk = $500 per trade
Position size = Risk / (Entry - Stop Loss)
Example: $500 / (100 - 98) = 250 shares
```

**Percentage of Capital:**
```
Risk = 2% of account per trade
For $10,000 account: Max risk = $200 per trade
```

**Kelly Criterion:**
```
f = (Win% × Avg Win - Loss% × Avg Loss) / Avg Win
Position size = f × Account size
More mathematically optimal
```

### Stop Loss Rules

```
Always use stop loss!
- Never risk more than 2-5% per trade
- Set at logical support/resistance level
- For breakout: below recent low/high
- For mean reversion: beyond opposite band
```

### Take Profit Rules

```
Exit when:
- Hit profit target (risk:reward ratio)
- Hit trailing stop
- Indicator reversal
- End of trading day
```

## ⚠️ Common Mistakes

### 1. Over-Optimization
```
❌ Optimize too many parameters (curve fitting)
✅ Keep parameters simple and robust
✅ Test on out-of-sample data
```

### 2. Ignoring Commissions & Slippage
```
❌ Backtest without realistic costs
✅ Include broker commissions
✅ Add 1-2% slippage for realism
```

### 3. Low Win Rate Strategies
```
❌ Accept < 40% win rate without high profit factor
✅ Aim for 50%+ win rate if possible
✅ Or high profit factor (3:1 ratio)
```

### 4. Emotional Trading
```
❌ Deviate dari strategy saat live trading
✅ Stick to rules yang sudah ditest
✅ Keep trading journal
✅ Review results regularly
```

### 5. Inadequate Backtesting
```
❌ Backtest hanya 1 tahun data
✅ Test minimal 5-10 years
✅ Include different market conditions
✅ Bear market, bull market, sideways
```

### 6. No Risk Management
```
❌ Trade without stop loss
✅ Always define risk per trade
✅ Never risk > 5% account per trade
✅ Manage position size carefully
```

## 📈 Trading Workflow

### Daily Routine

```
1. Market Open
   - Check overnight news
   - Review watchlist
   - Scan for entry signals

2. During Trading
   - Monitor positions
   - Stick to entry/exit rules
   - Track trades in journal

3. Market Close
   - Close end-of-day positions
   - Review today's trades
   - Plan tomorrow's trades

4. Weekly Review
   - Analyze weekly performance
   - Check strategy metrics
   - Adjust if needed
```

### Monthly Review

```
1. Performance Analysis
   - Total return
   - Win rate
   - Largest win/loss
   - Risk/reward ratio

2. Strategy Evaluation
   - Backtest with new data
   - Check parameter optimization
   - Compare with other strategies

3. Risk Assessment
   - Drawdown analysis
   - Position sizing review
   - Account growth/decline

4. Improvements
   - Document lessons learned
   - Adjust strategy parameters
   - Test new ideas
```

## 📚 Additional Resources

- **AmiBroker Documentation**: https://www.amibroker.com/guide/
- **AFL Reference Guide**: https://www.amibroker.com/guide/aflanguage.html
- **Video Tutorials**: https://www.amibroker.com/video/
- **Community Forum**: https://www.amibroker.com/forums/

## 🎓 Next Steps

1. ✅ Setup AmiBroker ([SETUP_GUIDE.md](SETUP_GUIDE.md))
2. ✅ Learn this Trading Guide
3. → Learn AFL Basics ([docs/AFL_BASICS.md](docs/AFL_BASICS.md))
4. → Explore Strategies ([strategies/](strategies/))
5. → Start Backtesting!

---

**Ready to start your trading journey? Let's analyze some charts! 📊**
