# TANA v5.4 Backtesting Guide

## Overview
Complete guide for backtesting the TANA v5.4 IMPROVED strategy in AmiBroker for ISSI (Indonesian Sharia Index) stocks.

---

## 📋 Pre-Backtesting Checklist

- [ ] AmiBroker installed and running
- [ ] Historical data for ISSI stocks (minimum 1 year recommended)
- [ ] TANA_v5.4_IMPROVED.afl loaded into AmiBroker
- [ ] Watchlist "ISSI JUNI 2026" created with current ISSI constituents
- [ ] AmiBroker database initialized with price data
- [ ] Backup of original data created

---

## 🎯 Backtesting Setup

### Step 1: Load Strategy into AmiBroker

1. Open AmiBroker
2. Go to **File → New Formula**
3. Copy the entire TANA_v5.4_IMPROVED.afl code into the editor
4. Click **File → Save As** and name it `TANA_v5.4_BACKTEST`
5. Click **Apply** to activate the formula

### Step 2: Configure Basic Parameters

Start with **CONSERVATIVE** settings for initial backtest:

```
Param Values:
- Min TRX30M (M): 1.0
- Min VScore: 7
- Max Risk%: 8
- Min SCORE: 60
- Filter ISSI BERSIH: Yes
- Entry Offset (Ticks): 3
- Stop Loss Offset (Ticks): 1
- Take Profit Offset (Ticks): 2
- Min Liquidity - V7 (Billions): 4
- Exit on Close (vs Low): Low
```

### Step 3: Set Date Range

**Recommended backtesting periods** (test different market conditions):

1. **Recent Uptrend** (Last 3 months)
   - Date: June 1 - August 31, 2026
   - Volatility: Normal to High
   - Trend: Predominantly up

2. **Full Year** (Comprehensive)
   - Date: June 1, 2025 - June 1, 2026
   - Tests: Uptrend, downtrend, sideways
   - Volume: Full variation

3. **Crisis/Drawdown** (Risk testing)
   - Date: March - May 2026 (if available)
   - Tests: Strategy in declining market
   - Volatility: High

---

## 🔍 Running Backtests

### Method 1: Indicator View (Quick Screening)

1. Go to **View → Indicator**
2. Select stocks from ISSI watchlist one by one
3. Observe:
   - Buy signals (where Filter=1)
   - Entry prices (HargaTB)
   - Stop loss levels (HargaSL)
   - Scoring metrics

**Use for:** Quickly finding best candidates, visual pattern recognition

### Method 2: Portfolio Backtest (Comprehensive)

1. Go to **Tools → Backtest → Backtest All symbols in watchlist**
2. Select ISSI JUNI 2026 watchlist
3. Configure backtest settings:

```
Position Settings:
- Initial Capital: IDR 100,000,000 (or your amount)
- Default Position Size: 1% of equity (or fixed # of shares)
- Commission: 0.15% (typical IDX)
- Slippage: 0.05%

Exit Settings:
- Use buy/sell signals from formula
- Allow short selling: NO (Sharia compliance)
- Round lot size: 1

Backtest Range:
- From: (your chosen date)
- To: (your chosen date)
```

4. Click **Run**
5. Analyze results in Backtest Report

---

## 📊 Analyzing Results

### Key Metrics to Track

| Metric | Target | Why It Matters |
|--------|--------|----------------|
| **Total Return %** | > 15% annual | Overall profitability |
| **Win Rate %** | > 50% | Trade quality |
| **Profit Factor** | > 1.5 | Reward vs Risk |
| **Max Drawdown %** | < 15% | Worst-case loss |
| **Sharpe Ratio** | > 1.0 | Risk-adjusted returns |
| **Avg Win/Avg Loss** | > 2.0 | Winning trades bigger |
| **Consecutive Losses** | < 5 | Avoid long losing streaks |

### AmiBroker Backtest Report Sections

1. **Overview Tab**
   - Total Return (%)
   - Buy & Hold Return
   - Number of Trades
   - Win Rate

2. **Equity Curve Tab**
   - Visual growth of capital
   - Drawdown periods
   - Performance vs Buy & Hold

