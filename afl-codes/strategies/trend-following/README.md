# Trend Following Strategies

Strategi yang mengikuti trend pasar. Strategi ini cocok untuk trader yang ingin memanfaatkan pergerakan trend jangka menengah hingga panjang.

## 📊 Strategi yang Tersedia

### 1. Simple Moving Average Crossover (`simple_moving_average.afl`)

**Konsep:**
- Menggunakan dua Simple Moving Average (SMA) dengan periode berbeda
- Buy saat MA cepat menyilang di atas MA lambat
- Sell saat MA cepat menyilang di bawah MA lambat

**Parameter Default:**
- Fast MA: 10 periode
- Slow MA: 20 periode
- Stop Loss: 1%

**Keuntungan:**
- ✅ Strategi paling sederhana
- ✅ Mudah dipahami dan diimplementasikan
- ✅ Cocok untuk pemula

**Kekurangan:**
- ❌ Lag dalam sinyal (MA lagging indicator)
- ❌ Banyak false signals di market sideways
- ❌ Memerlukan trend yang jelas

**Best For:**
- Timeframe: 1H, 4H, 1D
- Market: Strong trending
- Trader Level: Beginner

---

### 2. EMA Crossover (`ema_crossover.afl`)

**Konsep:**
- Menggunakan Exponential Moving Average (EMA) yang lebih responsive
- Tambahan trend filter dengan 50 EMA
- Buy saat fast EMA cross above slow EMA dan price > trend EMA
- Sell saat fast EMA cross below slow EMA atau price < trend EMA

**Parameter Default:**
- Fast EMA: 12 periode
- Slow EMA: 26 periode
- Trend EMA: 50 periode
- Stop Loss: 2%

**Keuntungan:**
- ✅ EMA lebih responsive terhadap perubahan harga
- ✅ Triple MA filter mengurangi false signals
- ✅ Better untuk swing trading

**Kekurangan:**
- ❌ Masih lag dibanding price action
- ❌ Whipsaw di market sideways
- ❌ Perlu parameter tuning

**Best For:**
- Timeframe: 1H, 4H, 1D, 1W
- Market: Strong to medium trending
- Trader Level: Intermediate

---

## 🎯 Bagaimana Memilih?

**Pilih Simple Moving Average jika:**
- Anda pemula
- Ingin strategi yang sangat mudah dipahami
- Tradable dengan timeframe longer (4H, 1D)

**Pilih EMA Crossover jika:**
- Anda sudah familiar dengan moving averages
- Ingin sinyal yang lebih responsive
- Ingin menambah trend filter untuk accuracy

---

## 📈 Backtesting Tips

1. **Gunakan data historis minimal 5 tahun**
2. **Test di berbagai market conditions** (bull, bear, sideways)
3. **Optimize parameter dengan walk-forward analysis**
4. **Hati-hati dengan overfitting**

---

## 💡 Trading Tips

1. **Ikuti Trend yang Jelas**
   - Pastikan trend sudah established sebelum entry
   - Jangan trade di flat/sideways market

2. **Risk Management**
   - Selalu gunakan stop loss
   - Risk 1-2% per trade
   - Jangan menambah posisi saat losing

3. **Monitoring**
   - Monitor momentum indikator (RSI, MACD)
   - Watchout untuk trend reversal signals
   - Close position saat ada divergence

---

## 🔗 Related

- [Trend Following Concepts](../../docs/COMMON_PATTERNS.md#trend-following)
- [Moving Average Guide](../../docs/AFL_BASICS.md#indicators)

---

*Last Updated: August 2026*
