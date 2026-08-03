# Backtesting Metrics Explained - Quick Reference

Quick guide to understanding and interpreting backtest results for TANA v5.4.

---

## 📊 Core Profitability Metrics

### Total Return (%)
**What it means:** Total profit/loss as a percentage of starting capital
```
Example: If you start with 100M and end with 120M, Total Return = 20%
```
**Target for TANA v5.4:** 
- Conservative: 12-18% annually
- Balanced: 20-30% annually  
- Aggressive: 30-45% annually

**Red flags:**
- ⚠️ Negative return = Strategy loses money
- ⚠️ < 10% annual = Too slow (could just invest in bonds)

---

### Number of Trades
**What it means:** Total number of buy signals triggered

```
Typical range: 30-100 trades per 6-month period
```

**What's optimal:**
- Too few (< 20): Strategy too selective, may miss opportunities
- Just right (30-100): Generates enough signals for statistics
- Too many (> 200): May generate noise, overtrading

**Check:**
- Are trades clustered in certain months?
- Are there dry periods with no signals?

---

### Win Rate (%)
**What it means:** Percentage of trades that make money

```
Win Rate = (Winning Trades / Total Trades) × 100

Example: 60 winning trades out of 100 total = 60% win rate
```

**Target for TANA v5.4:**
- Minimum: 45%
- Good: 50-55%
- Excellent: 60%+

**Important notes:**
- ⚠️ Win rate alone doesn't mean profitability
- ⚠️ 40% win rate is OK if winning trades are much bigger
- ✅ Should be at least 45-50% for consistency

---

### Profit Factor
**What it means:** Ratio of gross profits to gross losses

```
Profit Factor = Total Wins / Total Losses

Example: Total wins = 50M, Total losses = 30M
Profit Factor = 50/30 = 1.67
```

**Interpretation:**
- < 1.0: Strategy loses money ❌
- 1.0-1.2: Barely profitable ⚠️
- 1.2-1.5: Good ✅
- 1.5-2.0: Very good ✅✅
- > 2.0: Excellent ✅✅✅

**Example:**
- Profit Factor 1.5 = For every 1M you lose, you make 1.5M ✅

---

## 📉 Risk Metrics (CRITICAL)

### Max Drawdown (%)
**What it means:** Largest peak-to-trough decline during the backtest period

```
Example: Capital grows to 120M, then drops to 100M
Max Drawdown = 20M / 120M = 16.67%
```

**Target for TANA v5.4:**
- Conservative: 8-12%
- Balanced: 12-18%
- Aggressive: 18-25%

**Why it matters:**
- Shows worst-case scenario
- Affects your ability to stay in the trade
- Watch if drawdown > 25% (psychologically very hard)

**Red flags:**
- ⚠️ > 30%: Strategy is too risky
- ⚠️ Drawdown gets deeper and deeper (recovery not happening)

---

### Largest Single Loss (%)
**What it means:** Worst single trade

```
Example: You lose 5% of account on one trade
```

**Target for TANA v5.4:**
- Should be: 2-4% of account per trade
- ❌ Never > 5% per single trade

**Why it matters:**
- Shows if one bad trade can wipe you out
- Indicates if stop losses are working

---

### Consecutive Losses (Max)
**What it means:** Longest losing streak

```
Example: 5 losing trades in a row = Max 5 consecutive losses
```

**Target:**
- Good: < 4 consecutive losses
- Acceptable: 4-6 consecutive losses
- Risky: > 6 consecutive losses

**Why it matters:**
- Shows if you can psychologically handle the strategy
- Affects position sizing decisions
- If you have 10 consecutive losses with 2% loss each = 20% drawdown

---

### Average Winning Trade vs Average Losing Trade
**What it means:** Ratio of size of winning trades to losing trades

```
Avg Win: 3%
Avg Loss: 1%
Ratio: 3:1 (Excellent - you win 3x your losses)
```

**Target for TANA v5.4:**
- Minimum: 1.5:1 ratio
- Good: 2:1 ratio
- Excellent: 3:1 ratio or higher

**Example scenarios:**
- 2:1 ratio means: For every 1% you lose, you make 2%
  - 50% win rate with 2:1 ratio = profitable
  - This is how a strategy with < 60% win rate can still make money

