# Aplikasi Penjagaan SYM Husky — SYM Husky Care App

Aplikasi web progresif (**PWA**) yang dibangunkan khusus untuk pemilik skuter kembara **SYM Husky ADV 150 (Euro 4 / Euro 5)** di Malaysia. Aplikasi ini menyediakan log penyelenggaraan berkala automatik, panduan teknikal bateri & kotak fius, rujukan panel meter TFT, kamus kod kerosakan **OBD-II ELM327**, pengira beban elektrik aksesori, panduan penyelesaian masalah lazim, kalkulator kos servis, dan senarai semak konvoi komuniti.

---

## Ciri Utama (8 Modul)

1. **Jadual Selenggara (`jadual`)**
   - *Repair & Maintenance Record Sheet* dengan fungsi *autosave* mengikut bulan & tahun (`localStorage`).
   - Paparan gabungan semua rekod sejarah servis dari awal hingga terkini.
   - Eksport rekod ke **CSV**, **Word (`.docx`)**, dan **Pratonton Cetak / PDF** A4.
   - Jadual servis berkala rasmi SYM Husky (300 KM, 1,000 KM, 3,000 KM, 6,000 KM, 12,000 KM) dengan penapis kod (`I`, `C`, `R`, `L`).

2. **Bateri & Kotak Fius (`bateri`)**
   - Simulasi bacaan voltan rehat (*resting*) dan pengecasan (*charging*) bateri **YTZ10S**.
   - Rajah interaktif susunan fius dan spesifikasi ampere setiap litar.

3. **Panel Meter (`meter`)**
   - Panduan interaktif ikon amaran panel meter TFT dan fungsi butang `M` / `S` (jam, tripmeter, penunjuk servis minyak enjin).

4. **Kod OBD-II & Konsol ELM327 (`obd`)**
   - Pangkalan data kod ralat ECU Euro 4 / Euro 5 dan kod kelipan SYM (*Flash Codes*).
   - Simulator konsol **ELM327** serta sokongan kebenaran **Web Bluetooth** dan **Geolocation (GPS)** untuk sambungan pengimbas OBD-II.

5. **Aksesori & Beban Watt (`aksesori`)**
   - Katalog naik taraf aksesori popular dan kalkulator beban watt untuk lampu *spotlight*, pengecas USB, dan TPMS.

6. **Masalah Biasa (`masalah`)**
   - Senarai isu lazim pemilik SYM Husky beserta punca dan langkah penyelesaian pantas.

7. **Kos Selenggara (`kos`)**
   - Kalkulator anggaran kos alat ganti & upah mengikut jarak perbatuan (*1k, 5k, 6k, 12k*) dengan butang pindah terus ke rekod penyelenggaraan.

8. **Grup Husky (`grup`)**
   - Senarai semak pemeriksaan pra-tunggangan (*pre-ride checklist*) dan perkongsian jemputan komuniti.

---

## Keupayaan PWA & Spesifikasi `manifest.json`

Aplikasi ini dilengkapi sokongan penuh piawaian **Progressive Web App (PWA)** moden melalui `public/manifest.json`, `public/sw.js`, dan `src/utils/pwa.ts`:

