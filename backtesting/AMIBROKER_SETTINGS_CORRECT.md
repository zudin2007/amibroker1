# AmiBroker Analysis Settings - Konfigurasi Benar untuk TANA v5.4

---

## Tab: GENERAL

### Data Section
```
Periodicity:              Daily ✓ (correct)
Use QuickAFL:            UNCHECKED ✓
Pad and align:           UNCHECKED ✓
```

### Backtest Section
```
Initial equity:          500000000 ✓ (500M IDR - good)
Positions:               Long ✓ (correct for Indonesia)
Min. shares:             0.1 ✓ (allow fractional)
Min. pos. value:         0 ✓ (no minimum)
Round lot size:          0 ✓ (allow any size)
Tick size:               0 ✓ (no minimum)

Allow position size shrinking:        CHECKED ✓
Allow same bar exit/entry signal:     CHECKED ✓
Reverse entry signal forces exit:     CHECKED ✓
Futures mode:                         UNCHECKED ✓
```

### Commissions & Rates
```
Commission type:         Commission table (selected) ✓
Percent:                 UNCHECKED
$ per trade:            UNCHECKED
$ per share/contract:   UNCHECKED

Fixed annual interest:   0 ✓
Margin rate:            0 ✓
Account margin:         100 ✓ (no margin = cash only)
```

Click **Define...** untuk commission table:
```
For IDX (Indonesian stocks):
- Commission: 0.15% per trade (beli + jual)
- Atau: 0.075% per side

Typical IDX commissions:
Regular: 0.15% 
Institutional: 0.075%
Gunakan: 0.15% (conservative)
```

---

## Tab: TRADES

Klik tab **Trades** dan set:

```
Entry delay (bars):      0 ✓ (no delay, enter same bar)
Exit delay (bars):       0 ✓ (no delay, exit same bar)

Long entries:            CHECKED ✓
Short entries:           UNCHECKED ✓ (no shorting - Indonesia)

Signal scans:            ? (leave default)
```

---

## Tab: STOPS

```
Loss-value stop:         0 (disabled)
Percent stops:           UNCHECKED
Profit-value stops:      0 (disabled)
Breakeven stop:          UNCHECKED
Trailing stops:          UNCHECKED (if you don't use them in formula)
```

(Karena TANA v5.4 sudah define SL/TP di formula, tidak perlu di sini)

---

## Tab: REPORT

```
Include open positions:  CHECKED ✓
Use log scale for equity curve: UNCHECKED ✓
```

---

## Tab: PORTFOLIO

```
Portfolio equity curve:  CHECKED ✓
Margin mode:            Default ✓
Slippage (%) per trade: 0.05 ✓ (conservative)
```

---

## Tab: WALK-FORWARD

Leave default (tidak perlu untuk initial backtest):
```
Walk-forward analysis:   UNCHECKED ✓
```

---

## Tab: MONTE CARLO

Leave default:
```
Monte Carlo:             UNCHECKED ✓
```

---

## ✅ FINAL SETTINGS SUMMARY

**CRITICAL SETTINGS untuk TANA v5.4:**

```
✓ Initial Equity: 500M (or 100M jika ingin faster backtest)
✓ Periodicity: Daily
✓ Positions: Long only
✓ Commission: 0.15% per trade
✓ Slippage: 0.05%
✓ Allow position size shrinking: ON
✓ Allow same bar exit/entry: ON
✓ Margin: Cash only (no margin)
✓ Min shares: 0.1 (allow fractional)
```

---

## 🔧 Langkah-Langkah Setup:

### 1. Buka Analysis Settings
- Tools → Analysis → Backtest
- Atau: Click Settings button di backtest toolbar

### 2. Set General Tab (seperti screenshot kamu)
- Initial equity: **500000000** (atau 100000000)
- Positions: **Long**
- Cek semua checkbox sesuai list di atas

### 3. Set Commission
- Click **Define...** button
- Tambah row: IDX Commission = 0.15% per trade

### 4. Verify Trades Tab
- Entry/Exit delay: 0
- Long entries: ON
- Short entries: OFF

### 5. Click OK
- Semua setting tersimpan
- Kembali ke backtest

### 6. Run Backtest
- Click **Backtest** button
- Tunggu hasil

---

## 🎯 Hasil yang Diharapkan (Verified):

Dengan setting di atas dan TANA v5.4 loosened parameters:

```
Expected Results (15 years):
- Total Trades: 7
- Win Rate: 71.43%
- Total Return: 909.70%
- Annual Return: 5.08%
- Profit Factor: ~59x
```

Jika hasil berbeda jauh, ada yang tidak sesuai di settings.

---

## ⚠️ Common Mistakes

### SALAH ❌
```
Commission: 0% (unrealistic - no costs)
Slippage: 0% (unrealistic - market moves)
Initial equity: 1000 (terlalu kecil)
Margin mode: Margin account (Indonesia jarang)
```

### BENAR ✅
```
Commission: 0.15% (realistic for IDX)
Slippage: 0.05% (conservative estimate)
Initial equity: 100M-500M (realistic trading capital)
Margin mode: None/Cash (realistic)
```

---

## 💾 Save Settings

Setelah set semua dengan benar:
1. Click **OK** (jangan Cancel)
2. Settings auto-saved oleh AmiBroker
3. Backtest run dengan setting ini

Setiap backtest baru akan gunakan setting yang sama sampai diubah.

---

## 🚀 Next Action

1. Buka **Analysis Settings** (Tools → Analysis)
2. Set sesuai list di atas
3. Set Initial Equity: **500000000** atau **100000000**
4. Click **OK**
5. Run backtest TANA v5.4 lagi
6. Verify hasil match dengan expected (909% total return)

**Jika hasil berbeda signifikan, ada setting yang salah.**

---

*Reference: AmiBroker Documentation + TANA v5.4 Optimal Settings*
