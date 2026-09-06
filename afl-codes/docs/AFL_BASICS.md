# AFL Basics - Panduan Pemula

Introduksi ke AmiBroker Formula Language (AFL) - bahasa pemrograman untuk AmiBroker.

## 📚 Daftar Isi

1. [Apa itu AFL?](#apa-itu-afl)
2. [Syntax Dasar](#syntax-dasar)
3. [Variables & Data Types](#variables--data-types)
4. [Built-in Variables](#built-in-variables)
5. [Operators](#operators)
6. [Control Structures](#control-structures)
7. [Functions](#functions)
8. [Practical Examples](#practical-examples)

## 🎯 Apa itu AFL?

**AmiBroker Formula Language (AFL)** adalah bahasa scripting yang dirancang khusus untuk:
- Menulis custom indicators
- Membuat trading strategies
- Analyze market data
- Generate entry/exit signals

**Karakteristik:**
- Mudah dipelajari (similar to C/Pascal)
- Powerful untuk technical analysis
- Supports array operations (time series data)
- Built-in functions untuk trading logic

## 💻 Syntax Dasar

### Hello World Indicator

```afl
// This is a comment
/* Multi-line
   comment style */

// Simple indicator
Plot(Close, "Close Price", colorBlack, styleLine);
```

### Basic Structure

```afl
// 1. Optional: Include directives
#include <IncludeFile.afl>

// 2. Optional: User-defined functions
function MyFunction(param) {
    return param * 2;
}

// 3. Main code
// Analyze data and create output
Plot(Close, "Price", colorBlack);
Buy = Cross(MA(Close, 10), MA(Close, 20));
Sell = Cross(MA(Close, 20), MA(Close, 10));
```

### Rules

```
1. Statements end with semicolon (;)
2. Case sensitive: MA ≠ ma
3. Arrays are 0-indexed
4. Variables auto-created on first use
5. Comments: // or /* */
```

## 🔤 Variables & Data Types

### Primary Data Types

```afl
// Numbers (float/integer)
price = 100.50;
count = 5;

// Strings
symbol = "AAPL";
message = "Price crossed moving average";

// Boolean (0 = false, 1 = true)
is_bullish = 1;
is_bearish = 0;

// Arrays (time series)
prices = Close;  // Array of closes
volumes = Volume;
```

### Variable Naming

```afl
// Good names (descriptive)
fast_ma = MA(Close, 10);
slow_ma = MA(Close, 50);
rsi_value = RSI(14);

// Avoid
x = MA(Close, 10);  // Too generic
a1 = 5;  // Meaningless
```

### Arrays

```afl
// Arrays represent time series
// Each index = one bar
Close[0]   = Today's close
Close[1]   = Yesterday's close
Close[-10] = 10 bars ago

// Working with arrays
for(i = 1; i < BarCount; i++) {
    avg = (Close[i] + Close[i-1]) / 2;
}
```

## 📊 Built-in Variables

### Price Arrays (most important)

```afl
Open     // Opening price
High     // Highest price in period
Low      // Lowest price in period
Close    // Closing price
Volume   // Trading volume
OpenInt  // Open Interest

// Access current bar:
current_price = Close;

// Access previous bar:
prev_price = Close[1];
```

### Special Variables

```afl
BarCount      // Total number of bars
BarIndex      // Current bar number (0-based)
Status        // Market status flags
DateTime      // Date/Time array
```

## 🔧 Operators

### Arithmetic

```afl
a = 10;
b = 3;

add = a + b;        // 13
subtract = a - b;   // 7
multiply = a * b;   // 30
divide = a / b;     // 3.33...
modulo = a % b;     // 1 (remainder)
power = a ^ b;      // 1000 (10^3)
```

### Comparison (return 1 if true, 0 if false)

```afl
a = 10;
b = 5;

a == b  // False (0) - equal
a != b  // True (1) - not equal
a > b   // True (1) - greater
a < b   // False (0) - less
a >= b  // True (1) - greater or equal
a <= b  // False (0) - less or equal
```

### Logical

```afl
// AND - all must be true
if(price > 100 AND volume > 1000000) {
    // Execute
}

// OR - at least one must be true
if(price < 50 OR price > 200) {
    // Execute
}

// NOT - negation
if(NOT is_trending) {
    // Execute
}
```

## 🔀 Control Structures

### If Statement

```afl
Close = 105;

if(Close > 100) {
    message = "Price above 100";
} else if(Close < 100) {
    message = "Price below 100";
} else {
    message = "Price equals 100";
}
```

### For Loop

```afl
// Loop through all bars
for(i = 1; i < BarCount; i++) {
    if(Close[i] > Open[i]) {
        // Green candle
    }
}

// Loop with step
for(i = 1; i <= 100; i = i + 5) {
    // i = 1, 6, 11, 16, ...
}
```

### While Loop

```afl
i = 0;
while(i < 10) {
    // Do something
    i = i + 1;
}
```

## 📦 Functions

### Using Built-in Functions

```afl
// Moving Average
ma10 = MA(Close, 10);
ma20 = SMA(Close, 20);      // Simple MA
ma_exp = EMA(Close, 30);    // Exponential MA

// Indicators
rsi = RSI(14);
macd = MACD();
bb_upper = BBandTop(Close, 20, 2);

// String functions
symbol = Name();
text = "Buy signal at " + Close;
```

### Creating Custom Functions

```afl
// Simple function
function DoublePrice(price) {
    return price * 2;
}

// Function with multiple parameters
function WeightedAverage(val1, val2, weight) {
    return (val1 * weight + val2 * (1 - weight));
}

// Usage
result = DoublePrice(Close);
weighted = WeightedAverage(Close, MA(Close, 20), 0.6);
```

### Common Built-in Functions

```afl
// Math
Abs(x)           // Absolute value
Max(a, b)        // Maximum of two
Min(a, b)        // Minimum of two
Sqrt(x)          // Square root
Log(x)           // Natural logarithm

// Time series
Highest(price, periods)   // Highest in X bars
Lowest(price, periods)    // Lowest in X bars
HHV(price, periods)       // Same as Highest
LLV(price, periods)       // Same as Lowest

// Indicators
CrossAbove(a, b)  // a crosses above b
CrossBelow(a, b)  // a crosses below b
Cross(a, b)       // Either crossover
```

## 💡 Practical Examples

### Example 1: Simple Moving Average Crossover

```afl
// Parameters
FastPeriod = 10;
SlowPeriod = 20;

// Calculate MAs
FastMA = EMA(Close, FastPeriod);
SlowMA = EMA(Close, SlowPeriod);

// Generate signals
Buy = Cross(FastMA, SlowMA);   // Fast crosses above Slow
Sell = Cross(SlowMA, FastMA);  // Slow crosses above Fast

// Plot
Plot(Close, "Close", colorBlack, styleLine);
Plot(FastMA, "Fast MA", colorBlue, styleLine);
Plot(SlowMA, "Slow MA", colorRed, styleLine);

// Signal colors
PlotShapes(Buy * shapeUpArrow, colorGreen, 0, Low);
PlotShapes(Sell * shapeDownArrow, colorRed, 0, High);
```

### Example 2: RSI Overbought/Oversold

```afl
// RSI indicator
rsi_period = 14;
rsi_value = RSI(rsi_period);

// Thresholds
overbought = 70;
oversold = 30;

// Generate signals
Buy = Cross(oversold, rsi_value);      // RSI goes above 30
Sell = Cross(rsi_value, overbought);   // RSI goes above 70

// Plot
Plot(Close, "Close", colorBlack);
Plot(rsi_value, "RSI", colorBlue);
Plot(overbought, "Overbought", colorRed);
Plot(oversold, "Oversold", colorGreen);
```

### Example 3: Support & Resistance Breakout

```afl
// Define support and resistance
period = 20;
resistance = Highest(High, period);
support = Lowest(Low, period);

// Breakout signals
BreakoutUp = Close > resistance[1];    // Above previous resistance
BreakoutDown = Close < support[1];     // Below previous support

// Buy on breakout up, sell on breakout down
Buy = BreakoutUp;
Sell = BreakoutDown;

// Plot
Plot(Close, "Price", colorBlack, styleLine);
Plot(resistance, "Resistance", colorRed, styleDashed);
Plot(support, "Support", colorGreen, styleDashed);

// Mark signals
PlotShapes(Buy * shapeUpArrow, colorGreen);
PlotShapes(Sell * shapeDownArrow, colorRed);
```

## 📝 Common AFL Patterns

### Pattern 1: Entry & Exit

```afl
// Entry condition
entry_condition = (FastMA > SlowMA) AND (Close > Highest(High, 10));

// Exit conditions
exit_profit = Close > BuyPrice + 50;
exit_loss = Close < BuyPrice - 30;

Buy = entry_condition;
Sell = exit_profit OR exit_loss;
```

### Pattern 2: Multiple Confirmations

```afl
// Trend confirmation
trend_up = MA(Close, 10) > MA(Close, 20) AND Close > MA(Close, 50);
trend_down = MA(Close, 10) < MA(Close, 20) AND Close < MA(Close, 50);

// Momentum confirmation
rsi_bullish = RSI(14) > 50;
rsi_bearish = RSI(14) < 50;

// Combined signal
Buy = trend_up AND rsi_bullish;
Sell = trend_down AND rsi_bearish;
```

### Pattern 3: Position Sizing

```afl
// Calculate position size based on risk
risk_percent = 2;           // Risk 2% per trade
atr_value = ATR(14);        // Average True Range

// Position size inverse to volatility
position_size = (Equity() * risk_percent / 100) / atr_value;

// Limit position size
position_size = Min(position_size, 1000);  // Max 1000 shares
```

## 🚀 Best Practices

1. **Use Comments**
   ```afl
   // Explain WHY, not WHAT
   // Buy when momentum turns positive
   Buy = Cross(0, MACD());
   ```

2. **Clear Variable Names**
   ```afl
   ✅ fast_ma = EMA(Close, 10);
   ❌ x = EMA(Close, 10);
   ```

3. **Structure Your Code**
   ```afl
   // 1. Parameters
   // 2. Calculations
   // 3. Signals
   // 4. Plotting
   ```

4. **Test Incrementally**
   ```afl
   // Start simple, add complexity gradually
   // Test each part before combining
   ```

## 📚 Next Steps

1. ✅ Learn AFL basics (this guide)
2. → Explore [COMMON_PATTERNS.md](COMMON_PATTERNS.md)
3. → Study examples in [../../strategies/](../../strategies/)
4. → Create your first strategy
5. → Backtest and optimize

## 🔗 Additional Resources

- **AFL Reference**: https://www.amibroker.com/guide/aflanguage.html
- **Code Snippets**: https://www.amibroker.com/code/snippets/
- **Community Forum**: https://www.amibroker.com/forums/

---

**Happy coding! Start writing your first AFL formula today! 💻**
