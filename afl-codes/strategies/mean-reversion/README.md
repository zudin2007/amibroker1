# Mean Reversion Strategies

Strategi yang mengasumsikan harga akan kembali ke rata-rata setelah pergerakan ekstrem. Cocok untuk trader yang ingin profit dari price correction.

## 📊 Strategi yang Tersedia

### 1. RSI Oversold (`rsi_oversold.afl`)

**Konsep:**
- Menggunakan RSI (Relative Strength Index) untuk identify oversold conditions
- Buy saat RSI cross above 30 (oversold)
- Sell saat RSI cross above 70 (overbought) atau price break below trend MA

**Parameter Default:**
- RSI Period: 14
- Oversold Level: 30
- Overbought Level: 70
- MA Period: 20 (trend filter)
- Stop Loss: 2.5%

**Keuntungan:**
- ✅ Clear oversold/overbought signals
- ✅ Good untuk identifying reversal opportunities
- ✅ Works well in range-bound markets

**Kekurangan:**
- ❌ Dapat menghasilkan false signals di strong trends
- ❌ RSI dapat stay overbought/oversold for extended periods
- ❌ Risk jika trend change sharp

**Best For:**
- Timeframe: 15M, 1H, 4H
- Market: Range-bound, sideways
- Trader Level: Intermediate

---

### 2. Bollinger Bands Reversal (`bollinger_band_reversal.afl`)

**Konsep:**
- Menggunakan Bollinger Bands untuk identify extreme price movements
- Buy saat price touch/cross lower band (oversold)
- Sell saat price touch/cross upper band (overbought)

**Parameter Default:**
- BB Period: 20
- Standard Deviation: 2.0
- Take Profit: 1.5%
- Stop Loss: 2%

**Keuntungan:**
- ✅ Visualisasi yang clear dengan bands
- ✅ Works well saat volatility change
- ✅ Good risk/reward opportunities

**Kekurangan:**
- ❌ Tidak cocok untuk strong trending markets
- ❌ Band squeeze dapat memberikan false breakouts
- ❌ Perlu attention ke volatility changes

**Best For:**
- Timeframe: 1H, 4H, 1D
- Market: Range-bound, moderately volatile
- Trader Level: Intermediate

---

## ⚡ Mean Reversion vs Trend Following

| Aspek | Mean Reversion | Trend Following |
|-------|---|---|
| **Konsep** | Harga kembali ke mean | Harga follow trend |
| **Market** | Sideways, range-bound | Strong trending |
| **Win Rate** | Often High (55-60%) | Lower (45-50%) |
| **Profit Factor** | Medium (1.5-2.0) | High (2.0-3.0+) |
| **Risk** | Medium-High | Low-Medium |
| **Best Timeframe** | Short-term (15M-1H) | Medium-term (1H-1D) |

---

## 🎯 Bagaimana Memilih?

**Pilih RSI Oversold jika:**
- Anda ingin clear entry signals
- Market sedang range-bound
- Prefer mechanical signals (oversold/overbought levels)

**Pilih Bollinger Bands jika:**
- Anda ingin visual confirmation
- Interested di volatility-based trading
- Ingin dynamic support/resistance levels

---

## 📈 Backtesting Tips

1. **Test di Non-Trending Market**
   - Gunakan data dari sideways/consolidation periods
   - Hindari strong bull/bear markets

2. **Check Volatility Conditions**
   - Bands performance berbeda di high vs low volatility
   - Optimize parameters per volatility regime

3. **Risk Management Critical**
   - Mean reversion bisa generate losses jika trend change sharp
   - Selalu gunakan stops

---

## 💡 Trading Tips

### Entry Rules
1. Wait untuk clear oversold/overbought signal
2. Confirm dengan price action (candle pattern)
3. Check volume untuk confirmation

### Exit Rules
1. Take profit saat reversal confirmed
2. Stop loss jika breakout di opposite direction
3. Time-based exit (exit end-of-day)

### Risk Management
- Risk 2-3% per trade (higher risk tolerance)
- Smaller position size dibanding trend following
- Use wider stops untuk volatility

---

## ⚠️ Common Mistakes

1. ❌ Trading mean reversion di trending market
   - Solusi: Use trend filter, identify market regime

2. ❌ Ignoring risk management
   - Solusi: Always set stop loss, size position correctly

3. ❌ Averaging down (adding to losing position)
   - Solusi: Take the stop loss, move on

4. ❌ Holding too long expecting reversal
   - Solusi: Set exit rules, stick to them

---

## 🔗 Related

- [Mean Reversion Concepts](../../docs/COMMON_PATTERNS.md#mean-reversion)
- [Oversold/Overbought Guide](../../docs/AFL_BASICS.md#indicators)
- [Bollinger Bands Explanation](../../docs/COMMON_PATTERNS.md#bollinger-bands)

---

*Last Updated: August 2026*
