# Husky-Care
All-in-one web app and maintenance companion for SYM Husky 150 owners. Features monthly autosaving service logs, OBD-II DTC scanner terminal, battery diagnostics, TFT meter guide, and curated DIY upgrade tutorials.
# 🛵 SYM Husky 150 Companion Web App

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Web%20%7C%20Mobile--Responsive-blue.svg)](#)
[![Built with TailwindCSS](https://img.shields.io/badge/UI-Tailwind%20CSS-38B2AC.svg)](https://tailwindcss.com/)

Aplikasi web setempat (*one-stop companion app*) yang direka khas untuk pemilik dan komuniti skuter **SYM Husky 150**. Menggabungkan jadual selenggara digital berserta fungsi simpanan automatik (*autosave*), pangkalan data kod diagnostik OBD-II, konsol ELM327, panduan panel meter TFT, serta katalog panduan DIY penjimatan kos.

---

## 🌟 Ciri-Ciri Utama (Key Features)

### 1. 📋 Repair & Maintenance Sheet (Autosave Mengikut Bulan & Tahun)
* **Log Rekod Servis Berkala:** Menyimpan rekod jarak perbatuan (*mileage*), tarikh, butiran komponen, keterangan kerosakan, dan tandatangan mekanik[span_0](start_span)[span_0](end_span).
* **Simpanan Tempatan Automatik (*Autosave*):** Disimpan terus ke `localStorage` pelayar mengikut tetapan bulan dan tahun (`YYYY-MM`) tanpa risiko kehilangan data.
* **Jadual Servis Berkala Rasmi:** Paparan matriks selenggara lengkap 300 km hingga 12,000 km berasaskan manual kilang berserta kod status (I, C, R, L).

### 2. 🔋 Diagnostik Bateri & Sistem Fius
* **Panduan Voltan Masa Nyata:** Status bacaan voltan rehat (12.6V–12.8V), mod siap siaga sistem *Keyless* (12.2V–12.4V), amaran bateri lemah, dan paras voltan pengecasan normal semasa menunggang (13.8V–14.8V).
* **Tips Motosikal Terbiar:** Prosedur perlindungan bateri YTZ10S untuk tempoh 3 hari, 7 hari (cabut terminal negatif), dan 30 hari (tangki penuh & *center stand*).
* **Kaedah Jumper & Cas DIY:** 3 tatacara *jump start* selamat (Powerbank 12V, motosikal lain, dan bateri kereta) serta langkah pengecasan pintar di rumah.

### 3. ⏱️ Panduan Panel Meter TFT & Kokpit
* **Kawalan Butang "M" & "S":** Tatacara menukar unit kelajuan (KM/H $\leftrightarrow$ MP/H) dan tetapan jam digital.
* **Pengurusan Jarak (Mileage):** Cara *reset* Single Mileage (Trip) dan Oil Mileage (penunjuk servis minyak enjin).
* **Kawalan Traksi (TCS):** Panduan menghidupkan atau mematikan sistem TCS pada kelajuan bawah 5 km/j.

### 4. 💻 Pangkalan Data Kod OBD-II & Simulator ELM327
* **Buletin Teknikal Rasmi (IB: 419):** Senarai lengkap kod ralat P-Codes (Euro 4 / Euro 5) meliputi sistem pendikit (TPS), penderia O2, suhu cecair penyejuk (ECT), dan suis keselamatan tongkat sisi.
* **Carian Pantas (Live Filter):** Cari kod DTC atau nama komponen dengan serta-merta.
* **Konsol Diagnostik ELM327:** Simulator pembacaan data ECU secara langsung (*Live RPM, Coolant Temp, Voltan, MIL status*) serta integrasi pautan ke perisian **Car Scanner ELM OBD2**.

### 5. 🛠️ 10 Masalah Biasa (Common Issues & Fixes)
* Panduan mengatasi isu sensor O2 basah ketika hujan lebat, *throttle body* kotor, lampu amaran TCS berkelip, gegaran *CVT judder*, bunyi dengung pam petrol, dan starter relay melekat.

### 6. 💰 Kos Selenggara & Panduan Jimat Upah (DIY)
* **Anggaran Kos Rutin:** Kos pasaran alat ganti seperti minyak enjin 10W-30, minyak transmisi 85W-140, bateri YTZ10S, dan tali sawat CVT.
* **Panduan DIY Mengikut Tahap:** Panduan bergambar/langkah demi langkah bagi pemasangan filem tinted, penapis udara, *monorack*, *crash bar*, dan pendawaian lampu sorot (Spotlight) menggunakan geganti 4-pin (Relay) berserta anggaran penjimatan upah sehingga **RM165 – RM335+**.

### 7. 🛒 Katalog Aksesori & Naik Taraf
* Senarai aksesori khusus SYM Husky 150 dibahagikan mengikut kategori (Perlindungan, Utiliti, Prestasi, Pencahayaan, dan Kosmetik) lengkap dengan pautan terus ke Shopee dan video rujukan TikTok.

---

## 🛠️ Spesifikasi Pantas SYM Husky 150

| Parameter | Spesifikasi Disyorkan |
| :--- | :--- |
| **Bahan Api** | Petrol tanpa plumbum RON95 ke atas (Oktana 90+) |
| **Minyak Enjin** | SL/CF SAE 10W-30 (1.05L total / 1.0L servis biasa) |
| **Minyak Gearbox** | SAE 85W-140 (100cc / 100ml) |
| **Model Bateri** | YTZ10S (Gel / Maintenance-Free) |
| **Konfigurasi Fius** | 25A + (20A × 2) + (15A × 3) |
| **Kapasiti Tangki** | 15 Liter |

---

## 🚀 Pemasangan & Penggunaan (Getting Started)

Aplikasi ini dibina sebagai aplikasi web satu halaman (*Single Page Application*) tanpa memerlukan pemasangan pelayan (*server-less*).

### Menjalankan Secara Tempatan (Local):
1. Klon repositori ini ke komputer anda:
   ```bash
   git clone [https://github.com/kimsoju81/sym-husky-care.git](https://github.com/kimsoju81/sym-husky-care.git)