3. **Trades Tab**
   - Entry date & price
   - Exit date & price
   - P&L per trade
   - % Return per trade
   - Risk/Reward ratio

4. **Statistics Tab**
   - Sharpe Ratio
   - Profit Factor
   - Max Consecutive Wins/Losses
   - Monthly/Yearly breakdown

---

## 🧪 Testing Phases

### Phase 1: Conservative Test (Week 1)
**Goal:** Verify basic functionality, no major losses

**Settings:**
- Date Range: Last 3 months
- Min VScore: 7
- Max Risk%: 8
- Entry Offset: 3 ticks
- Position Size: 1% equity

**Success Criteria:**
- ✓ More than 50% win rate
- ✓ Profit factor > 1.0
- ✓ Max drawdown < 10%
- ✓ No critical errors

### Phase 2: Aggressive Test (Week 1-2)
**Goal:** Test with more entries, find optimization

**Settings:**
- Date Range: Full year (6-12 months)
- Min VScore: 6 (more entries)
- Max Risk%: 10 (slightly higher)
- Entry Offset: 2 ticks (earlier entries)
- Position Size: 2% equity

**Success Criteria:**
- ✓ Total return > 20% annually
- ✓ Drawdown < 20%
- ✓ Consistent monthly returns
- ✓ Fewer drawdown months than profit months

### Phase 3: Parameter Optimization (Week 2-3)
**Goal:** Find optimal parameter combinations

**Test Matrix:**

| Entry Offset | Min VScore | Max Risk | Results |
|--------------|-----------|----------|---------|
| 2 | 6 | 10 | ? |
| 2 | 7 | 8 | ? |
| 3 | 6 | 10 | ? |
| 3 | 7 | 8 | ? |
| 4 | 7 | 6 | ? |

Record each combination's:
- Total return
- Win rate
- Max drawdown
- Sharpe ratio

**Choose:** Combination with best risk-adjusted returns (Sharpe)

### Phase 4: Forward Test (Week 3-4)
**Goal:** Validate optimization on recent data

**Method:**
1. Optimize on first 6 months of data
2. Test best parameters on last 6 months
3. Compare: Should perform similarly (within 50%)
4. If performance degrades > 50%, re-optimize

---

## 📝 Recording Results

### Backtest Result Template

```
TANA v5.4 Backtest #1
=====================

Test Date: 2026-08-XX
Backtest Period: 2026-06-01 to 2026-08-31
Duration: 3 months

PARAMETERS:
- Min TRX30M: 1.0
- Min VScore: 7
- Max Risk%: 8
- Min SCORE: 60
- Entry Offset: 3 ticks
- Stop Loss Offset: 1 tick
- Take Profit Offset: 2 ticks
- Min Liquidity: 4B
- Exit on Close: No (exits on Low)

RESULTS:
- Total Return: ___% 
- Buy & Hold Return: ___%
- Number of Trades: ___
- Winning Trades: ___
- Losing Trades: ___
- Win Rate: ___%

RISK METRICS:
- Largest Win: ___% on [date]
- Largest Loss: ___% on [date]
- Max Drawdown: ___%
- Avg Trade Return: ___% 
- Sharpe Ratio: ___

OBSERVATIONS:
- Best performing sectors: ___________
- Worst performing sectors: ___________
- Most frequent entry pattern: ___________
- Average holding period: ___ days
- Issues encountered: ___________

NEXT STEPS:
- [ ] Test different parameters
- [ ] Analyze individual losing trades
- [ ] Check correlation with market conditions
- [ ] Compare with other strategies
```

---

## 🎓 Expected Performance Baseline

Based on the strategy design (10-factor scoring, ISSI focus, sharia compliance):

### Conservative Scenario
- **Annual Return:** 12-18%
- **Win Rate:** 50-55%
- **Max Drawdown:** 8-12%
- **Best For:** Capital preservation focus

### Balanced Scenario
- **Annual Return:** 20-30%
- **Win Rate:** 50-60%
- **Max Drawdown:** 12-18%
- **Best For:** Most traders

### Aggressive Scenario
- **Annual Return:** 30-45%
- **Win Rate:** 45-55% (fewer, bigger wins)
- **Max Drawdown:** 18-25%
- **Best For:** Risk-tolerant traders

