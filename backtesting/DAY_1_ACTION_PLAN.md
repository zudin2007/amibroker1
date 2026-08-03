# TANA v5.4 Backtesting - Day 1 Action Plan

**Objective:** Complete first conservative backtest today  
**Time Required:** 30-60 minutes  
**By End of Day:** You'll have first performance metrics

---

## ✅ Pre-Flight Checklist (5 minutes)

Before starting AmiBroker, verify you have:

- [ ] TANA_v5.4_IMPROVED.afl file ready
- [ ] AmiBroker installed and running
- [ ] Historical data loaded in AmiBroker (at least 6 months)
- [ ] ISSI watchlist created or available
- [ ] Pen & paper or text file open for notes

**Status: READY?** → YES ✓ / NO ✗

---

## Step 1: Load the Strategy (5 minutes)

### In AmiBroker:

1. Go to **File → New Formula**
   - This opens the AFL editor

2. Copy the entire TANA_v5.4_IMPROVED.afl code
   - Select all (Ctrl+A)
   - Paste into the editor (Ctrl+V)

3. Save the formula:
   - Click **File → Save As**
   - Name: `TANA_v5.4_BACKTEST_RUN1`
   - Click Save

4. Click **Apply** button at the bottom right
   - The formula should compile without errors
   - You should see the parameters panel on the left

**✓ CHECKPOINT:** Formula loaded and applied?

---

## Step 2: Set Conservative Parameters (3 minutes)

On the left side, you'll see parameter sliders. Set these to CONSERVATIVE:

```
Min TRX30M (M):              1.0  ← default, keep it
Min VScore:                  7    ← default, good
Max Risk%:                   8    ← default, safe
Min SCORE:                   60   ← default, solid
Entry Offset (Ticks):        3    ← good starting point
Stop Loss Offset (Ticks):    1    ← tight but effective
Take Profit Offset (Ticks):  2    ← reasonable
Min Liquidity - V7 (Billions): 4   ← default, safe
Exit on Close:               0    ← means exit on Low (better)
Filter ISSI BERSIH:          1    ← means ON (recommended)
```

**How to adjust:**
- Click the slider or type the number directly
- Press Enter to apply

**✓ CHECKPOINT:** All parameters set as above?

---

## Step 3: Verify Watchlist (2 minutes)

You need the ISSI watchlist. Check if it exists:

1. Go to **Tools → Watchlist Manager**
2. Look for "ISSI JUNI 2026" or similar ISSI list
3. If it doesn't exist:
   - Right-click in watchlist area
   - Select **New Watchlist**
   - Name it: `ISSI_BACKTEST`
   - Add some ISSI stocks (BBCA, BBRI, BMRI, ASII, UNVR, etc.)

**Minimum stocks to include:** 20-30 major ISSI constituents

**✓ CHECKPOINT:** Watchlist ready?

---

## Step 4: Switch to Watchlist View (2 minutes)

1. Close the formula editor (or minimize it)
2. Go to **View → Watchlist**
3. Select your ISSI watchlist from the dropdown
4. You should see list of stocks with your formula columns

**You should see columns like:**
- Emiten (stock name)
- VScore (viral score)
- SCORE (overall score)
- %TN (price vs fractal)
- Risk%
- TB, SL, TS (entry, stop, target prices)
- RANK

**✓ CHECKPOINT:** Do you see these columns with numbers/colors?

---

## Step 5: Adjust Time Period (3 minutes)

Set the backtest period to LAST 3 MONTHS:

1. Look at the **Date range bar** at the bottom of screen
2. Click the date selector (usually shows current date range)
3. Set:
   - **From:** June 1, 2026
   - **To:** August 31, 2026
   - (Or any recent 3-month period)

4. Click OK to apply

**Why 3 months?**
- Fast backtest (30 minutes)
- Reasonable sample size (~20-40 trades typically)
- Recent market conditions

**✓ CHECKPOINT:** Date range set to 3 months?

---

## Step 6: Check for Buy Signals (5 minutes)

Now look at the watchlist. You should see some stocks highlighted (in watchlist view, buy signals appear as highlighted rows).

**What you're looking for:**
- Stocks with Filter = 1 (TRUE) = buy signal
- Look for green/yellow colored rows
- Check the RANK column (highest scores first)

**If you see NO signals:**
- Problem: Watchlist may be wrong, or market conditions don't match
- Solution: Lower Min VScore to 6
- Solution: Lower Min Liquidity to 2B
- Try again

**If you see TOO MANY signals (>100):**
- Problem: Parameters too loose
- Solution: Raise Min VScore to 8
- Solution: Raise Max Risk to 6%
- Try again

**✓ CHECKPOINT:** Do you see 5-20 buy signals?

---

## Step 7: Run Portfolio Backtest (15-20 minutes)

Now run the actual backtest:

1. Go to **Tools → Backtest → Backtest all symbols in Watchlist**

2. A dialog box opens. Set these:
   ```
   Initial Capital (IDR): 100000000 (100M)
   Position Size: 1% of equity (or choose "Fixed Shares" = 100 shares)
   Commission: 0.15% (typical IDX)
   Slippage: 0.05% (conservative)
   
   Date From: June 1, 2026
   Date To: August 31, 2026
   
   Allow short selling: NO (unchecked)
   ```

3. Click **Backtest** button
   - Wait for it to complete (usually 5-30 seconds)
   - A new report window opens automatically

**✓ CHECKPOINT:** Backtest report window opened?

---

## Step 8: Record Key Metrics (10 minutes)

The backtest report shows results. Find and record these numbers:

