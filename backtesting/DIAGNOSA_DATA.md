# Diagnosa: Kenapa Tetap "No Results"

Jika masih "No results" setelah disable filter dan loose parameter, masalahnya adalah DATA atau WATCHLIST.

---

## ✅ CEKLIS DIAGNOSIS - Ikuti Urutan Ini

### CEK 1: Apakah Ada Data di AmiBroker?

1. **Tutup Backtest window** (jika terbuka)
2. Go to **View → Watchlist** (atau click tab Watchlist)
3. Pilih watchlist apapun dari dropdown (misal: "All quotes")
4. **LIHAT HASILNYA:**
   - Ada baris/row saham? 
   - Ada column dengan angka (Price, Volume)?

**HASIL CEK 1:**
- [ ] YES - Ada data, lanjut CEK 2
- [ ] NO - Data kosong, lanjut CEK 5

---

### CEK 2: Berapa Banyak Saham Ada?

Di watchlist view yang terbuka:
- Lihat jumlah baris yang ada
- Scroll ke bawah untuk lihat total

**Berapa saham?** _______ 

**HASIL:**
- [ ] > 10 saham, lanjut CEK 3
- [ ] < 10 saham, watchlist terlalu kecil, lanjut CEK 5
- [ ] 0 saham, watchlist kosong, lanjut CEK 5

---

### CEK 3: Apakah Ada Data di Date Range 1/06/2026 - 3/08/2026?

1. Di watchlist, perhatikan kolom **Date**
2. Lihat apakah ada data dari June-August 2026
3. Lihat kolom **Price** - ada angka?

**HASIL:**
- [ ] YES - Ada data di 2026, lanjut CEK 4
- [ ] NO - Data tidak sampai 2026, lanjut CEK 5

---

### CEK 4: Apakah Formula Error?

1. Click tab **Formula** (atau Alt+1)
2. Di editor, lihat bagian paling bawah (status bar)
3. Ada error message (merah)?

**HASIL:**
- [ ] NO ERROR - Formula OK, masalahnya parameter/logic
- [ ] ADA ERROR - Ada syntax error, lanjut CEK 5

---

### CEK 5: Kondisi Data/Setup Apa?

Dari semua CEK di atas:

**Jika CEK 1 = NO (data kosong):**
```
MASALAH: AmiBroker tidak ada data
SOLUSI:
1. Go to Tools → Import Quotes
2. Pilih source (CSV, API, dll)
3. Import data untuk saham yang ingin di-backtest
4. Tunggu import selesai
5. Coba backtest lagi
```

**Jika CEK 2 = NO (watchlist terlalu kecil atau kosong):**
```
MASALAH: Watchlist kosong atau sangat kecil
SOLUSI:
1. Go to Tools → Watchlist Manager
2. Create watchlist baru: "BACKTEST_SAHAM"
3. Add saham dari ISSI: ASII, BBCA, BBRI, BMRI, UNVR, CPIN, INTP, TLKM, PGAS, ISAT, SMGR, ADRO, JSMR, LPKR, MNCN
4. Minimal 20 saham
5. Close Watchlist Manager
6. Di Backtest, pilih watchlist baru
7. Coba backtest lagi
```

**Jika CEK 3 = NO (data tidak ada di 2026):**
```
MASALAH: Database hanya punya data lama (sebelum 2026)
SOLUSI:
1. Perlu import data terbaru
2. Go to Tools → Import Quotes
3. Pilih periode June-August 2026
4. Import setiap saham atau bulk import
5. Coba backtest lagi dengan range 2025-2026

ALTERNATIF: Test dengan periode lama yang ada data
- Misal 2024-2025 jika data ada
- Lihat di watchlist kolom Date berapa range yang tersedia
```

**Jika CEK 4 = YES (ada ERROR):**
```
MASALAH: Formula punya syntax error
SOLUSI:
1. Copy formula error message
2. Di formula editor, review line yang error
3. Common issues:
   - Typo di nama function
   - Missing semicolon
   - Wrong watchlist name dalam formula
4. Bisa coba:
   - Reload formula dari TANA_v5.4_IMPROVED.afl file
   - Atau buka TANA_v5.4_IMPROVED.afl langsung di AmiBroker
```

---

## 🎯 QUICK DIAGNOSIS QUESTIONS

Jawab pertanyaan ini untuk diagnosis lebih cepat:

1. **Apakah AmiBroker sudah pernah digunakan sebelumnya?**
   - YES / NO
   - Jika YES, ada data saham yang sudah? 

2. **Dari mana data diperoleh?**
   - AmiBroker built-in?
   - CSV file?
   - API broker?
   - Belum ada / tidak tahu

3. **Watchlist "ISSI" atau "All quotes" apakah kosong atau ada saham?**
   - Kosong / Ada (berapa banyak?)

4. **Di formula editor, ada error message merah?**
   - YES / NO
   - Jika YES, apa pesan errornya?

---

## 🔧 PALING MUNGKIN: Data Belum Di-Import

Kalau AmiBroker baru diinstall atau belum disetup, kemungkinan:
- ❌ Belum ada data saham sama sekali
- ❌ Atau data yang ada tidak lengkap untuk 2026

**SOLUSI CEPAT:**
1. Go to **Tools → Import Quotes**
2. Pilih source (misal CSV, atau online source)
3. Pilih saham ISSI (ASII, BBCA, BBRI, dll)
4. Import data untuk periode 2025-2026
5. Tunggu selesai
6. Coba backtest lagi

---

## 📝 Report Balik dengan Info Ini:

Setelah cek semua, lapor:

```
CEK 1 - Ada data di AmiBroker?        YES / NO
CEK 2 - Berapa banyak saham?          ___ saham
CEK 3 - Ada data 2026?                YES / NO
CEK 4 - Ada error formula?            YES / NO
CEK 5 - Apa masalah utama?            (pilih dari list)

Jawaban Quick Diagnosis:
1. AmiBroker pernah dipakai?          YES / NO
2. Data dari mana?                     _______
3. Watchlist kosong?                   YES / NO
4. Ada error merah?                    YES / NO

ACTION PLAN:
[ ] Import data (jika belum ada)
[ ] Create/populate watchlist (jika kosong)
[ ] Reload formula (jika error)
[ ] Coba backtest lagi
```

---

## ⚡ Fastest Path Forward

Asumsi paling mungkin: **Belum ada data di AmiBroker**

```
1. Tools → Import Quotes
2. Pilih saham (20-30 ISSI stocks)
3. Date range: 1/01/2025 - 3/08/2026
4. Click Import → tunggu
5. View → Watchlist → Cek ada data
6. Run backtest lagi
```

Jika ini work, backtest baru akan keluar hasil.

---

**Mari cek satu-satu dari CEK 1 sampai 5, lapor hasilnya!**
