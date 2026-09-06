# Support & Resistance Strategies

Strategi berbasis price action yang menggunakan level support dan resistance sebagai key entry dan exit points.

## 📚 Konsep Dasar

### Apa itu Support & Resistance?

```
RESISTANCE (Tekanan)
    ↓
    ━━━━━━━━━━━  Harga sulit naik di atas level ini
    
    (Price Action Zone)
    
    ━━━━━━━━━━━  Harga sulit turun di bawah level ini
    ↑
SUPPORT (Dukungan)
```

**Support:**
- Price level di mana buying pressure cukup kuat
- Harga sulit menembus ke bawah
- Bounce point untuk reversal

**Resistance:**
- Price level di mana selling pressure cukup kuat
- Harga sulit menembus ke atas
- Rejection point untuk reversal

---

## 🎯 Strategi yang Direkomendasikan

### Level Breakout Strategy

**Konsep:**
- Identify key support/resistance levels
- Buy saat breakout di atas resistance
- Sell saat breakdown di bawah support

**Rules:**
```
Buy Condition:
1. Price breaks di atas resistance level
2. Volume > average (confirmation)
3. Set stop loss di bawah recent swing low

Sell Condition:
1. Price breaks di bawah support level
2. Volume confirms
3. Exit recent long positions
```

### Pivot Point Trading

**Konsep:**
- Menggunakan pivot points sebagai S/R levels
- Trade bounces di pivot levels
- Trade breakouts melalui pivots

**Pivot Levels:**
```
Pivot = (High + Low + Close) / 3

Support 2 = Pivot - (High - Low)
Support 1 = (2 × Pivot) - High
Resistance 1 = (2 × Pivot) - Low
Resistance 2 = Pivot + (High - Low)
```

---

## 📁 Files & Examples

Currently, this folder contains strategic frameworks. You can implement:

1. **Level Breakout Strategy** - Anda dapat customize levels berdasarkan:
   - Daily high/low
   - Weekly levels
   - Monthly levels
   - Pivot points
   - Previous swing points

2. **Support/Resistance Confluence** - Combine dengan:
   - Moving averages
   - Fibonacci levels
   - Trendlines
   - Volume profiles

---

## 💡 How to Create S/R Strategy

### Step 1: Identify Levels

```afl
// Find previous swing high/low
period = 20;
recent_high = Highest(High, period);
recent_low = Lowest(Low, period);

// Or use simple resistance/support
resistance = Highest(High, 50);  // 50-bar high
support = Lowest(Low, 50);       // 50-bar low
```

### Step 2: Set Entry Rules

```afl
// Breakout entry
Buy = Close > resistance[1];
Sell = Close < support[1];

// Bounce entry
Buy = Close > MA(Close, 20) AND Low[1] > support;
Sell = Close < MA(Close, 20) AND High[1] < resistance;
```

### Step 3: Backtest & Optimize

- Test pada different markets
- Check win rate vs profit factor
- Optimize level periods

---

## 🎓 Best Practices

### 1. Level Selection

✅ **DO:**
- Use multiple timeframe levels
- Combine S/R dengan other indicators
- Update levels regularly
- Use volume untuk confirm

❌ **DON'T:**
- Over-complicate level selection
- Use too many levels (creates confusion)
- Ignore recent price action
- Trade right at exact levels (use buffer)

### 2. Entry & Exit

✅ **DO:**
- Wait untuk clear breakout (close, not just wick)
- Confirm dengan volume
- Use risk-based position sizing
- Set stops logically (below/above level)

❌ **DON'T:**
- Fade every bounce (counter-trend)
- Ignore confirmed breakouts
- Over-leverage
- Move stops jika losing

### 3. Timeframes

- **Daily/Weekly levels** - Best untuk swing trading
- **Hourly levels** - Good untuk day trading
- **15M levels** - Short-term scalping

---

## 📊 Risk Management

```
For Support/Resistance Trading:

1. Entry Risk = Entry Price - Stop Loss
2. Position Size = (Risk % of Account) / Entry Risk
3. Take Profit = Entry + (Entry Risk × Risk:Reward Ratio)

Example:
- Account: $10,000
- Risk: 2% = $200
- Entry: 100
- Stop: 98
- Entry Risk: 2
- Position: $200 / 2 = 100 shares
- Take Profit (2:1 ratio): 100 + 4 = 104
```

---

## 🔗 Related

- [Price Action Trading](../../docs/COMMON_PATTERNS.md#price-action)
- [Support & Resistance Identification](../../docs/COMMON_PATTERNS.md#support-resistance)
- [Breakout Trading](../../docs/COMMON_PATTERNS.md#breakout)

---

## 📝 Next Steps

1. Implement level-based strategy menggunakan AFL
2. Backtest pada historical data
3. Start paper trading sebelum real money
4. Monitor dan optimize levels

---

*Last Updated: August 2026*
