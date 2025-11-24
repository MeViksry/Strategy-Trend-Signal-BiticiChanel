# Strategy Trend Signal [BiticiChanel]

![Version](https://img.shields.io/badge/version-5.0-blue.svg)
![License](https://img.shields.io/badge/license-MPL--2.0-green.svg)
![Platform](https://img.shields.io/badge/platform-TradingView-orange.svg)
![Language](https://img.shields.io/badge/language-Pine%20Script%20v5-purple.svg)
![Status](https://img.shields.io/badge/status-Active-success.svg)

## Deskripsi

**Strategy Trend Signal [BiticiChanel]** adalah strategi trading otomatis berbasis Pine Script v5 yang menggabungkan multiple indikator teknikal canggih untuk mengidentifikasi peluang trading dengan tingkat akurasi tinggi. Strategi ini mengintegrasikan Smart Money Concepts (SMC), Market Structure Analysis, Support & Resistance dinamis, Momentum indicators, dan sistem filter anti-repaint yang ketat.

Dirancang untuk trader yang menginginkan sistem trading komprehensif dengan manajemen risiko otomatis, trailing stop cerdas, dan visualisasi data yang jelas melalui dashboard real-time.

## Kontak & Komunitas

[![GitHub](https://img.shields.io/badge/GitHub-MeViksry-181717?style=for-the-badge&logo=github)](https://github.com/MeViksry/Strategy-Trend-Signal-BiticiChanel)
[![Telegram](https://img.shields.io/badge/Telegram-biticiapp2-26A5E4?style=for-the-badge&logo=telegram)](https://t.me/biticiapp2)

## Fitur Utama

### 1. Smart Money Concepts (SMC)

![SMC](https://img.shields.io/badge/Feature-Smart%20Money%20Concepts-blue)

Implementasi lengkap konsep Smart Money untuk memahami pergerakan institusional:

- **Internal Structure Detection**: Identifikasi otomatis struktur pasar internal
- **Break of Structure (BOS)**: Deteksi perubahan struktur bullish/bearish
- **Change of Character (CHoCH)**: Pengenalan perubahan karakter pasar
- **Order Block Detection**: Visualisasi zona order block internal
  - Bullish Order Blocks (warna biru)
  - Bearish Order Blocks (warna merah)
- **Confluence Filter**: Filter tambahan untuk meningkatkan akurasi
- **Volatility-Based Filtering**: Menggunakan ATR atau Cumulative Mean Range
- **Mitigation Logic**: Pilihan High/Low atau Close untuk mitigasi order block

**Konfigurasi:**
- Show Internal Structure
- Bullish Structure: All/BOS/CHoCH
- Bearish Structure: All/BOS/CHoCH
- Internal Order Blocks dengan ukuran dapat disesuaikan (1-20)
- Warna kustomisasi untuk bull/bear

### 2. Market Structure Analysis (MSS & BOS)

![MSS-BOS](https://img.shields.io/badge/Feature-Market%20Structure-green)

Analisis struktur pasar menggunakan pivot points:

- **Market Structure Shift (MSS)**: Identifikasi perubahan struktur pasar mayor
- **Break of Structure (BOS)**: Deteksi break struktur minor
- **Pivot Strength**: Konfigurasi kekuatan pivot (default: 3)
- **Visual Indicators**: Garis dan label otomatis untuk setiap event
- **Customizable Style**: Solid, Dashed, atau Dotted line style

**Sinyal:**
- Bullish MSS: Perubahan dari bearish ke bullish
- Bearish MSS: Perubahan dari bullish ke bearish
- Bullish BOS: Break struktur dalam trend bullish
- Bearish BOS: Break struktur dalam trend bearish

### 3. Support & Resistance v2 (Dynamic SnR)

![SNR](https://img.shields.io/badge/Feature-Dynamic%20SnR-orange)

Sistem Support & Resistance dinamis dengan algoritma canggih:

- **Automatic Level Detection**: Deteksi otomatis level kunci berdasarkan pivot
- **Strength-Based Ranking**: Level diurutkan berdasarkan kekuatan (jumlah touch)
- **Dynamic Channel Width**: Lebar channel adaptif berdasarkan volatilitas
- **Distance Percentage**: Tampilan jarak dalam persentase dari harga current
- **Maximum Levels**: Kontrol jumlah level yang ditampilkan (1-10)
- **Minimum Strength Filter**: Filter level lemah (strength < threshold)

**Konfigurasi:**
- Pivot Period: 4-30 (default: 10)
- Source: High/Low atau Close/Open
- Maximum Number of Pivot: 5-100 (default: 20)
- Maximum Channel Width: 1-100% (default: 10%)
- Maximum Number of S/R: 1-10 (default: 5)
- Minimum Strength: 1-10 (default: 2)
- Line Style: Solid/Dotted/Dashed
- Custom Colors untuk Support dan Resistance

**Fitur Khusus:**
- Auto-update posisi label
- Extend lines ke kanan dan kiri
- Break detection untuk alert

### 4. Momentum Signal (RSI-Based)

![Momentum](https://img.shields.io/badge/Feature-Momentum%20Signal-red)

Sistem sinyal momentum berbasis RSI dengan filter ketat:

- **RSI Period**: Konfigurasi panjang RSI (default: 14)
- **Threshold Levels**:
  - Positive Momentum: Di atas 65
  - Negative Momentum: Di bawah 32
- **EMA Confirmation**: Filter tambahan menggunakan EMA(5)
- **Visual Highlighter**: Background fill untuk identifikasi trend
- **Momentum Labels**: Label LONG/SHORT otomatis

**Warna Kustomisasi:**
- Positive Momentum: Hijau (customizable)
- Negative Momentum: Merah (customizable)
- Background fill untuk visualisasi yang jelas

### 5. Momentum Acceleration Position

![MomAcc](https://img.shields.io/badge/Feature-Momentum%20Acceleration-purple)

Indikator momentum acceleration dengan dual source:

- **Price-Based Momentum**: Menggunakan harga close
- **Volume-Based Momentum**: Menggunakan On Balance Volume (OBV)
- **Arrow Visualization**: Panah atas/bawah untuk indikasi momentum
- **Oscillator View**: Tampilan oscillator opsional
  - Price Momentum Oscillator
  - OBV Momentum Oscillator
- **Customizable Display**:
  - Plotting Length: Berapa bar yang ditampilkan
  - Height adjustment
  - Vertical offset
  - Placement: Top atau Bottom

**Formula:**
```
v = SMA(change(source, length) / length, 3)
a = change(v, length) / length
momentum = v - a
```

### 6. No-Repaint Engine (STRICT)

![No-Repaint](https://img.shields.io/badge/Status-No%20Repaint%20Verified-success)

Sistem filter multi-layer yang benar-benar tidak repaint:

#### MTF Trend Filter
- **Multi-Timeframe Analysis**: Analisis trend di timeframe lebih tinggi
- **Default MTF**: 1H (dapat disesuaikan)
- **No Lookahead**: `lookahead=barmerge.lookahead_off`
- **No Gaps Bias**: `gaps=barmerge.gaps_off`
- **Visual Indicator**: Garis purple menunjukkan MTF trend

#### ADX Trend Strength
- **Minimum ADX**: Threshold kekuatan trend (default: 20)
- **ADX Velocity Check**: Memastikan ADX sedang naik
- **Formula**: `ADX > threshold AND ADX > ADX[1]`

#### EMA Trend Filter
- **Local EMA**: EMA 200 periode
- **Trend Confirmation**: Close vs EMA position
- **Bull Trend**: Close > EMA(200)
- **Bear Trend**: Close < EMA(200)

#### Volume Confirmation
- **Volume Check**: Volume > SMA(Volume, 20)
- **High Volume Bars**: Konfirmasi dengan volume di atas rata-rata

**Confluence Logic:**
```
LONG Signal = RSI Positive + Momentum > 0 + ADX Valid + EMA Bull + MTF Bull + Volume OK
SHORT Signal = RSI Negative + Momentum < 0 + ADX Valid + EMA Bear + MTF Bear + Volume OK
```

### 7. Trade Management System

![Trade-Management](https://img.shields.io/badge/Feature-Auto%20Trade%20Management-yellow)

Sistem manajemen trade otomatis dengan fitur lengkap:

#### Stop Loss Modes
1. **Percentage-Based SL**
   - Jarak SL dalam persentase dari entry
   - Default: 2%
   - Range: 0.1% - custom

2. **SRv2 Level (Auto)**
   - SL otomatis di level Support/Resistance terdekat
   - Long: SL di support terdekat di bawah entry
   - Short: SL di resistance terdekat di atas entry
   - Fallback ke 1% jika tidak ada level

#### Take Profit System
- **Risk:Reward Ratio**: Konfigurasi RR (default: 1:4)
- **Single Target**: Full exit di target profit
- **Auto Calculation**: TP = Entry + (Risk × RR Ratio)

#### Trailing Stop Mechanism

**Level 1 - Break Even Protection (BEP):**
```
Long: Jika price mencapai Entry + 1×Risk → SL pindah ke Entry
Short: Jika price mencapai Entry - 1×Risk → SL pindah ke Entry
```

**Level 2 - Trail Win Protection:**
```
Long: Jika price mencapai Entry + 2×Risk → SL pindah ke Entry + 1×Risk
Short: Jika price mencapai Entry - 2×Risk → SL pindah ke Entry - 1×Risk
```

**Keunggulan:**
- Proteksi profit secara otomatis
- Tidak perlu intervensi manual
- Label yang jelas: "BEP" atau "TRAIL-WIN"
- Berbasis risk, bukan persentase arbitrary

#### Auto Position Reversal
- Deteksi sinyal berlawanan
- Auto close posisi existing
- Instant entry posisi baru
- Komentar: "Reversal to Long/Short"

### 8. Dashboard Real-Time

![Dashboard](https://img.shields.io/badge/Feature-Live%20Dashboard-informational)

Dashboard informatif di kanan atas chart:

**Saat Ada Posisi Aktif:**
- **SIGNAL**: Arah trade (LONG/SHORT) dengan warna
- **ENTRY**: Harga entry
- **TARGET**: Target profit (warna hijau)
- **STOP**: Stop loss (warna merah)
- **WIN RATE**: Persentase winrate (warna kuning)
- **PROFIT**: Net profit dengan warna dinamis

**Saat Scanning:**
- Status: "SCANNING..."
- WIN RATE tetap ditampilkan
- PROFIT tetap ditampilkan

**Fitur:**
- Auto-hide saat tidak ada posisi
- Warna dinamis berdasarkan kondisi
- Format angka otomatis
- Transparent background dengan border

## Sistem Alert

![Alerts](https://img.shields.io/badge/Feature-12%20Alert%20Types-critical)

Total 12 tipe alert yang dapat dikonfigurasi:

### Support & Resistance Alerts
1. **Resistance Broken**: Harga break level resistance
2. **Support Broken**: Harga break level support

### Smart Money Concepts Alerts
3. **SMC Internal Bullish Change**: Struktur internal berubah bullish
4. **SMC Internal Bearish Change**: Struktur internal berubah bearish

### Market Structure Alerts
5. **TFO: Any MSS**: Market Structure Shift terdeteksi
6. **TFO: Any BOS**: Break of Structure terdeteksi
7. **TFO: Bull MSS**: Bullish MSS
8. **TFO: Bull BOS**: Bullish BOS
9. **TFO: Bear MSS**: Bearish MSS
10. **TFO: Bear BOS**: Bearish BOS

### Momentum Alerts
11. **RSI: Positive Trend**: Momentum RSI positif
12. **RSI: Negative Trend**: Momentum RSI negatif
13. **MomAcc: Early Warning**: Momentum cross zero
14. **MomAcc: Long Opportunity**: Momentum crossover
15. **MomAcc: Short Opportunity**: Momentum crossunder

**Cara Setup Alert:**
1. Klik kanan pada chart → "Add Alert"
2. Pilih "Strategy Trend Signal [BiticiChanel]"
3. Pilih tipe alert dari dropdown
4. Set notifikasi (App, Email, Webhook, etc.)
5. Klik "Create"

## Instalasi & Setup

### Langkah 1: Import ke TradingView

1. Buka [TradingView](https://www.tradingview.com)
2. Klik "Pine Editor" di bagian bawah chart
3. Klik "New" → "Blank indicator"
4. Hapus semua kode default
5. Copy-paste seluruh kode dari file ini
6. Klik "Save" dan beri nama "Strategy Trend Signal [BiticiChanel]"
7. Klik "Add to Chart"

### Langkah 2: Konfigurasi Awal

#### Visual & Fitur Utama
```
1. Show SMC (Internal & OB): ✓ ON
2. Show MSS & BOS: ✓ ON
3. Show Momentum Signal: ✓ ON
4. Show Momentum Position: ✓ ON
5. Show SnR: ✓ ON
```

#### Trade Management
```
Show Dashboard Table: ✓ ON
SL Mode: "Percentage" atau "SRv2 Level (Auto)"
SL Percentage: 2.0%
Target Risk:Reward: 4.0 (1:4)
```

#### No-Repaint Engine
```
Use MTF Trend Filter: ✓ ON
MTF Timeframe: "60" (1 Hour)
Use ADX (Trend Strength): ✓ ON
Min ADX Strength: 20
Use EMA Trend Filter: ✓ ON
Use Volume Check: ✓ ON
```

### Langkah 3: Optimasi per Timeframe

#### Scalping (1m - 5m)
```
- RSI Length: 7-10
- Momentum Length: 8-10
- Pivot Strength: 2-3
- MTF: 15m atau 30m
- ADX Threshold: 15-20
```

#### Day Trading (15m - 1H)
```
- RSI Length: 14 (default)
- Momentum Length: 13 (default)
- Pivot Strength: 3-5
- MTF: 1H atau 4H
- ADX Threshold: 20-25
```

#### Swing Trading (4H - 1D)
```
- RSI Length: 14-21
- Momentum Length: 13-21
- Pivot Strength: 5-7
- MTF: 1D atau 1W
- ADX Threshold: 25-30
```

## Panduan Penggunaan

### A. Identifikasi Trend dengan SMC

1. **Lihat Struktur Internal:**
   - Label "BOS" atau "CHoCH" menunjukkan perubahan struktur
   - Garis dashed menghubungkan level kunci
   - Order Blocks (kotak biru/merah) menunjukkan zona institusional

2. **Konfirmasi dengan Market Structure:**
   - "MSS" = Perubahan trend mayor
   - "BOS" = Kelanjutan trend

### B. Menunggu Sinyal Entry

1. **Sinyal LONG:**
   - Label "LONG" muncul di bawah bar
   - Background hijau (jika fitur aktif)
   - Momentum arrow naik
   - Price di atas MTF trend line (purple)

2. **Sinyal SHORT:**
   - Label "SHORT" muncul di atas bar
   - Background merah (jika fitur aktif)
   - Momentum arrow turun
   - Price di bawah MTF trend line (purple)

### C. Monitor Dashboard

Setelah entry, perhatikan:
- **ENTRY**: Harga masuk
- **TARGET**: Tujuan profit
- **STOP**: Level cut loss
- **Status trailing stop akan otomatis update**

### D. Exit Strategy

**Otomatis (Direkomendasikan):**
- Sistem akan exit di TP atau SL
- Trailing stop akan aktif otomatis di profit tertentu
- Label "BEP" atau "TRAIL-WIN" menunjukkan update SL

**Manual:**
- Close posisi jika muncul sinyal berlawanan
- Close di support/resistance kuat
- Close jika momentum berubah drastis

## Contoh Kasus Trading

### Case Study 1: Long Entry BTC/USDT (15m)

**Setup:**
- Timeframe: 15 menit
- Asset: BTC/USDT
- Modal: $1000
- SL Mode: SRv2 Auto
- RR Ratio: 1:4

**Sinyal:**
1. SMC menunjukkan "CHoCH" bullish di $42,150
2. Price break order block bearish
3. RSI cross ke atas 65
4. Momentum acceleration positif
5. Price di atas MTF EMA (1H)
6. Volume tinggi konfirmasi
7. Label "LONG" muncul di $42,200

**Eksekusi:**
- Entry: $42,200
- SL Auto: $42,000 (support terdekat)
- Risk: $200 (0.47%)
- TP: $43,000 ($200 × 4 = $800 profit potential)
- RR: 1:4

**Management:**
- Price mencapai $42,600 → SL pindah ke Entry ($42,200) = BEP
- Price mencapai $43,000 → SL pindah ke $42,800 = TRAIL-WIN
- TP Hit di $43,000 → Profit $800

**Hasil:**
- Win Rate: 1/1 = 100%
- Net Profit: $800

### Case Study 2: Short Entry ETH/USDT (1H)

**Setup:**
- Timeframe: 1 jam
- Asset: ETH/USDT
- Modal: $1000
- SL Mode: Percentage (2%)
- RR Ratio: 1:3

**Sinyal:**
1. Market Structure "MSS" bearish di $2,500
2. Order block bullish gagal hold
3. RSI drop di bawah 32
4. Momentum acceleration negatif
5. Price di bawah MTF EMA (4H)
6. Volume confirmation
7. Label "SHORT" muncul di $2,480

**Eksekusi:**
- Entry: $2,480
- SL: $2,530 (2% = $50)
- Risk: $50
- TP: $2,330 ($50 × 3 = $150 profit potential)
- RR: 1:3

**Management:**
- Price turun ke $2,430 → SL pindah ke Entry ($2,480) = BEP
- Price turun ke $2,380 → SL pindah ke $2,430 = TRAIL-WIN
- TP Hit di $2,330 → Profit $150

**Hasil:**
- Win Rate: 1/1 = 100%
- Net Profit: $150

## Optimasi Performa

### 1. Backtest Strategy

**Cara Backtest:**
1. Pilih timeframe yang sesuai
2. Pilih range date yang cukup (minimal 3-6 bulan)
3. Lihat "Strategy Tester" tab di bawah
4. Analisis metrics:
   - Net Profit
   - Win Rate
   - Profit Factor
   - Max Drawdown
   - Sharpe Ratio

**Target Metrics (Good Strategy):**
```
Net Profit: Positif konsisten
Win Rate: > 50%
Profit Factor: > 1.5
Max Drawdown: < 20%
Sharpe Ratio: > 1.0
```

### 2. Forward Testing

**Rekomendasi:**
1. Test di demo account minimal 1 bulan
2. Gunakan risk 1-2% per trade
3. Catat semua trade di journal
4. Evaluasi setiap minggu

### 3. Parameter Tuning

**Jika Win Rate Rendah (<45%):**
- Naikkan ADX threshold (20 → 25)
- Aktifkan semua filter
- Gunakan MTF lebih tinggi
- Naikkan minimum strength SnR

**Jika Terlalu Sedikit Sinyal:**
- Turunkan ADX threshold (20 → 15)
- Nonaktifkan beberapa filter
- Gunakan timeframe lebih rendah
- Turunkan RSI threshold

**Jika Drawdown Terlalu Besar:**
- Perkecil RR ratio (4 → 3)
- Gunakan SL percentage lebih kecil
- Aktifkan volume filter
- Gunakan timeframe lebih besar

## Tips & Best Practices

### Risk Management

1. **Position Sizing:**
   ```
   Risk per Trade = Account × Risk% ÷ (Entry - SL)
   
   Contoh:
   Account: $10,000
   Risk: 1%
   Entry: $100
   SL: $98
   
   Position Size = $10,000 × 1% ÷ ($100 - $98)
                 = $100 ÷ $2
                 = 50 units
   ```

2. **Diversifikasi:**
   - Maksimal 2-3 posisi bersamaan
   - Jangan all-in satu asset
   - Spread risk di multiple pairs

3. **Max Daily Loss:**
   - Set limit maksimal loss per hari (contoh: 3%)
   - Jika tercapai, stop trading hari itu

### Psikologi Trading

1. **Disiplin Mengikuti Sinyal:**
   - Jangan FOMO entry tanpa sinyal
   - Jangan exit sebelum TP/SL
   - Trust the system

2. **Hindari Revenge Trading:**
   - Loss itu normal
   - Jangan double risk setelah loss
   - Stick to plan

3. **Journal Trading:**
   - Catat setiap trade
   - Screenshot setup
   - Review mingguan

### Monitoring & Maintenance

1. **Daily Checklist:**
   - Cek market condition (trending/ranging)
   - Cek high impact news
   - Monitor posisi aktif
   - Update stop loss jika perlu

2. **Weekly Review:**
   - Hitung win rate
   - Analisis losing trades
   - Adjustment parameter jika perlu

3. **Monthly Evaluation:**
   - Total profit/loss
   - Bandingkan dengan target
   - Strategy adjustment

## Troubleshooting

### Masalah Umum

#### 1. Sinyal Tidak Muncul

**Penyebab:**
- Filter terlalu ketat
- Kondisi market ranging
- Timeframe tidak sesuai

**Solusi:**
- Cek apakah semua filter aktif
- Turunkan threshold ADX
- Coba timeframe berbeda
- Lihat apakah ada error di console

#### 2. Terlalu Banyak False Signal

**Penyebab:**
- Filter terlalu longgar
- Market kondisi choppy
- Parameter tidak optimal

**Solusi:**
- Aktifkan semua filter
- Naikkan ADX threshold
- Gunakan MTF lebih tinggi
- Tambah confluence minimal

#### 3. Dashboard Tidak Muncul

**Penyebab:**
- "Show Dashboard Table" = OFF
- Belum ada posisi aktif

**Solusi:**
- Aktifkan di settings
- Entry posisi untuk test

#### 4. Order Block Tidak Terlihat

**Penyebab:**
- "Show Internal Order Blocks" = OFF
- OB Size terlalu kecil
- Sudah terhapus (mitigated)

**Solusi:**
- Aktifkan di SMC settings
- Naikkan OB Size (5-10)
- Zoom out untuk lihat history

#### 5. Alert Tidak Berbunyi

**Penyebab:**
- Alert belum di-setup
- Notifikasi off di device

**Solusi:**
- Setup alert manual (lihat bagian Alert)
- Cek settings notifikasi TradingView
- Test alert dengan event yang sering

## FAQ (Frequently Asked Questions)

### Umum

**Q: Apakah strategi ini profitable?**
A: Tidak ada strategi yang 100% profitable. Profitability tergantung pada:
- Market condition
- Parameter settings
- Risk management
- Trading discipline
Selalu backtest dan forward test dulu.

**Q: Timeframe mana yang paling bagus?**
A: Tergantung trading style:
- Scalper: 1m-5m (butuh fokus tinggi)
- Day Trader: 15m-1H (balance)
- Swing Trader: 4H-1D (santai)
Rekomendasi pemula: 15m atau 1H.

**Q: Berapa modal minimal?**
A: Minimal $100-$500 untuk belajar. Untuk live trading serius, minimal $1000-$5000 agar position sizing lebih fleksibel.

**Q: Apakah bisa untuk Forex/Stocks/Crypto?**
A: Ya, bisa untuk semua asset. Namun perlu adjustment parameter karena karakteristik volatilitas berbeda.

### Teknis

**Q: Apa itu "No-Repaint"?**
A: Sinyal tidak berubah setelah bar close. Apa yang terlihat saat bar close = final signal. Ini penting agar backtest = real trading.

**Q: Kenapa harus pakai MTF filter?**
A: MTF (Multi-Timeframe) membantu konfirmasi trend besar, sehingga tidak melawan arus utama. Ini mengurangi false signal.

**Q: Apa bedanya BOS dan MSS?**
A:
- BOS (Break of Structure): Break dalam trend yang sama (continuation)
- MSS (Market Structure Shift): Perubahan trend (reversal)

**Q: Kapan Order Block dihapus?**
A: Order Block dihapus saat price mitigasi (touch) level tersebut:
- Bearish OB: Saat high/close menyentuh OB top
- Bullish OB: Saat low/close menyentuh OB bottom

**Q: Apa itu Confluence Signal?**
A: Sinyal yang memenuhi SEMUA filter:
- RSI momentum
- Momentum acceleration
- ADX strength
- EMA trend
- MTF trend
- Volume confirmation

### Trading

**Q: Bolehkah entry tanpa semua filter?**
A: Tidak direkomendasikan. Filter dibuat untuk proteksi. Entry tanpa filter = risk tinggi.

**Q: Bagaimana jika SL terlalu jauh?**
A: 
- Gunakan "Percentage" mode
- Adjust percentage lebih kecil (1-1.5%)
- Skip trade jika risk terlalu besar

**Q: Apakah trailing stop bisa dimatikan?**
A: Trailing stop built-in di strategy, tidak bisa dimatikan. Ini fitur proteksi profit otomatis.

**Q: Bolehkah close profit sebelum TP?**
A: Boleh, tapi tidak optimal. Sistem sudah di-design dengan RR ratio yang profitable. Trust the system.

**Q: Bagaimana handle weekend/gap?**
A: 
- Crypto: 24/7, tidak ada gap
- Forex: Hindari entry Jumat sore, gap Senin
- Stocks: Hindari entry sebelum close, gap morning

## Lisensi & Hak Cipta

### Mozilla Public License 2.0

Strategi ini dilisensikan di bawah **Mozilla Public License 2.0**.

**Anda Diperbolehkan:**
- Menggunakan untuk tujuan komersial
- Modifikasi kode
- Distribusi
- Sublicense

**Dengan Syarat:**
- Mencantumkan lisensi asli
- Menyatakan perubahan yang dibuat
- Sumber kode modifikasi harus tersedia

**Lihat lisensi lengkap:** [Mozilla MPL 2.0](https://mozilla.org/MPL/2.0/)

### Copyright

```
© 2024 BiticiChanel
All Rights Reserved
```

**Original Author:** BiticiChanel  
**Code Maintainer:** MeViksry  
**Version:** 5.0  
**Last Update:** 2024

## Changelog

### Version 5.0 (Current)
- Implementasi No-Repaint Engine yang ketat
- Penambahan MTF Trend Filter anti-repaint
- ADX Velocity Check untuk konfirmasi trend
- Perbaikan Trailing Stop Logic (BEP & Trail-Win)
- Dashboard Real-Time dengan win rate akurat
- Support 15 tipe alert
- Auto Position Reversal
- Optimasi performa dan visualisasi

### Version 4.0
- Penambahan Smart Money Concepts (SMC)
- Market Structure Analysis (MSS & BOS)
- Dynamic Support & Resistance v2
- Momentum Acceleration Indicator

### Version 3.0
- Basic RSI Signal System
- Simple Trade Management
- Visual indicators

## Contributing

Kontribusi sangat diterima! Jika Anda ingin berkontribusi:

1. Fork repository ini
2. Buat branch fitur (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buka Pull Request

**Area yang Bisa Dikembangkan:**
- Machine Learning integration
- Additional filters
- More alert types
- Mobile optimization
- Multi-asset optimization
- Backtesting improvements

## Support & Komunitas

### Butuh Bantuan?

1. **GitHub Issues:**  
   [Report Bug atau Request Feature](https://github.com/MeViksry/Strategy-Trend-Signal-BiticiChanel/issues)

2. **Telegram Community:**  
   Join untuk diskusi, sharing hasil, dan update:  
   [https://t.me/biticiapp2](https://t.me/biticiapp2)

3. **Email:**  
   Untuk pertanyaan bisnis atau kolaborasi