---

## 🚨 Common Issues & Solutions

### Issue 1: No Buy Signals Generated
**Possible Causes:**
- Watchlist "ISSI JUNI 2026" not found → Create watchlist with exact name
- Min VScore too high → Lower to 6 temporarily
- Min Liquidity too high → Reduce to 2B for testing
- Min TRX30M threshold too high → Lower to 0.5B

### Issue 2: Too Many Whipsaw Trades
**Possible Causes:**
- Entry Offset too low (2 ticks) → Increase to 4-5
- Min VScore too low (< 6) → Increase to 7-8
- Market in ranging conditions → Use trend filter

### Issue 3: Losses Exceed Wins Significantly
**Possible Causes:**
- Max Risk% too high (>8) → Lower to 6-7%
- Stop Loss Offset too large → Reduce to 0.5-1 tick
- Taking profits too early → Increase TP Offset

### Issue 4: No Trades in Certain Periods
**Possible Causes:**
- Market conditions not suitable (sideways/low volume)
- Parameters too strict
- Try relaxing Min VScore by 1-2 points

---

## 💡 Backtesting Best Practices

### DO's ✅
- [ ] Test multiple periods (uptrend, downtrend, sideways)
- [ ] Record all test results for comparison
- [ ] Validate parameters on out-of-sample data
- [ ] Monitor actual trading vs backtest (check for slippage)
- [ ] Re-optimize quarterly as market conditions change
- [ ] Test with realistic commissions and slippage
- [ ] Use position sizing that matches your capital
- [ ] Check for survivorship bias in stock selection

### DON'Ts ❌
- [ ] Over-optimize (curve fitting) - test on fresh data
- [ ] Ignore liquidity - ensure stocks can be traded
- [ ] Trust single backtest - run multiple periods
- [ ] Forget transaction costs - use realistic figures
- [ ] Backtest only in trending markets - test all conditions
- [ ] Use unrealistic position sizes (e.g., 100% per trade)
- [ ] Ignore correlation with broader market

---

## 📈 Tracking Progress

### Weekly Backtest Log

**Week 1 (Aug 3-9):**
- [ ] Phase 1 conservative test completed
- Results: __________
- Decision: __________

**Week 2 (Aug 10-16):**
- [ ] Phase 2 aggressive test completed
- Results: __________
- Decision: __________

**Week 3 (Aug 17-23):**
- [ ] Parameter optimization runs 1-5
- Best parameters: __________
- Decision: __________

**Week 4 (Aug 24-30):**
- [ ] Forward validation test
- Performance vs optimization: __________
- Final decision: Ready for live trading? YES / NO

---

## 🎯 Next Steps After Backtesting

### If Results Are Good (>15% annual, <15% max DD):
1. ✅ Deploy to paper trading (1-2 weeks)
2. ✅ Monitor live signals vs backtest
3. ✅ Check for slippage, market impact
4. ✅ Start with micro position size (0.5% equity)
5. ✅ Scale up gradually if consistent

### If Results Need Improvement:
1. ⚠️ Identify problem areas (entry/exit timing, parameters)
2. ⚠️ Modify parameters systematically
3. ⚠️ Test again on fresh date ranges
4. ⚠️ Consider adding filters or indicators
5. ⚠️ Review original strategy logic (v5.3 audit)

### If Results Are Poor (<10% annual, >20% max DD):
1. ❌ Strategy may not suit current market conditions
2. ❌ Consider combining with other strategies
3. ❌ Review for systematic errors in logic
4. ❌ Wait for market regime change
5. ❌ Go back to drawing board (v6.0 development)

---

## 📞 Support Resources

- AmiBroker Help: **Tools → Help Topics → Backtesting**
- AmiBroker Formula Reference: **Tools → Formula Reference**
- Strategy Discussion: Review AFL_AUDIT_REPORT.md for deep dive
- Performance Tips: See BEST_PRACTICES.md in amibroker repository

---

*Last Updated: 2026-08-03*
*Strategy Version: 5.4 IMPROVED*
*Tested on: ISSI Index Constituents*
