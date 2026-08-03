# How to Use Backtest Results Tracking Templates

**Two Templates Available:**
1. **BACKTEST_RESULTS_TRACKING.md** - Comprehensive template with detailed sections
2. **QUICK_RESULTS_TRACKER.csv** - Quick entry spreadsheet format

---

## 🎯 Quick Start (2 minutes)

### Option 1: Use CSV in Excel/Google Sheets
```
1. Open QUICK_RESULTS_TRACKER.csv
2. Right-click → Open with → Excel (or Google Sheets)
3. Fill in values as you complete each backtest
4. Save to track progress
```

### Option 2: Use Markdown in Google Docs/Word
```
1. Open BACKTEST_RESULTS_TRACKING.md
2. Copy content to Google Docs or Word
3. Fill in brackets [____] with your values
4. Use [X] to mark checkboxes
```

---

## 📋 Detailed Instructions by Phase

### PHASE 1: Conservative Test (3 months, strict parameters)

**Before Running Backtest:**
```
1. Open BACKTEST_RESULTS_TRACKING.md
2. Scroll to "PHASE 1: CONSERVATIVE TEST"
3. Note the parameters to use:
   - Min VScore: 7
   - Max Risk %: 6
   - Min SCORE: 70
   - Min TRX: 4B
4. Note the date range: 3 months (6/02/2026 → 3/08/2026)
```

**While Running Backtest:**
```
1. In AmiBroker, adjust parameters to Phase 1 values
2. Set date range (3 months)
3. Run backtest
4. Screenshot results when done
```

**After Backtest Completes:**
```
1. Fill in "Phase 1 Results" table:
   - Test Date: [Today's date]
   - # of Trades: [From backtest results]
   - Win Rate: [From backtest results]%
   - Total Return: [From backtest results]%
   - Max Drawdown: [From backtest results]%
   - Profit Factor: [Calculate or from backtest]
   - etc.

2. Fill in "Phase 1 Trades Detail" for each trade:
   - Stock name
   - Entry/exit dates and prices
   - Return %
   - Any notes

3. Check "Phase 1 Validation Checklist"

4. Mark "Phase 1 Status": PASS / FAIL / NEEDS ADJUSTMENT
```

**Expected Outcome:**
- ✅ 0-2 trades
- ✅ 100% win rate (or close)
- ✅ Validates basic logic works

**If Phase 1 FAILS:**
- Check strategy code for errors
- Verify data is loading properly
- Review AMIBROKER_SETTINGS_CORRECT.md
- See FIX_NO_RESULTS.md for troubleshooting

**If Phase 1 PASSES:**
- Continue to Phase 2

---

### PHASE 2: Aggressive Test (1 year, default parameters)

**Before Running Backtest:**
```
1. Scroll to "PHASE 2: AGGRESSIVE TEST"
2. Note the parameters (defaults):
   - Min VScore: 6
   - Max Risk %: 8
   - Min SCORE: 60
   - Min TRX: 2B
3. Note date range: 1 year (3/08/2025 → 3/08/2026)
```

**While Running Backtest:**
```
1. Adjust AmiBroker parameters to Phase 2 values
2. Set date range to 1 year
3. Run backtest (may take 2-5 minutes)
4. Screenshot results
```

**After Backtest Completes:**
```
1. Fill in "Phase 2 Results" table (all metrics)
2. List each trade in "Phase 2 Trades Summary"
   (Quick format: Stock, Dates, Entry, Exit, Return, Win/Loss)
3. Fill in "Phase 2 Performance Analysis"
   - Best sectors
   - Win rate breakdown
   - Loss analysis
4. Mark "Phase 2 Status": PASS / FAIL / NEEDS ADJUSTMENT
```

**Expected Outcome:**
- ✅ 5-10 trades
- ✅ 40-60% win rate
- ✅ Positive total return
- ✅ <30% max drawdown

**If Phase 2 is Good:**
- Continue to Phase 3 (optimization)

**If Phase 2 is Bad:**
- Go back to Phase 1
- Check if there's an issue with the strategy
- Review trade quality
- Consider if parameters need adjustment

---

### PHASE 3: Optimization (Multiple parameter combinations)

**Purpose:** Find the BEST parameter combination

