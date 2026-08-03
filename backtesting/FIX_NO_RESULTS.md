# Perbaikan: "No Results" pada Backtest

Backtest menunjukkan "No results" - mari kita perbaiki step by step.

---

## 🔧 Solusi Cepat (Coba urutan ini)

### SOLUSI 1: Sesuaikan Date Range (COBA DULU!)

**Masalah:** Tanggal 1/01/2000 terlalu jauh ke belakang, data mungkin tidak lengkap

**Cara Perbaiki:**
1. Di filter bar, ubah tanggal:
   - **FROM:** 1/06/2026 (June 1, 2026)
   - **TO:** 3/08/2026 (sudah benar)

2. Atau lebih singkat:
   - **FROM:** 1/07/2026 (July 1, 2026)
   - **TO:** 3/08/2026

3. Klik **Apply** atau tekan Enter

4. Lihat apakah hasil muncul

**Kalau sudah ada hasil → SUKSES!**
**Kalau masih "No results" → Lanjut ke Solusi 2**

---

### SOLUSI 2: Disable ISSI Filter

**Masalah:** Filter ISSI cari watchlist "ISSI JUNI 2026" yang mungkin tidak ada/namanya beda

**Cara Perbaiki:**

1. Buka **Formula** (click tombol Formula di toolbar)
2. Cari parameter: **Filter ISSI BERSIH**
3. Ubah dari: **1** (ON) → **0** (OFF)
4. Click **Apply**
5. Run backtest lagi

**Penjelasan:**
- 1 = Filter ON (hanya ISSI)
- 0 = Filter OFF (semua saham)

**Kalau sekarang ada hasil → Filter ISSI masalahnya**
**Kalau masih tidak ada → Lanjut ke Solusi 3**

---

### SOLUSI 3: Relax Parameter (Lebih Permisif)

**Masalah:** Parameter terlalu ketat, tidak ada saham yang qualify

**Ubah ini:**
```
Min VScore:                  dari 7 → ubah ke 6
Max Risk%:                   dari 8 → ubah ke 10
Min Liquidity - V7 (Billions): dari 4 → ubah ke 2
Min SCORE:                   dari 60 → ubah ke 50
```

**Cara:**
1. Di parameter panel (kiri), click setiap parameter
2. Drag slider atau ketik angka baru
3. Click **Apply**
4. Lihat hasil

**Ini akan banyak sinyal. Tujuannya:** memastikan formula berfungsi

**Kalau ada hasil sekarang → Formula bekerja!**
**Kalau masih tidak ada → Lanjut ke Solusi 4**

---

### SOLUSI 4: Cek Data dan Simbol

**Masalah:** Kemungkinan data tidak ter-load atau simbol tidak ada

**Cara cek:**
1. Tutup backtest dialog
2. Go to **View → Watchlist**
3. Pilih watchlist apapun (misal: All Quotes)
4. Lihat apakah ada data (price, volume, dll)
5. Scroll lihat saham yang tersedia

**Kalau data kosong:**
- Perlu load data historical terlebih dahulu
- Go to **Tools → Import Quotes**
- Pilih source data (CSV, API, dll)

**Kalau ada data:**
- Data ada, masalahnya parameter/filter saja
- Kembali ke Solusi 1-3

---

## 🎯 Recommended Quick Fix Path

Coba **URUTANNYA INI:**

### Step A: Paling Cepat (30 detik)
```
1. Ubah date range: 1/07/2026 → 3/08/2026
2. Click Apply
3. Run backtest lagi
4. Ada hasil? → SELESAI ✓
```

### Step B: Jika Step A tidak berhasil (1 menit)
```
1. Buka Formula
2. Ubah "Filter ISSI BERSIH" dari 1 → 0
3. Click Apply
4. Run backtest
5. Ada hasil? → Watchlist ISSI problem (Step D)
6. Tidak ada hasil? → Lanjut Step C
```

### Step C: Jika Step B masih tidak berhasil (2 menit)
```
1. Ubah parameters jadi lebih loose:
   - Min VScore: 6
   - Max Risk%: 10
   - Min Liquidity: 2
2. Click Apply
3. Run backtest
4. Ada hasil? → Parameter terlalu ketat (Step E)
5. Tidak ada hasil? → Kemungkinan data problem
```

### Step D: Perbaiki ISSI Filter
```
Jika ada hasil tanpa filter tapi tidak ada dengan filter:

1. Create watchlist baru:
   - Go to Tools → Watchlist Manager
   - Right-click → New Watchlist
   - Name: "ISSI_BACKTEST"
   - Add saham: ASII, BBCA, BBRI, BMRI, UNVR, CPIN, INTP, TLKM, PGAS, ISAT, SMGR, ADRO, JSMR, LPKR, MNCN

2. Kemudian di formula, ubah:
   ```
   InISSIWatchlist = InWatchListName("ISSI_BACKTEST");
   ```
   (sesuaikan nama watchlist yang baru)

3. Click Apply dan run backtest
```

### Step E: Optimize Setelah Dapat Hasil
```
Kalau sudah ada hasil dengan parameter loose:
- Perlahan ketat-kan kembali
- Cari sweet spot antara many signals dan quality signals
- Min VScore 6-7
- Max Risk 8-10
- Min Liquidity 2-4
```

---

## ✅ Diagnosis Checklist

Sebelum bikin backtest baru, pastikan:

- [ ] Date range sudah sesuai (tidak terlalu ke belakang)
- [ ] Watchlist sudah ter-select/exist
- [ ] Data sudah ter-load di AmiBroker
- [ ] Parameter tidak terlalu ketat
- [ ] Filter ISSI disabled (jika testing awal)

---

## 📋 Report Form

Setelah dicoba, isi ini:

```
Quick Fix Attempt:
Solusi mana yang dicoba: _____ (A/B/C/D/E)
Hasilnya: Ada sinyal / Masih No results

Jika ADA SINYAL:
- Berapa jumlah trades? _____
- Berapa win rate? _____%
- Max Drawdown? _____%

Jika MASIH No results:
- Sudah ubah date range? YES/NO
- Sudah disable ISSI filter? YES/NO
- Sudah loose parameter? YES/NO
- Data ter-load di AmiBroker? YES/NO
```

---

## 🆘 Jika Semua Tidak Berhasil

Kirim info ini untuk bantuan lebih lanjut:

```
1. Screenshot dari Watchlist (menunjukkan saham dan data)
2. Screenshot dari parameter setting
3. Screenshot error message (jika ada)
4. Berapa saham dalam watchlist?
5. Data range mana yang sudah ada di AmiBroker?
```

---

**Coba Solusi A terlebih dahulu - biasanya masalahnya cuma date range!**

Lapor hasilnya setelah dicoba 👆
