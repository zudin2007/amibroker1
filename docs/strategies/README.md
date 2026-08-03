# AmiBroker Trading Strategies Documentation

This folder contains comprehensive documentation and examples of trading strategies implemented using AmiBroker Formula Language (AFL).

## Strategies Included

### TN v5.0 IMPROVED - Momentum Screener
**Status:** ✅ Fully Parameterized & Ready for Backtesting

High-performance momentum screening strategy with 10-factor viral scoring system.

- **Expected Returns:** 5-15 trades per year
- **Target Win Rate:** 40%+
- **Key Features:**
  - 8 fully configurable parameters (no hardcoding)
  - Relaxed filters for practical trading
  - Fractal-based entry/exit logic
  - Risk-based position sizing

**Location:** `/docs/strategies/tn-v5.0/`

**Quick Links:**
- [Strategy Guide](./tn-v5.0/README.md) - Complete overview and usage
- [Improvement Guide](./tn-v5.0/IMPROVEMENT_GUIDE.md) - What changed and why
- [Analysis Document](./tn-v5.0/ANALYSIS_AND_FIXES.md) - Original issues fixed
- [AFL Code](./tn-v5.0/TN_v5.0_IMPROVED.afl) - Production-ready formula

---

## How to Use These Strategies

### 1. Load into AmiBroker
Copy the `.afl` file contents into AmiBroker's formula editor and save.

### 2. Configure Parameters
All strategies use configurable parameters accessible in AmiBroker's Parameters tab.

### 3. Backtest
Use AmiBroker's backtesting engine with proper settings:
- Commission: 0.15% (Indonesian market standard)
- Slippage: 0.05%
- Date range: Sufficient historical data (preferably 5+ years)

### 4. Optimize
Test different parameter combinations to find optimal settings for your risk profile.

### 5. Paper Trade
Verify strategy performance on live market data before deploying real capital.

---

## Strategy Development Guidelines

When adding new strategies to this folder:

1. **Code Quality**
   - Use clear variable names
   - Add section comments explaining purpose
   - Avoid hardcoded values (use Param() instead)
   - Remove unused code and duplicates

2. **Documentation**
   - Create README.md with strategy overview
   - Document all parameters and their ranges
   - Include backtesting methodology
   - Provide example parameter combinations

3. **Backtesting**
   - Test on 5+ years of historical data
   - Verify results on out-of-sample data
   - Document performance metrics
   - Include win rate, return, drawdown stats

4. **Version Control**
   - Use semantic versioning (v1.0, v1.1, v2.0)
   - Track changes in version history
   - Keep old versions for reference

---

## Performance Disclaimer

⚠️ **Important:** Past performance does not guarantee future results.

- Strategies are backtested on historical data
- Market conditions change over time
- Actual live performance may differ significantly
- Always use proper risk management and position sizing
- Start with small position sizes before scaling

---

## Related Documentation

- [AmiBroker Getting Started](../GETTING_STARTED.md) - Introduction to AmiBroker
- [Plugin Types](../PLUGIN_TYPES.md) - Information about AmiBroker plugins
- [Architecture Guide](../ARCHITECTURE.md) - System architecture overview

---

## Next Steps

1. Choose a strategy from this folder
2. Read the comprehensive README
3. Load the AFL code into AmiBroker
4. Run backtests with default parameters
5. Optimize parameters based on your goals
6. Paper trade to validate results

---

**Last Updated:** August 3, 2026  
**Maintained By:** Claude Code - Anthropic

For questions about specific strategies, see their individual README files.