### MUST CAPTURE:
```
OVERVIEW TAB:
- Total Return: ____%
- Number of Trades: ___
- Winning Trades: ___
- Losing Trades: ___
- Win Rate: ____%
- Profit Factor: ___

STATISTICS TAB:
- Max Drawdown: ____%
- Largest Win: ____%
- Largest Loss: ____%
- Avg Trade Return: ____%
- Sharpe Ratio: ___

DATES TAB (if available):
- Date range tested: from ____ to ____
```

**Example of what you might see:**
```
Total Return: 18.5%
Number of Trades: 28
Winning Trades: 16
Losing Trades: 12
Win Rate: 57%
Profit Factor: 1.8
Max Drawdown: 11.2%
Largest Win: 4.8%
Largest Loss: -2.1%
Avg Trade Return: 0.66%
Sharpe Ratio: 1.3
```

**✓ CHECKPOINT:** Did you write down all numbers?

---

## Step 9: Quick Analysis (5 minutes)

Look at the numbers you captured and ask:

```
□ Total Return > 10%?           YES / NO
□ Win Rate > 45%?                YES / NO
□ Max Drawdown < 20%?            YES / NO
□ Profit Factor > 1.3?           YES / NO
□ Avg Win > Avg Loss?            YES / NO
```

### Results:
- **4-5 YES answers:** ✅ Excellent! Move to Phase 2
- **3 YES answers:** ⚠️ Good enough, but optimize parameters
- **< 3 YES answers:** ❌ Need major adjustments

**What to do next:**
- If 4-5 YES → Proceed to full year backtest
- If 3 YES → Try different parameters (see troubleshooting)
- If < 3 YES → Check watchlist/data/parameters

**✓ CHECKPOINT:** Results make sense?

---

## Step 10: Look at Individual Trades (Optional but Helpful)

In the same report window:

1. Click on **Trades** tab
2. Look at the list of individual trades
3. Spot check:
   - Are entry prices reasonable? (near TB prices from formula)
   - Are exits sensible? (hitting SL or TS levels?)
   - Do winning trades trend-following? (good)
   - Do losing trades happen in sideways markets? (expected)

**This helps you understand if the strategy logic is working.**

---

## ✅ SAVE YOUR RESULTS

**Create a text file and save:**

```
=== TANA v5.4 BACKTEST RUN 1 ===
Date of Test: August 3, 2026
Test Period: June 1 - August 31, 2026 (3 months)

PARAMETERS USED:
Min VScore: 7
Max Risk%: 8
Entry Offset: 3 ticks
Stop Loss: 1 tick
Take Profit: 2 ticks
Min Liquidity: 4B

RESULTS:
Total Return: __%
Trades: __
Win Rate: __%
Max DD: __%
Profit Factor: __
Sharpe: __

PASS/FAIL:
[ ] PASS - Proceed to Phase 2
[ ] MARGINAL - Adjust parameters and retry
[ ] FAIL - Major revisions needed

NEXT ACTION:
_______________________________
```

---

## 🎯 End of Day Status

By the end of today you should have:

- ✅ Strategy loaded in AmiBroker
- ✅ Conservative backtest completed (3 months)
- ✅ Key metrics recorded
- ✅ Initial assessment done
- ✅ Clear next step identified

**Expected time:** 45 minutes total

---

## 🚨 Troubleshooting Quick Guide

### Problem: "Formula has errors"
**Solution:**
- Check that you copied the ENTIRE AFL code
- Make sure there are no extra spaces at the beginning
- Try copy-paste again carefully
- Contact: Save the error message and review AFL_AUDIT_REPORT.md

### Problem: "No buy signals showing"
**Solution:**
- Lower Min VScore from 7 to 6
- Lower Min Liquidity from 4B to 2B
- Extend date range to 6 months (may be low-signal period)
- Check if watchlist is populated correctly

### Problem: "Backtest takes too long or crashes"
**Solution:**
- Use shorter date range (1-2 months instead of 3)
- Use fewer stocks in watchlist (10-15 instead of 30)
- Try reducing Initial Capital to 50M
- Restart AmiBroker and try again

### Problem: "Results look unrealistic (99% return or -99% loss)"
**Solution:**
- Check position sizing (should be 1% equity or ~100 shares)
- Verify commission is set (0.15% for IDX)
- Check slippage is enabled
- May indicate data quality issues - verify data loaded correctly

### Problem: "Can't find ISSI watchlist"
**Solution:**
- Create new watchlist manually
- Add major ISSI stocks: ASII, BBCA, BBRI, BMRI, UNVR, CPIN, INTP, TLKM
- Or check if it's named differently (ISSI, ISSI2026, etc.)

---

## 📞 After Today's Backtest

Once you complete this, you'll have:

1. **Run #1 Data:** Conservative 3-month test results
2. **Action Decision:** Know if strategy is worth deeper testing
3. **Next Step:** Either proceed to Phase 2 or adjust parameters

**Timeline for full testing:** 
- Week 1: Conservative (TODAY) ✓
- Week 2: Aggressive
- Week 3: Optimization
- Week 4: Validation

---

## 💡 Pro Tips

1. **Take screenshots** of the report for your records
2. **Run multiple 3-month periods** to see consistency
3. **Paper trade for 1-2 weeks** before going live
4. **Keep a trading journal** to compare backtest vs actual results
5. **Re-run quarterly** as market conditions change

---

**Ready? Open AmiBroker and start at Step 1!**

*Estimated completion: 45 minutes*  
*Target time: Before end of today*

---

*Created: 2026-08-03*  
*Version: 1.0*