| Ahli Manifest / API | Fungsi & Pelaksanaan dalam Aplikasi |
| :--- | :--- |
| **`screenshots`** | Tangkapan skrin `wide` (`1280x720`) dan `narrow` (`720x1280`) untuk paparan pemasangan *Rich Install UI*. |
| **`scope_extensions`** | Membenarkan domain aplikasi tambahan kekal dalam skop PWA (`type: "origin"`) dengan fail pengesahan `public/.well-known/web-app-origin-association`. |
| **`related_applications`** | Memautkan aplikasi pendamping **Car Scanner ELM OBD2** di Google Play Store dan Apple App Store (`prefer_related_applications: false`). |
| **`iarc_rating_id`** | ID penarafan umur rasmi International Age Rating Coalition (`e84b072d-71b3-4d3e-86ae-31a8ce4e53b7`). |
| **`file_handlers`** | Membolehkan fail rekod `.csv` dan `.json` dibuka terus ke modul Jadual Selenggara melalui `window.launchQueue`. |
| **`launch_handler`** | Menggunakan `client_mode: ["focus-existing", "auto"]` untuk memfokuskan tetingkap sedia ada tanpa membuka salinan pendua. |
| **`protocol_handlers`** | Mendaftarkan skema protokol tersuai `web+symhusky://` (contoh: `web+symhusky://obd/P0130`) untuk navigasi terus ke modul atau kod ralat. |
| **`share_target`** | Menerima teks, tajuk, atau pautan yang dikongsi dari aplikasi lain terus ke log penyelenggaraan (`/?tab=jadual&action=share`). |
| **`widgets`** | Menyokong **Windows Adaptive Card Widget** (`public/widgets/husky-widget-template.json` & `husky-widget-data.json`) berserta kitaran hayat `widgetinstall`, `widgetresume`, dan `widgetclick` dalam Service Worker. |
| **`edge_side_panel`** | Menyokong paparan bar sisi Microsoft Edge dengan lebar pilihan `420px`. |
| **`display_override` (`tabbed`)** | Menyokong mod paparan berbilang tab (`tabbed`, `window-controls-overlay`, `standalone`, `minimal-ui`) bersama konfigurasi `tab_strip`. |
| **`note_taking`** | Membolehkan sistem operasi melancarkan penciptaan catatan servis baharu secara terus melalui `/?tab=jadual&action=new-note`. |
| **Background Sync API** | Mendaftarkan tag `sym-husky-sync-records` setiap kali rekod atau profil disimpan supaya penyegerakan diselesaikan apabila sambungan internet kembali stabil. |
| **Periodic Background Sync API** | Mendaftarkan tag `sym-husky-periodic-check` (selang 24 jam) bagi mengemas kini data widget dan semakan berkala di latar belakang. |
| **Web Push Notifications API** | Mengendalikan acara `push` dan `notificationclick` dalam `public/sw.js` untuk memaparkan peringatan servis berkala dan membuka terus modul berkaitan. |

---

## Struktur Direktori Utama

```text
├── public/
│   ├── .well-known/
│   │   └── web-app-origin-association   # Pengesahan asal bagi scope_extensions
│   ├── screenshots/                     # Tangkapan skrin wide, narrow & widget
│   ├── widgets/                         # Templat & data Adaptive Card Windows
│   ├── manifest.json                    # Konfigurasi lengkap PWA Manifest
│   ├── sw.js                            # Service Worker (Cache, Sync, Push, Widgets)
│   ├── pwa-192x192.png                  # Ikon PWA 192x192
│   ├── pwa-512x512.png                  # Ikon PWA 512x512
│   ├── pwa-maskable-512x512.png         # Ikon boleh topeng (maskable) dengan zon selamat
│   └── apple-touch-icon.png             # Ikon iOS Safari 180x180
├── src/
│   ├── components/
│   │   ├── OfflineIndicator.tsx         # Penunjuk status luar talian
│   │   ├── PWAInstallButton.tsx         # Butang pasang PWA & panduan iOS
│   │   └── RecordPrintPreviewModal.tsx  # Pratonton cetakan A4 & eksport
│   ├── data/
│   │   └── huskyData.ts                 # Data jadual, kod OBD, fius & kos
│   ├── hooks/
│   │   ├── useOnlineStatus.ts           # Pengesan status rangkaian
│   │   └── usePWAInstall.ts             # Pengendali acara beforeinstallprompt
│   ├── modules/                         # 8 komponen modul utama aplikasi
│   ├── utils/
│   │   ├── pwa.ts                       # Utiliti SW, Background Sync, Periodic Sync & Push
│   │   └── recordExport.ts              # Penjana dokumen Word (.docx)
│   ├── App.tsx                          # Pengurusan keadaan & pengendali laluan PWA
│   └── main.tsx                         # Titik masuk aplikasi & pendaftaran SW
├── index.html                           # Meta tag PWA, iOS & manifest link
└── package.json                         # Skrip pembangunan & binaan Vite
```

---

## Pemasangan & Pembangunan Setempat

### Prasyarat
- **Node.js** versi 20+ (atau Bun)

### Langkah Menjalankan Aplikasi

1. **Pasang kebergantungan:**
   ```bash
   npm install
   ```

2. **Mulakan pelayan pembangunan (port 3000):**
   ```bash
   npm run dev
   ```

3. **Semak ralat TypeScript:**
   ```bash
   npm run lint
   ```

4. **Bina versi produksi:**
   ```bash
   npm run build
   ```

5. **Pratonton binaan produksi:**
   ```bash
   npm run preview
   ```

---

## Lesen

Projek ini diedarkan di bawah lesen **Apache-2.0**.