---

## 📈 Risk-Adjusted Return Metrics

### Sharpe Ratio
**What it means:** Return generated per unit of risk taken

```
Sharpe Ratio = (Average Return - Risk Free Rate) / Volatility

Risk Free Rate ≈ Indonesian Government Bond yield (~6%)
```

**Target for TANA v5.4:**
- Poor: < 0.5
- Acceptable: 0.5-1.0
- Good: 1.0-1.5
- Excellent: > 1.5

**Interpretation:**
- Higher is better
- Compares strategies fairly (accounts for risk taken)
- Use this to compare 2 strategies
  - Strategy A: 30% return, 20% drawdown
  - Strategy B: 25% return, 10% drawdown
  - B likely has higher Sharpe (better risk-adjusted)

---

### Recovery Factor
**What it means:** Total profit divided by max drawdown

```
Recovery Factor = Total Profit / Max Drawdown

Example: 
Total Profit: 20M
Max Drawdown: 10M
Recovery Factor = 20 / 10 = 2.0
```

**Target:**
- < 1.0: Bad (profit < max drawdown)
- 1.0-1.5: Okay
- 1.5-2.0: Good
- > 2.0: Excellent

**Example:**
- Recovery Factor 2.0 means you made 2x the max drawdown as profit
- Shows strategy can recover and profit beyond worst loss

---

## 🎯 Trade Quality Metrics

### Average Trade Duration
**What it means:** Average time a position is held

```
Example: Average holding period = 3 days
```

**Target for TANA v5.4:**
- Expected: 2-7 days (short-term swing trading)
- Too short (< 1 day): High commissions, slippage impact
- Too long (> 15 days): May miss better opportunities

**Observation:**
- Is duration consistent? (Good = yes)
- Longer in winners, shorter in losers? (Good = yes)

---

### Best vs Worst Streaks
**What it means:** Best and worst consecutive performance

```
Best streak: 8 winning trades
Worst streak: 6 losing trades

This shows resilience
```

**What to look for:**
- ✅ Good: Best streak 2x or more than worst streak
- ⚠️ Okay: Best streak similar to worst streak
- ❌ Bad: Worst streak longer than best streak

---

## 🔄 Consistency Metrics

### Monthly Performance
**What it means:** Returns broken down by month

```
Jan: +5%
Feb: -2%
Mar: +8%
...monthly pattern
```

**Good signs:**
- ✅ Positive months > negative months
- ✅ No month with loss > -10%
- ✅ Pattern is similar across multiple years

**Red flags:**
- ⚠️ One good month, rest are bad
- ⚠️ Highly inconsistent (10% in Jan, -15% in Feb)
- ❌ Consistent losses in specific months

---

### Sector Performance
**What it means:** How strategy performs in different stock sectors

```
Financials: +25% (20 trades)
Technology: +15% (15 trades)
Industrials: -5% (10 trades)
```

**What to check:**
- ✅ Strategy profitable across most sectors
- ✅ Losses concentrated in 1-2 sectors
- ⚠️ If sector performs well, is it just market-driven?

---

## 🔴 Red Flags - When to Reject Results

Stop and reconsider if you see:

```
❌ Win Rate < 40%
   → Unless average win is 3x+ larger than average loss
   
❌ Max Drawdown > 30%
   → Strategy too volatile, psychological damage risk
   
❌ Profit Factor < 1.2
   → Marginal profitability, not worth real trading risk
   
❌ Negative total return
   → Strategy doesn't work in this market regime
   
❌ Average win < Average loss
   → You're cutting winners and letting losers run (backwards)
   
❌ Sharpe Ratio < 0.5
   → Returns not worth the risk taken
   
❌ More than 50% of profit from 1-2 trades
   → Getting lucky, not systematic
   
❌ All profit comes from 1-2 months
   → Not robust, may be curve-fitted
   
❌ Highly inconsistent monthly returns
   → Doesn't work reliably in all conditions
```

---

## ✅ Ideal Backtest Results Summary