**Before Running Tests:**
```
1. Scroll to "PHASE 3: TEST MATRIX"
2. Prepare 10-15 parameter combinations to test
3. Use this matrix:
   - VScore: 6, 7, 8
   - Risk %: 6, 8, 10
   - Score: 50, 60, 70
   - TRX: 1B, 2B, 4B
```

**Test Strategy (2 approaches):**

**Approach A: Test One Variable at a Time (Faster)**
```
Round 1: Change VScore only
- Keep Risk=8, Score=60, TRX=2 (Phase 2 baseline)
- Test: VScore 6, 7, 8

Round 2: Change Risk % only (use best VScore)
- Keep Score=60, TRX=2
- Test: Risk 6, 8, 10

Round 3: Change Score only (use best VScore + Risk)
- Keep TRX=2
- Test: Score 50, 60, 70

Round 4: Change TRX only (use best of above)
- Test: TRX 1B, 2B, 4B
```

**Approach B: Full Matrix (More Complete)**
```
Test all 54 combinations (2 × 3 × 3 × 3)
Takes longer but finds the true best
Use if you have time
```

**Running Each Test:**
```
1. Adjust parameters in AmiBroker
2. Run full-year backtest
3. Record results in Phase 3 Test Matrix table:
   - Test #
   - Date
   - All 4 parameters
   - Backtest results (trades, win%, return, drawdown)
   - Brief notes
```

**After All Tests Complete:**
```
1. Sort results by "Total Return" (highest first)
2. Identify top 3 best combinations
3. Fill in "Phase 3 Top 3 Best Results"
4. Fill in "Phase 3 Insights"
   - What parameter changes improved results?
   - Best tradeoffs discovered?
5. Mark "Phase 3 Status": PASS / FAIL / CONTINUE TESTING
```

**CSV Quick Version:**
```
Use QUICK_RESULTS_TRACKER.csv for fast entry:
1. Copy CSV to Excel
2. Fill in Test 3.1, 3.2, ... etc
3. Sort by Total_Return_Percent (descending)
4. Top 3 = your best parameters
```

**Phase 3 Output:**
- BEST PARAMETERS for your strategy
- You'll use these for Phase 4

---

### PHASE 4: Validation (Out-of-sample test)

**Purpose:** Verify parameters aren't overfitted to 2025-2026 data

**Before Running Backtest:**
```
1. Scroll to "PHASE 4: VALIDATION"
2. Enter best parameters from Phase 3
3. Note date range: Fresh data (2023-2025)
   - Use 2 years BEFORE Phase 2 period
   - Or 2 years AFTER Phase 2 period if available
```

**Running Validation Test:**
```
1. Set parameters to Phase 3 best values
2. Set date range to fresh 2-year period (2023-2025 or 2024-2026)
3. Run backtest
4. Record all results in "Phase 4 Results" table
```

**Checking for Overfitting:**
```
Compare Phase 2 vs Phase 4:
- Win rate change: <20% difference = GOOD
- Return change: <30% difference = GOOD
- Drawdown change: <25% difference = GOOD
- Trade frequency: Should be similar = GOOD

If variance > 30% = strategy is OVERFITTED
If variance < 20% = strategy is ROBUST
```

**After Validation:**
```
1. Mark "Phase 4 Status": NOT OVERFITTED / SLIGHTLY / HEAVILY
2. Fill in "Phase 4 Conclusion"
3. If PASSED: Ready for paper trading!
4. If FAILED: Go back to Phase 3, adjust parameters
```

---

## 📊 Using CSV Quick Tracker

**Import to Excel/Google Sheets:**

```
1. Open QUICK_RESULTS_TRACKER.csv with text editor
2. Copy all content
3. In Excel: Paste Special → Values
4. In Google Sheets: Insert → File upload → CSV
5. Adjust column widths
6. Start filling in results
```

**Columns Included:**
- Phase (1, 2, 3.1, 3.2, ... 4)
- Test_Date
- Parameters (VScore, Risk%, Score, TRX)
- Period_Months
- Results (Trades, Win%, Return, Drawdown, Profit Factor, etc.)
- Status
- Notes

**Quick Sorting:**
```
In Excel:
1. Select all data
2. Data → Sort
3. Sort by "Total_Return_Percent" (descending)
4. View best performers at top
```

