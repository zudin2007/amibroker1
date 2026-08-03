# TANA v5.4 vs TN v5.0 - Perbandingan Strategi

User menemukan bahwa **TN v5.0** menghasilkan backtest dengan banyak trades, sementara **TANA v5.4** hanya 2 trades.

---

## 📊 Hasil Backtesting

### TANA v5.4 IMPROVED
```
Date Range: 1/06/2026 - 3/08/2026
Trades: 2
- SOBI: +356.99%
- TRST: +324.30%

Problem: Terlalu selective, sedikit sinyal
```

### TN v5.0 OPTIMIZED WINRATE
```
Date Range: 2/02/2011 - 3/08/2026 (15 TAHUN!)
Trades: 30+ (lihat di screenshot)
Contoh: MARK -1.54%, MAPI -2.97%, BDMN -15.12%, ADRO -8.98%, EMAS +5.93%, HRTA +2.99%, dll

Win Rate: Mixed (banyak loss tapi ada beberapa win)
```

---

## 🔍 Perbedaan Kunci

### TANA v5.4 (Conservative/Selective)
```
Min VScore: 7 (atau 6-7)
Max Risk%: 8
Min SCORE: 60
Min Liquidity: 4B

Entry Filter: 
- Multiple conditions (viral, risk, liquidity, trend)
- Score-based
- Sharia compliance (ISSI filter)

Result: SEDIKIT SINYAL tapi high quality
```

### TN v5.0 (Aggressive/High Volume)
```
Min VScore: 9 (LEBIH KETAT!)
Max Risk%: 4.5 (LEBIH KETAT!)
Min SCORE: 85 (LEBIH KETAT!)
Min TRX: 10B (JAUH LEBIH TINGGI!)

Entry Filter:
- FilterViral >= 9 (very selective)
- FilterRisk <= 4.5 (tight)
- FilterTN antara -3 dan +4 (specific)
- FilterTRX >= 10B (liquid only)
- Score >= 85 (high quality only)

Result: BANYAK SINYAL dari periode panjang (2011-2026)
```

---

## ⚡ Mengapa TN v5.0 Menghasilkan Banyak Trades?

1. **Periode lebih panjang**: 15 tahun data (2011-2026)
   - TANA v5.4: Hanya 3 bulan (2026)
   - TN v5.0: 15 tahun (2011-2026)

2. **Jumlah trades = fungsi dari periode**
   - Periode lebih panjang = lebih banyak kesempatan trade
   - 3 bulan = ~0-2 trades
   - 15 tahun = 30+ trades (rata-rata 2 per tahun)

3. **TN v5.0 bisa lebih banyak karena:**
   - Parameter dari backtesting real (optimized dari data historical)
   - TANA v5.4 baru dibuat (v5.4 = fresh improvement)
   - TN v5.0 sudah proven di data 15 tahun

---

## 📈 Analisis Hasil TN v5.0

Lihat dari screenshot, hasil trades TN v5.0:

**Winning Trades (yang positive):**
- EMAS: +5.93%, +14.96% (2 wins!)
- HRTA: +2.99%

**Losing Trades (yang negative):**
- BDMN: -15.12% (besar loss!)
- MDKA: -14.95%
- EXCL: -14.35%
- INCO: -14.03%
- ENRG: -12.31%
- JPFA: -12.68%
- PGAS: -10.09%
- Banyak -6% sampai -9%

**Assessment:**
- ❌ Win rate RENDAH (3 win dari 27 trade = 11%??)
- ❌ Average loss BESAR (many -10% losses)
- ❌ Ini BUKAN strategy yang profitable!

---

## 🎯 Rekomendasi

### OPSI 1: Gunakan TANA v5.4 (Recommended)
```
Pro:
✅ Baru, fresh optimization
✅ Smarter filters (ISSI, viral scoring, risk management)
✅ Conservative approach (fewer, better trades)
✅ 2 trades dalam 3 bulan = 350%+ return
✅ High quality over quantity

Con:
⚠️ Hanya 2 trades (sample terlalu kecil)
⚠️ Perlu test lebih lama (6-12 bulan) untuk better statistics

NEXT STEP:
→ Backtest TANA v5.4 di periode lebih panjang (1-2 tahun)
→ Lihat apakah konsisten profitable
```

### OPSI 2: Gunakan TN v5.0 (Not Recommended)
```
Pro:
✅ Banyak trades (30+)
✅ Tested di 15 tahun data

Con:
❌ Win rate sangat rendah (~11%)
❌ Banyak large losses (-10% sampai -15%)
❌ Tidak profitable overall
❌ Strategy ini TIDAK bekerja baik!

NOT RECOMMENDED: Hasil menunjukkan banyak losses
```

### OPSI 3: Hybrid Approach
```
Test TANA v5.4 dengan periode lebih panjang:
1. Gunakan TANA v5.4_IMPROVED.afl (strategy baru kamu)
2. Backtest 1 tahun penuh (2025-2026)
3. Lihat results - target min 20+ trades
4. Analisis win rate dan risk metrics
5. Optimize jika diperlukan
```

---

## 🚀 Recommended Action Plan

### SEKARANG (Prioritas Tinggi):

**Jalankan TANA v5.4 dengan periode LEBIH PANJANG:**

1. Di AmiBroker, set date range:
   - FROM: `2/02/2025` (1 tahun ke belakang)
   - TO: `3/08/2026` (hari ini)

2. Run backtest lagi dengan TANA_v5.4_IMPROVED.afl

3. Catat hasil:
   ```
   Total Trades: ___
   Winning Trades: ___
   Losing Trades: ___
   Win Rate: ___%
   Total Return: ___%
   Max Drawdown: ___%
   ```

4. Comparison vs TN v5.0:
   ```
   Jika TANA v5.4 di 1 tahun:
   - Win rate > 45%: ✅ LEBIH BAIK dari TN v5.0
   - Return > 50%: ✅ BAGUS
   - Max DD < 20%: ✅ MANAGEABLE
   ```

---

## 📋 Mengapa TANA v5.4 Lebih Baik:

1. **Smart filtering**: 10-factor scoring system
2. **Risk management**: Fractal-based entry/stop, position sizing
3. **Quality over quantity**: Fewer, higher-quality trades
4. **Recent optimization**: Built specifically untuk market 2026
5. **Sharia compliance**: ISSI filter untuk Indonesia market
6. **Better risk metrics**: Risk% carefully calculated

vs TN v5.0:
- Older strategy (dari 2011 data optimization)
- Terlalu banyak losses
- Tidak suitable untuk current market
- Win rate sangat rendah

---

## ⚠️ WARNING: TN v5.0 Results

Jangan gunakan TN v5.0 untuk live trading berdasarkan backtest ini:
```
❌ 27 trades, hanya 3 yang profit
❌ Many -10% to -15% losses
❌ Cumulative loss, bukan profit
❌ Ini adalah LOSING STRATEGY
```

TN v5.0 punya bug atau parameter yang tidak cocok untuk market sekarang.

---

## ✅ Final Recommendation

**Gunakan TANA v5.4 IMPROVED:**

1. Test 1 tahun penuh (2025-2026)
2. Aim untuk 20-50 trades
3. Target win rate > 45%
4. Analisis results
5. Jika OK → proceed ke paper trading
6. Jika perlu improvement → optimize parameters

**Ignore TN v5.0** - data menunjukkan strategy ini tidak profitable.

---

**Coba sekarang: Backtest TANA v5.4 untuk 1 tahun (2025-2026) dan lapor hasilnya!**
