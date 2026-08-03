# TANA v5.4 Backtesting Results Log

Track all backtesting runs to compare parameters and find optimal settings.

---

## Backtest Run #1: CONSERVATIVE TEST

**Date:** ____________  
**Duration:** ____________  
**Backtest Period:** From __________ To __________

### Parameters
```
Min TRX30M (M):              _______
Min VScore:                  _______
Max Risk%:                   _______
Min SCORE:                   _______
Entry Offset (Ticks):        _______
Stop Loss Offset (Ticks):    _______
Take Profit Offset (Ticks):  _______
Min Liquidity - V7 (Billions): _______
Exit on Close:               _______
Filter ISSI BERSIH:          _______
```

### Performance Summary
```
Total Return:                _______ %
Buy & Hold Return:           _______ %
Number of Trades:            _______
Winning Trades:              _______
Losing Trades:               _______
Win Rate:                    _______ %
Profit Factor:               _______
```

### Risk Metrics
```
Largest Single Win:          _______ % (Date: ________)
Largest Single Loss:         _______ % (Date: ________)
Max Drawdown:                _______ %
Avg Trade Return:            _______ %
Avg Winning Trade:           _______ %
Avg Losing Trade:            _______ %
Consecutive Wins (Max):      _______ trades
Consecutive Losses (Max):    _______ trades
Sharpe Ratio:                _______
Recovery Factor:             _______
```

### Monthly Performance
| Month | Return % | Trades | Win Rate | Max DD |
|-------|----------|--------|----------|--------|
| Month 1 | ___% | ___ | ___% | ___% |
| Month 2 | ___% | ___ | ___% | ___% |
| Month 3 | ___% | ___ | ___% | ___% |

### Top 5 Winning Trades
```
1. Stock: _______ | Date: _______ | Return: _______% | Duration: ___ days
2. Stock: _______ | Date: _______ | Return: _______% | Duration: ___ days
3. Stock: _______ | Date: _______ | Return: _______% | Duration: ___ days
4. Stock: _______ | Date: _______ | Return: _______% | Duration: ___ days
5. Stock: _______ | Date: _______ | Return: _______% | Duration: ___ days
```

### Top 5 Losing Trades
```
1. Stock: _______ | Date: _______ | Loss: _______% | Duration: ___ days
2. Stock: _______ | Date: _______ | Loss: _______% | Duration: ___ days
3. Stock: _______ | Date: _______ | Loss: _______% | Duration: ___ days
4. Stock: _______ | Date: _______ | Loss: _______% | Duration: ___ days
5. Stock: _______ | Date: _______ | Loss: _______% | Duration: ___ days
```

### Sector Performance
```
Financials:        _______ % return | ___ trades
Basic Materials:   _______ % return | ___ trades
Industrials:       _______ % return | ___ trades
Consumer Goods:    _______ % return | ___ trades
Healthcare:        _______ % return | ___ trades
Technology:        _______ % return | ___ trades
Utilities:         _______ % return | ___ trades
```

### Notes & Observations
```
Best performing conditions: _________________________
Worst performing conditions: ________________________
Most common entry pattern: __________________________
Average holding period: _____________________________
Liquidity issues encountered: _______ YES / NO
False signals (low quality entries): _______________
Market conditions during period: ____________________
Unexpected behaviors: _______________________________

ISSUES TO ADDRESS:
□ Issue: _______________  Solution: _______________
□ Issue: _______________  Solution: _______________
□ Issue: _______________  Solution: _______________

RECOMMENDATION FOR NEXT TEST:
____________________________________________________
____________________________________________________
```

---

## Backtest Run #2: AGGRESSIVE TEST

**Date:** ____________  
**Duration:** ____________  
**Backtest Period:** From __________ To __________

### Parameters
```
Min TRX30M (M):              _______
Min VScore:                  _______
Max Risk%:                   _______
Min SCORE:                   _______
Entry Offset (Ticks):        _______
Stop Loss Offset (Ticks):    _______
Take Profit Offset (Ticks):  _______
Min Liquidity - V7 (Billions): _______
Exit on Close:               _______
Filter ISSI BERSIH:          _______
```

### Performance Summary
```
Total Return:                _______ %
Buy & Hold Return:           _______ %
Number of Trades:            _______
Winning Trades:              _______
Losing Trades:               _______
Win Rate:                    _______ %
Profit Factor:               _______
```

### Risk Metrics
```
Largest Single Win:          _______ % (Date: ________)
Largest Single Loss:         _______ % (Date: ________)
Max Drawdown:                _______ %
Avg Trade Return:            _______ %
Avg Winning Trade:           _______ %
Avg Losing Trade:            _______ %
Consecutive Wins (Max):      _______ trades
Consecutive Losses (Max):    _______ trades
Sharpe Ratio:                _______
Recovery Factor:             _______
```

