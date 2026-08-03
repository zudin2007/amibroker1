# Price-NBSA-TN v2.6 IMPROVED Charting Indicator

**Version:** 2.6 IMPROVED  
**Status:** ✅ Production Ready  
**Market:** Indonesian stocks (IDX)

## Overview

Multi-pane charting indicator for manual swing trading analysis on Indonesian stock charts.

**3 Coordinated Panes:**
1. **Price Pane:** Candlesticks + Fractal levels (TN/KN) + Entry/SL/TP + Watermark
2. **NBSA Pane:** Net Buy-Sell Activity analysis (institutional volume)
3. **Volume Pane:** Volume histogram with moving average + spike detection

## Key Features in v2.6

✅ **Parameterized Tick Offsets** - Adjust entry/stop/target without code editing  
✅ **Fixed Title Display** - All info in comprehensive single title  
✅ **NBSA Data Validation** - Shows warning if data unavailable  
✅ **Volume Spike Detection** - Highlights unusual volume bars  
✅ **Auto-Calculated Metrics** - Risk/Reward, Distance from fractal  

## Quick Start

1. Copy `PriceNBSATN_v2.6_IMPROVED.afl` to AmiBroker Formulas folder
2. Create new chart and select the formula
3. Go to Parameters tab to customize offsets and display options
4. Chart updates instantly!

## Customizable Parameters

| Parameter | Default | Range | Purpose |
|-----------|---------|-------|---------|
| Entry Offset (Ticks) | 2 | 1-5 | Ticks above TN for entry |
| Stop Loss Offset (Ticks) | 1 | 0-3 | Ticks below 2-bar low |
| Take Profit Offset (Ticks) | 2 | 1-5 | Ticks below 5-bar low |
| Watermark Size | 1.2 | 0.5-3 | Stock name overlay size |
| Show Volume Spikes? | Yes | Yes/No | Highlight spikes |
| Volume Spike Threshold | 2x | 1-5x | What counts as spike |
| Show NBSA Pane? | Yes | Yes/No | Display NBSA section |

## Use Cases

- **Manual Swing Trading:** Visually confirm entry/exit levels before trading
- **Backtesting Verification:** See historical entries/exits on chart
- **Parameter Tuning:** Test different offset combinations on live data
- **Volume Analysis:** Spot anomalies and smart money activity

## Backward Compatibility

✅ **YES** - Default parameters produce identical output to v2.5

## See Also

- `PriceNBSATN_v2.6_IMPROVEMENTS.md` - Detailed release notes and comparisons
- `TN_v5.0_IMPROVED.afl` - Screener strategy for entry signals
- Combine screener + indicator for complete trading system

---

**Recommended:** Use TN v5.0 IMPROVED screener for signals + Price-NBSA-TN v2.6 for visual confirmation
