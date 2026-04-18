# SETUP GUIDE — mazayastudio GitHub Profile

## Struktur File

```
mazayastudio/              ← repo (nama = username GitHub kamu)
├── README.md
├── assets/
│   └── svg/
│       ├── header.svg     ← glitch title animation
│       ├── ticker.svg     ← scrolling tech stack
│       ├── skills.svg     ← animated skill bars
│       ├── stats.svg      ← stats cards
│       └── snake-dark.svg ← di-generate otomatis oleh Actions
└── .github/
    └── workflows/
        └── update-profile.yml
```

## Langkah Setup

### 1. Upload semua file ke repo

Pastikan repo `mazayastudio/mazayastudio` sudah ada.
Upload semua file dengan struktur folder persis seperti di atas.
Commit ke branch `main` atau `master`.

### 2. Aktifkan GitHub Actions

Buka repo → tab **Actions** → klik **"I understand my workflows, go ahead and enable them"**

### 3. Jalankan workflow pertama kali

Di tab Actions → pilih **"Update Profile Assets"** → klik **"Run workflow"**

Ini akan generate file `snake-dark.svg` secara otomatis.
Setelah selesai (~1-2 menit), snake animation akan muncul di README.

### 4. Verifikasi

Buka `github.com/mazayastudio` — semua animasi seharusnya sudah jalan:
- Glitch title + cursor blink di header
- Ticker marquee berjalan
- Skill bars animate on load
- Stats cards dengan pulsing dot
- Snake animation ter-update setiap hari jam 00:00 UTC

## Troubleshooting

**SVG tidak muncul?**
Pastikan path di README menggunakan `./assets/svg/namafile.svg`
bukan URL absolut. GitHub akan serve file dari repo langsung.

**Snake tidak muncul?**
File `snake-dark.svg` belum ada sebelum Actions pertama dijalankan.
Jalankan workflow manual dulu dari tab Actions.

**Animasi tidak jalan?**
GitHub me-render SVG secara aman — CSS animation di SVG biasanya jalan.
Tapi `@import` Google Fonts di SVG mungkin di-block oleh GitHub CSP.
Font akan fallback ke `monospace`/`sans-serif` — layout tetap sama.
