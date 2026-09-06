# TN v5.0 IMPROVED - Backtest Results Tracking Template

**Strategy:** TN v5.0 IMPROVED Momentum Screener  
**Date Started:** August 3, 2026  
**Tester:** [Your Name]  
**Overall Status:** [In Progress / Completed]

---

## 📋 Master Results Summary

Quick reference for best performing parameter combinations.

| Phase | Date | VScore | Risk% | Score | TRX(B) | # Trades | Win% | Total Return | MaxDD | Status | Notes |
|-------|------|--------|-------|-------|--------|----------|------|--------------|-------|--------|-------|
| 1     |      |   7    |   6   |  70   |   4    |   [_]    | [_]% |   [_]%       | [_]%  | [__]   |       |
| 2     |      |   6    |   8   |  60   |   2    |   [_]    | [_]% |   [_]%       | [_]%  | [__]   |       |
| 3a    |      |   6    |   6   |  60   |   2    |   [_]    | [_]% |   [_]%       | [_]%  | [__]   |       |
| 3b    |      |   6    |   8   |  50   |   2    |   [_]    | [_]% |   [_]%       | [_]%  | [__]   |       |
| 3c    |      |   7    |   8   |  60   |   2    |   [_]    | [_]% |   [_]%       | [_]%  | [__]   |       |
| 4     |      |  [_]   |  [_]  | [_]   |  [_]   |   [_]    | [_]% |   [_]%       | [_]%  | [__]   |       |

**Legend:** Status = [Ready/Running/Complete/Failed]

---

# PHASE 1: CONSERVATIVE TEST (3 Months)

**Objective:** Validate basic logic with strict parameters  
**Period:** 2026-05-03 to 2026-08-03 (3 months)  
**Expected:** 0-2 trades with 100% win rate

## Phase 1 Parameters

```
Min VScore:      7    (strict)
Max Risk %:      6    (conservative)
Min SCORE:       70   (high quality)
Min TRX (B):     4    (established)
Min TN %:        -5
Max TN %:         5
Min Volume Ratio: 0.5
Volume Weight:   10
```

## Phase 1 Results

| Metric | Value | Target | Status |
|--------|-------|--------|--------|
| **Test Date** | [____] | - | [ ] |
| **# of Trades** | [____] | 0-2 | [ ] |
| **Win Rate** | [____]% | >80% | [ ] |
| **Total Return** | [____]% | Positive | [ ] |
| **Avg Win** | [____]% | — | [ ] |
| **Avg Loss** | [____]% | — | [ ] |
| **Largest Win** | [____]% | — | [ ] |
| **Largest Loss** | [____]% | — | [ ] |
| **Max Drawdown** | [____]% | <10% | [ ] |
| **Profit Factor** | [____]x | >1.5 | [ ] |

## Phase 1 Trades Detail

### Trade 1
```
Entry:
- Stock: ________________
- Date: ________________
- Entry Price: ________________
- Position Size: ________________

Exit:
- Exit Date: ________________
- Exit Price: ________________
- Return: ________________%

Notes: ________________________________________________
```

### Trade 2
```
Entry:
- Stock: ________________
- Date: ________________
- Entry Price: ________________
- Position Size: ________________

Exit:
- Exit Date: ________________
- Exit Price: ________________
- Return: ________________%

Notes: ________________________________________________
```

## Phase 1 Validation Checklist

- [ ] Logic is correct (no obvious bugs)
- [ ] Trades follow expected signals
- [ ] Risk management is working
- [ ] Position sizing is reasonable
- [ ] No unexpected behavior

**Phase 1 Status:** [ ] PASS  [ ] FAIL  [ ] NEEDS ADJUSTMENT

**Phase 1 Notes:**
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

---

# PHASE 2: AGGRESSIVE TEST (1 Year)

**Objective:** Test default parameters for practical trading frequency  
**Period:** 2025-08-03 to 2026-08-03 (1 year)  
**Expected:** 5-10 trades with 40-60% win rate

## Phase 2 Parameters

```
Min VScore:      6    (default)
Max Risk %:      8    (default)
Min SCORE:       60   (default)
Min TRX (B):     2    (default)
Min TN %:        -5
Max TN %:         5
Min Volume Ratio: 0.5
Volume Weight:   10
```

## Phase 2 Results