### Comparison to Run #1
```
Change in Return:     Run #1: ___% → Run #2: ___% (Δ ___%)
Change in Win Rate:   Run #1: ___% → Run #2: ___% (Δ ___%)
Change in Max DD:     Run #1: ___% → Run #2: ___% (Δ ___%)
Change in Sharpe:     Run #1: ___ → Run #2: ___ (Δ ___)

Better metric:        ✓ Run #2
Equal performance:    ○ Both similar
Worse metric:         ✗ Run #2
```

### Notes
```
Observations: _______________________________________
Issues: ______________________________________________
Conclusion: ___________________________________________
```

---

## Parameter Optimization Matrix

Test different parameter combinations to find optimal settings.

### Test Combinations

| Run # | Entry Offset | Min VScore | Max Risk | SL Offset | TP Offset | Return % | Win Rate | Max DD | Sharpe | Rank |
|-------|--------------|-----------|----------|-----------|-----------|----------|----------|--------|--------|------|
| 1 | 2 | 6 | 10 | 1 | 2 | ___% | ___% | ___% | ___ | ___ |
| 2 | 2 | 7 | 8 | 1 | 2 | ___% | ___% | ___% | ___ | ___ |
| 3 | 3 | 6 | 10 | 1 | 2 | ___% | ___% | ___% | ___ | ___ |
| 4 | 3 | 7 | 8 | 1 | 2 | ___% | ___% | ___% | ___ | ___ |
| 5 | 4 | 7 | 6 | 0.5 | 3 | ___% | ___% | ___% | ___ | ___ |
| 6 | 2 | 6 | 8 | 1.5 | 2 | ___% | ___% | ___% | ___ | ___ |
| 7 | 3 | 6.5 | 9 | 1 | 2 | ___% | ___% | ___% | ___ | ___ |
| 8 | 2.5 | 6.5 | 8 | 1 | 2 | ___% | ___% | ___% | ___ | ___ |

### Optimal Parameters Found

**Best Risk-Adjusted Return (Highest Sharpe):**
```
Entry Offset:        _______
Min VScore:          _______
Max Risk:            _______
SL Offset:           _______
TP Offset:           _______
Expected Annual Return: _______ %
Expected Max Drawdown:  _______ %
Sharpe Ratio:           _______
```

**Best Absolute Return:**
```
Entry Offset:        _______
Min VScore:          _______
Max Risk:            _______
Expected Return: _______ %
Max Drawdown:    _______ %
```

**Best Consistency (Least Volatility):**
```
Entry Offset:        _______
Min VScore:          _______
Max Risk:            _______
Win Rate:        _______ %
Sharpe Ratio:    _______
```

---

## Out-of-Sample Validation

Test optimized parameters on data not used in optimization.

**Optimization Period:**
- From: ____________ To: ____________
- Optimal Params Found: ____________________________

**Validation Period:**
- From: ____________ To: ____________
- (Different time range than optimization)

### Validation Results
```
Optimization Period Return:    _______ %
Validation Period Return:      _______ %
Performance Degradation:       _______ % (should be < 50%)

Optimization Period Win Rate:  _______ %
Validation Period Win Rate:    _______ %

Optimization Period Max DD:    _______ %
Validation Period Max DD:      _______ %

RESULT:  ✓ PASSED / ✗ FAILED
         (Degradation < 50% = PASS)
```

### Analysis
```
Did strategy hold up in different market conditions? ___________
Were the parameters overfitted? _______________________________
Is it ready for forward testing? YES / NO
Next steps: _________________________________________________
```

---

## Final Recommendation

**Overall Assessment:**
```
□ READY FOR LIVE TRADING
  - Consistent performance across tests
  - Risk metrics within acceptable range
  - Out-of-sample validation passed
  
□ NEEDS IMPROVEMENT
  - Parameter adjustments needed: _______________
  - Market regime testing needed: _______________
  - Next optimization focus: ____________________
  
□ NOT SUITABLE FOR CURRENT MARKET
  - Reason: ___________________________________
  - Market condition mismatch: __________________
  - Alternative strategy: _______________________
```

**Final Parameters for Trading:**
```
Min TRX30M (M):              _______
Min VScore:                  _______
Max Risk%:                   _______
Min SCORE:                   _______
Entry Offset (Ticks):        _______
Stop Loss Offset (Ticks):    _______
Take Profit Offset (Ticks):  _______
Min Liquidity - V7 (Billions): _______
Exit on Close:               _______
```

**Trading Plan:**
```
Position Size per Trade:     _______ % of equity
Max Concurrent Positions:    _______ positions
Risk per Trade:              _______ % of equity
Daily Loss Limit:            _______ % of equity
Review Frequency:            Daily / Weekly / Monthly
```

**Live Trading Start Date:** ____________

**Performance Tracking:**
- [ ] Monitor actual trades vs backtest
- [ ] Record actual P&L weekly
- [ ] Compare with backtest expectations monthly
- [ ] Plan re-optimization: [Date] ____________

---

*Template Version: 1.0*  
*Strategy: TANA v5.4 IMPROVED*  
*Created: 2026-08-03*