**Conservative Profile (Capital Preservation):**
```
Annual Return:        15% +
Win Rate:             52%+
Max Drawdown:         < 12%
Sharpe Ratio:         > 1.0
Profit Factor:        > 1.4
Avg Win/Loss Ratio:   > 1.5
Consecutive Losses:   < 4
Recovery Factor:      > 1.5
```

**Balanced Profile (Growth & Safety):**
```
Annual Return:        25% +
Win Rate:             50%+
Max Drawdown:         < 18%
Sharpe Ratio:         > 1.2
Profit Factor:        > 1.5
Avg Win/Loss Ratio:   > 2.0
Consecutive Losses:   < 5
Recovery Factor:      > 1.8
```

**Aggressive Profile (Maximum Growth):**
```
Annual Return:        35% +
Win Rate:             48%+
Max Drawdown:         < 25%
Sharpe Ratio:         > 1.0
Profit Factor:        > 1.6
Avg Win/Loss Ratio:   > 2.5
Consecutive Losses:   < 6
Recovery Factor:      > 2.0
```

---

## 📋 Quick Decision Checklist

After backtest results, ask:

- [ ] Is annual return > 15%?
- [ ] Is win rate > 45%?
- [ ] Is max drawdown < 25%?
- [ ] Is Sharpe ratio > 0.8?
- [ ] Is profit factor > 1.3?
- [ ] Is avg win > avg loss?
- [ ] Can I handle the max drawdown psychologically?
- [ ] Did results hold up in different time periods?
- [ ] Are the results robust or curve-fitted?

**Scoring:**
- 8-9 YES → ✅ Ready for paper trading
- 6-7 YES → ⚠️ Needs parameter adjustment
- < 6 YES → ❌ Significant rework needed

---

## 🎓 Relationship Between Metrics

### Win Rate vs Average Win/Loss Ratio

These compensate for each other:

```
Scenario A:
- Win Rate: 60%
- Avg Win/Loss: 1.0 (same size wins and losses)
- Result: Profitable but modest

Scenario B:
- Win Rate: 40%
- Avg Win/Loss: 3.0 (winners 3x bigger than losses)
- Result: Very profitable despite lower win rate

Scenario C (IDEAL):
- Win Rate: 55%
- Avg Win/Loss: 2.0 (winners 2x bigger)
- Result: Highly profitable and resilient
```

### Return vs Drawdown Tradeoff

```
Low Risk Profile:     High Return Profile:
15-18% Return         35-45% Return
8-12% Drawdown        20-25% Drawdown
Higher Sharpe         Lower Sharpe
More consistent       More volatile

→ Choose based on your tolerance
```

---

## 💡 Important Notes

1. **Past Performance ≠ Future Results**
   - Backtest assumes conditions stay the same
   - Markets change (regimes, volatility, correlation)
   - Re-optimize quarterly

2. **Backtest vs Live Trading Differences**
   - Slippage (actual price worse than backtest)
   - Commissions (eating into profits)
   - Market impact (large orders move price)
   - Liquidity (can't always exit at exact stop)
   
   → Expect 10-20% lower returns in live trading

3. **Overfitting (Curve Fitting)**
   - Optimization on same data used for testing
   - Solution: Test on fresh out-of-sample data
   - If performance drops > 50%, strategy is overfitted

4. **Survivorship Bias**
   - Backtest only includes stocks that survived to today
   - Stocks that went bankrupt were delisted
   - Solution: Use historical constituents of index

---

## 🚀 Next Steps After Interpreting Results

1. **If metrics look good:**
   - ✅ Proceed to paper trading (1-2 weeks)
   - ✅ Monitor live signals vs backtest
   - ✅ Check slippage impact
   - ✅ Start small position size (0.5-1% equity)

2. **If metrics are marginal:**
   - ⚠️ Run parameter optimization
   - ⚠️ Test different time periods
   - ⚠️ Add additional filters
   - ⚠️ Plan second backtest

3. **If metrics are poor:**
   - ❌ Diagnose core issue (entry/exit/stops)
   - ❌ Review AFL logic (reference audit report)
   - ❌ Consider market regime mismatch
   - ❌ Plan major revisions (v6.0)

---

*Reference Guide Version: 1.0*  
*For Strategy: TANA v5.4 IMPROVED*  
*Created: 2026-08-03*