| Metric | Value | Target | Status |
|--------|-------|--------|--------|
| **Test Date** | [____] | - | [ ] |
| **# of Trades** | [____] | 5-10 | [ ] |
| **Win Rate** | [____]% | >40% | [ ] |
| **Total Return** | [____]% | Positive | [ ] |
| **Avg Win** | [____]% | — | [ ] |
| **Avg Loss** | [____]% | — | [ ] |
| **Largest Win** | [____]% | — | [ ] |
| **Largest Loss** | [____]% | — | [ ] |
| **Max Drawdown** | [____]% | <30% | [ ] |
| **Profit Factor** | [____]x | >1.5 | [ ] |
| **Avg Holding Days** | [____] | — | [ ] |

## Phase 2 Trades Summary

### Trade 1
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 2
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 3
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 4
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 5
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 6
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 7
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

### Trade 8
```
Stock: ________________    Dates: _______ to _______
Entry: ________  Exit: ________  Return: ________%  Win/Loss: [W/L]
Notes: ________________________________________________________________
```

## Phase 2 Performance Analysis

**Best Performing Sectors:**
- [ ] Finance/Banking
- [ ] Technology
- [ ] Retail
- [ ] Manufacturing
- [ ] Other: ________________

**Win Rate Breakdown:**
- Trades with >5% return: [__] trades ([__]%)
- Trades with >10% return: [__] trades ([__]%)
- Trades with >25% return: [__] trades ([__]%)

**Loss Analysis:**
- Trades with <-5% loss: [__] trades
- Trades with <-10% loss: [__] trades
- Trades stopped at SL: [__] trades
- Trades stopped at TS: [__] trades

**Phase 2 Status:** [ ] PASS  [ ] FAIL  [ ] NEEDS ADJUSTMENT

**Phase 2 Notes:**
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

---

# PHASE 3: PARAMETER OPTIMIZATION (Multiple Tests)

**Objective:** Find optimal parameter combination  
**Method:** Test different VScore, Risk%, Score, TRX combinations  
**Expected:** Identify best risk-adjusted return parameters

## Phase 3 Test Matrix

Track all parameter combinations tested:

| Test # | Date | VScore | Risk% | Score | TRX(B) | # Trades | Win% | Return | MaxDD | Notes |
|--------|------|--------|-------|-------|--------|----------|------|--------|-------|-------|
| 3.1    | [__] |   6    |   6   |  50   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.2    | [__] |   6    |   6   |  60   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.3    | [__] |   6    |   6   |  70   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.4    | [__] |   6    |   8   |  50   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.5    | [__] |   6    |   8   |  60   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.6    | [__] |   6    |   8   |  70   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.7    | [__] |   6    |  10   |  50   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.8    | [__] |   6    |  10   |  60   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.9    | [__] |   6    |  10   |  70   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.10   | [__] |   7    |   6   |  50   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.11   | [__] |   7    |   6   |  60   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.12   | [__] |   7    |   6   |  70   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.13   | [__] |   7    |   8   |  50   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.14   | [__] |   7    |   8   |  60   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.15   | [__] |   7    |   8   |  70   |   1    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.16   | [__] |   8    |   6   |  50   |   2    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.17   | [__] |   8    |   6   |  60   |   2    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.18   | [__] |   8    |   8   |  60   |   2    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.19   | [__] |   6    |   6   |  60   |   2    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |
| 3.20   | [__] |   6    |   8   |  60   |   2    |   [__]   | [_]% |  [_]%  | [_]%  | [____] |

## Phase 3 Top 3 Best Results

### Best Result #1
```
Parameters: VScore: [__], Risk%: [__], Score: [__], TRX: [__]B
Results: # Trades: [__], Win Rate: [__]%, Return: [__]%, MaxDD: [__]%
Reason: ________________________________________________________________
```

### Best Result #2
```
Parameters: VScore: [__], Risk%: [__], Score: [__], TRX: [__]B
Results: # Trades: [__], Win Rate: [__]%, Return: [__]%, MaxDD: [__]%
Reason: ________________________________________________________________
```

### Best Result #3
```
Parameters: VScore: [__], Risk%: [__], Score: [__], TRX: [__]B
Results: # Trades: [__], Win Rate: [__]%, Return: [__]%, MaxDD: [__]%
Reason: ________________________________________________________________
```

## Phase 3 Insights

**What Changed When I...:**
- Increased VScore from 6 to 7: ___________________________________________
- Increased Risk% from 6 to 8: ___________________________________________
- Decreased Score from 70 to 50: __________________________________________
- Changed TRX from 2B to 1B: ___________________________________________

