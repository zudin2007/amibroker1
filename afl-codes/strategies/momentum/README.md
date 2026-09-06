# Momentum Strategies

Strategi yang menangkap momentum (kecepatan dan force) pergerakan harga. Cocok untuk trader yang ingin profit dari price acceleration.

## 📊 Strategi yang Tersedia

### 1. MACD Momentum (`macd_momentum.afl`)

**Konsep:**
- Menggunakan MACD (Moving Average Convergence Divergence)
- Buy saat MACD cross above signal line (momentum turning positive)
- Sell saat MACD cross below signal line (momentum turning negative)
- Optional: Volume filter untuk confirmation

**Parameter Default:**
- Fast EMA: 12 periode
- Slow EMA: 26 periode
- Signal Period: 9 periode
- Volume Filter: Off (optional)
- Stop Loss: 1.5%

**Keuntungan:**
- ✅ Clear momentum change signals
- ✅ Works di trending dan range-bound markets
- ✅ Multiple levels untuk confirmation (MACD, Signal, Histogram)
- ✅ Volume filter option untuk additional confirmation

**Kekurangan:**
- ❌ Lag dari price action (lagging indicator)
- ❌ Dapat menghasilkan whipsaws di choppy market
- ❌ Perlu tuning parameters

**Best For:**
- Timeframe: 1H, 4H, 1D
- Market: Trending markets (best), also decent di breakouts
- Trader Level: Intermediate

---

## ⚡ Momentum Strategies Explained

### Momentum Concept
```
Momentum = Force + Direction + Speed

Strong momentum = price moving fast dan consistent di satu direction
Weak momentum = price moving slower, direction changing

Momentum divergence = price new high/low tapi momentum tidak
  → Signal potential reversal
```

### MACD Deep Dive

```
MACD Line = 12 EMA - 26 EMA
Signal Line = 9 EMA of MACD
Histogram = MACD - Signal Line

Buy Signal:
- MACD above 0 (positive momentum)
- MACD cross above signal (momentum accelerating)
- Histogram expanding (momentum strengthening)

Sell Signal:
- MACD below 0 (negative momentum)
- MACD cross below signal (momentum decelerating)
- Histogram shrinking (momentum weakening)
```

---

## 🎯 Bagaimana Memilih Momentum Strategy?

**MACD Momentum cocok untuk:**
- Anda ingin jelas momentum change signals
- Prefer mechanical entry/exit rules
- Willing untuk tune parameters
- Trade trending markets primarily

---

## 📈 Trading Setups

### Setup 1: Trend + Momentum Confirmation
```
Entry:
1. Price breaking above resistance
2. MACD crosses above signal
3. Histogram expanding

Exit:
1. MACD crosses below signal
2. Or take profit at target
```

### Setup 2: Early Momentum Detection
```
Entry:
1. Price consolidating
2. MACD starts crossing above signal
3. Before big move up

Exit:
1. Momentum divergence atau
2. MACD cross below signal
```

### Setup 3: Volume Confirmation
```
Entry:
1. MACD cross above signal
2. Volume > 20 EMA volume (dengan filter)
3. Price above key MA

Exit:
1. Volume drying up atau
2. MACD cross below signal
```

---

## 💡 Trading Tips

### Entry Rules
1. **Wait untuk clear MACD cross**
   - Jangan entry saat lingering di zero line
   - Clear cross = better reliability

2. **Confirm dengan price action**
   - Candle pattern bullish/bearish
   - Support/resistance break

3. **Check Context**
   - Market trending? Entry more aggressive
   - Market choppy? Wait untuk clearer signals

### Exit Rules
1. **Stop Loss**
   - Set below recent swing low
   - Typically 1-2% untuk momentum trades

2. **Take Profit**
   - Exit 1st at key resistance
   - Trail stop untuk remaining position

3. **Exit Conditions**
   - MACD cross (most important)
   - Divergence detected
   - Trend reversal confirmed

### Risk Management
- Risk 1-2% per trade (momentum trades dapat volatile)
- Scale in jika trend confirmed
- Scale out saat target hit

---

## 📊 Key Metrics to Monitor

```
MACD Line Value:
- > 0: Positive momentum
- < 0: Negative momentum
- Larger magnitude = stronger momentum

Signal Line:
- Shows MACD trend/direction
- Cross = change in momentum direction

Histogram:
- Shows momentum strength/weakness
- Growing = stronger momentum
- Shrinking = weaker momentum
- Divergence = potential reversal
```

---

## ⚠️ Common Mistakes

1. ❌ Trading every MACD cross
   - Banyak false signals, especially di choppy market
   - Solusi: Add filters (trend, volume, price action)

2. ❌ Ignoring momentum divergence
   - Price new high tapi MACD diverging = warning sign
   - Solusi: Watch untuk divergence, reduce position size

3. ❌ Averaging down losing positions
   - Momentum dapat reverse sharp
   - Solusi: Take the loss, move on

4. ❌ No stop loss
   - MACD wrong signal = big loss
   - Solusi: Always set stop loss before entry

5. ❌ Over-optimizing parameters
   - Perfect backtest ≠ Good future performance
   - Solusi: Keep parameters simple, test multiple years

---

## 📈 Backtesting Checklist

- [ ] Test 5+ years of data
- [ ] Include bull, bear, dan sideways markets
- [ ] Check win rate dan profit factor
- [ ] Review largest winning dan losing trades
- [ ] Check max drawdown
- [ ] Test dengan different market conditions
- [ ] Optimize parameters carefully
- [ ] Walk-forward test para validate

---

## 🔗 Related

- [Momentum Concepts](../../docs/COMMON_PATTERNS.md#momentum)
- [MACD Explanation](../../docs/AFL_BASICS.md#indicators)
- [Divergence Trading](../../docs/COMMON_PATTERNS.md#divergence)

---

*Last Updated: August 2026*