---

## 💾 Saving Your Results

**Best Practice:**
```
1. Save BOTH versions:
   - Markdown version (.md file)
   - Excel version (.xlsx file)

2. Back up after each phase:
   - Day 1: Phase 1 backup
   - Day 2: Phase 2 backup
   - Day 3-4: Phase 3 backups
   - Day 5: Phase 4 backup

3. Create summary document:
   - What you learned
   - Best parameters found
   - Next steps (paper trading)
```

**File Naming:**
```
TN_v5.0_Backtest_Results_Phase1_2026-08-03.xlsx
TN_v5.0_Backtest_Results_Phase2_2026-08-04.xlsx
TN_v5.0_Backtest_Results_Phase3_FINAL_2026-08-05.xlsx
TN_v5.0_Backtest_Results_Phase4_2026-08-06.xlsx
```

---

## 🎯 Checklist: Are You Ready?

Before starting Phase 1:
- [ ] AmiBroker installed and working
- [ ] Historical data loaded (2011-2026)
- [ ] Watchlist set up with IDX stocks
- [ ] AmiBroker settings verified (commission 0.15%, etc.)
- [ ] TN_v5.0_IMPROVED.afl loaded
- [ ] One of these templates downloaded

**Phase 1 Ready?**
- [ ] Yes, let's start Phase 1!

**Phase 2 Ready?**
- [ ] Phase 1 PASSED
- [ ] Markdown/Excel template updated
- [ ] Ready for 1-year aggressive test

**Phase 3 Ready?**
- [ ] Phase 2 PASSED
- [ ] Have identified 10-15 parameter combos to test
- [ ] Have 2-4 hours for optimization tests

**Phase 4 Ready?**
- [ ] Phase 3 COMPLETED
- [ ] Have identified top 3 parameter sets
- [ ] Have 2 years of fresh data available

---

## 📞 Tips & Tricks

**Speeding Up Phase 3:**
```
Instead of testing all 54 combinations:
1. Test one parameter at a time (faster method)
2. Only test the most promising combos
3. You can save 50% testing time this way
```

**Tracking Trades in Phase 2/3:**
```
When backtest has many trades:
1. Copy results to Excel
2. Paste as values
3. Sort by return %
4. Analyze best/worst trades
5. Look for patterns
```

**If Backtest Takes Too Long:**
```
Backtest running >10 minutes?
1. Reduce date range to 1 year
2. Use fewer stocks in watchlist (test on top 50)
3. Simplify before optimizing
```

**If Results Don't Make Sense:**
```
Backtest showing weird results?
1. Screenshot the results
2. Check: Data is loaded? (Tools → Data Manager)
3. Check: Dates are correct?
4. Check: Parameters saved? (reload formula)
5. See: FIX_NO_RESULTS.md in docs
```

---

## 🎓 Example: Filled-In Template

**PHASE 1 Example:**
```
Test Date: 2026-08-03
Parameters: VScore 7, Risk 6%, Score 70, TRX 4B
Period: 3 months (6/02/2026 → 3/08/2026)

Results:
- # Trades: 1
- Win Rate: 100%
- Total Return: 150%
- Max Drawdown: 5%
- Profit Factor: 100x

Status: PASS (Strategy logic validated!)
```

**PHASE 2 Example:**
```
Test Date: 2026-08-04
Parameters: VScore 6, Risk 8%, Score 60, TRX 2B
Period: 1 year (3/08/2025 → 3/08/2026)

Results:
- # Trades: 8
- Win Rate: 62.5%
- Total Return: 320%
- Max Drawdown: 18%
- Profit Factor: 8.5x

Status: PASS (Default parameters working well!)
Next: Phase 3 optimization
```

**PHASE 3 Example (Top Result):**
```
Best Combination Found:
- VScore: 6
- Risk %: 8
- Score: 60
- TRX: 2B

Results:
- # Trades: 9
- Win Rate: 67%
- Total Return: 410%
- Max Drawdown: 16%
- Notes: Better than Phase 2!
```

---

**Now you're ready to start backtesting!** 🚀

Start with Phase 1 → record results → move to Phase 2 → optimize in Phase 3 → validate in Phase 4.

Good luck with your TN v5.0 IMPROVED strategy backtest! 📊