**Best Tradeoff Found:**
- More trades vs higher win rate: _________________________________________
- Higher returns vs lower drawdown: _______________________________________

**Phase 3 Status:** [ ] PASS  [ ] FAIL  [ ] CONTINUE TESTING

---

# PHASE 4: VALIDATION (Out-of-Sample Test)

**Objective:** Verify optimized parameters aren't overfitted  
**Period:** 2023-08-03 to 2025-08-03 (Fresh 2-year data before Phase 2)  
**Expected:** Performance similar to Phase 2 (±30% variance acceptable)

## Phase 4 Optimal Parameters

Using best parameters from Phase 3:

```
Min VScore:      [__]
Max Risk %:      [__]
Min SCORE:       [__]
Min TRX (B):     [__]
Min TN %:        [__]
Max TN %:        [__]
Min Volume Ratio: [__]
Volume Weight:   [__]
```

## Phase 4 Results

| Metric | Phase 2 | Phase 4 | Variance | Status |
|--------|---------|---------|----------|--------|
| **# of Trades** | [____] | [____] | [____]% | [ ] |
| **Win Rate** | [____]% | [____]% | [____]% | [ ] |
| **Total Return** | [____]% | [____]% | [____]% | [ ] |
| **Max Drawdown** | [____]% | [____]% | [____]% | [ ] |
| **Avg Trade Return** | [____]% | [____]% | [____]% | [ ] |

## Overfitting Check

- [ ] Win rate variance < 20%? (Good: Strategy is robust)
- [ ] Return variance < 30%? (Good: Results are consistent)
- [ ] Drawdown variance < 25%? (Good: Risk is controlled)
- [ ] Trade frequency similar? (Good: Parameters are stable)

**Phase 4 Status:** [ ] NOT OVERFITTED  [ ] SLIGHTLY OVERFITTED  [ ] HEAVILY OVERFITTED

**Phase 4 Conclusion:**
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

---

# 📊 FINAL SUMMARY & DECISION

## Overall Performance

| Phase | Period | Status | Key Result |
|-------|--------|--------|------------|
| **1 (Conservative)** | 3 months | [____] | [____] |
| **2 (Aggressive)** | 1 year | [____] | [____] |
| **3 (Optimization)** | Multiple | [____] | Best: VScore:[__], Risk:[__], Score:[__], TRX:[__] |
| **4 (Validation)** | 2 years | [____] | Variance: [____]% |

## Optimal Strategy Parameters (FINAL)

```afl
Min VScore:           [__]
Max Risk %:           [__]
Min SCORE:            [__]
Min TRX (Billions):   [__]
Min TN %:             [__]
Max TN %:             [__]
Min Volume Ratio:     [__]
Volume Weight:        [__]
```

## Readiness Checklist

- [ ] Phase 1 PASSED (conservative test ok)
- [ ] Phase 2 PASSED (default parameters ok)
- [ ] Phase 3 COMPLETED (found optimal parameters)
- [ ] Phase 4 PASSED (validation ok, not overfitted)
- [ ] Win rate > 40%?
- [ ] Total return positive?
- [ ] Max drawdown < 30%?
- [ ] Trade frequency 1-2 per month?
- [ ] Risk management working properly?

## Decision

**Ready for:**
- [ ] Paper Trading (paper.example.com)
- [ ] Small Live Trading (0.5% risk per trade)
- [ ] Needs More Optimization (go back to Phase 3)
- [ ] Needs Redesign (fundamental issues found)

## Next Steps

```
1. [ ] Paper trade 2-4 weeks with live market data
2. [ ] Monitor entry/exit quality
3. [ ] Verify slippage and commission impact
4. [ ] Track actual vs expected returns
5. [ ] Start live trading if paper trading is good (0.5% risk/trade)
6. [ ] Scale up gradually after 1 month of profitability
7. [ ] Re-optimize quarterly as market changes
```

---

## 📝 Overall Notes & Observations

### General Comments
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

### Strengths of This Strategy
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

### Weaknesses or Concerns
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

### Future Improvements
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

### Risk Management Notes
```
_________________________________________________________________
_________________________________________________________________
_________________________________________________________________
```

---

**Backtest Completed By:** ___________________  
**Date Completed:** ___________________  
**Total Testing Time:** ___________________  
**Confidence Level:** [ ] Low  [ ] Medium  [ ] High  [ ] Very High

---

*Template Created: August 3, 2026*  
*For: TN v5.0 IMPROVED Momentum Screener Strategy*  
*Use this template to systematically track all backtest results across all 4 phases*
