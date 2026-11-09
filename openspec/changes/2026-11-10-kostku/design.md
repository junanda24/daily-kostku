# KOSTKU! — Design

## Stack
- Web artifact static (single-file app): `index.html` + `styles.css` + `app.js` (pola ARCHITECTURE.md §1: satu objek `state`, data terpisah, fungsi `render()` murni, event handler tipis, satu modul `store` untuk localStorage, IIFE scope).
- Tanpa framework, tanpa backend, tanpa dependency runtime. Font: Plus Jakarta Sans (Google Fonts) — workhorse UI face, mode Operate.
- Mobile-first, max-width 480px (app shell ala aplikasi HP), desktop: konten terpusat dengan latar gelap.

## Arsitektur state (lima keranjang)
1. **Lokal**: tab aktif, modal tambah/edit kamar, toast, bulan yang dipilih (UI state).
2. **URL**: tidak dipakai (bukan state shareable).
3. **Server state**: tidak ada (tanpa backend).
4. **Global client**: data kost (kamar, penghuni, pembayaran, pengeluaran) — satu `store` module di atas localStorage, key `kostku-v1`.
5. **Form**: form tambah kamar/penghuni/pengeluaran — state lokal per form, validasi saat submit (nama wajib, harga > 0, nomor WA angka).

## Visual world — "Buku Kas Hijau" (mode Operate)
- **Thesis**: buku kas kost yang serius tapi hangat — juragan kost membuka app dan dalam 3 detik tahu siapa yang belum bayar.
- **Palette (committed green)**: hijau tua `#14532d` (header, aksi primer), hijau uang `#15803d` (lunas/positif), kertas `#fafaf7` (ground), tinta `#1c1917`, amber `#b45309` (jatuh tempo), merah `#b91c1c` (terlambat), abu `#78716c` (sekunder). Tanpa gradient dekoratif.
- **Type**: Plus Jakarta Sans; angka rupiah tabular (`font-variant-numeric: tabular-nums`); heading 700–800, body 400–500.
- **Komponen khas**: kartu kamar seperti plat nomor pintu (nomor besar + status badge); cap stempel "LUNAS" (border ganda, rotate −8°, animasi scale-in); ring progres kamar lunas; grafik batang 6 bulan dari CSS.
- **Delight**: stempel LUNAS animasi, confetti canvas saat 100% lunas, count-up angka dashboard, toast bawah layar.
- **Motion**: satu momen authored — stempel + confetti; sisanya transisi 150–200ms ease-out. Konten terlihat default (tanpa entrance-hidden).

## Struktur file (repo)
```
2026-11-10-kostku/
  README.md
  .gitignore
  src/
    index.html
    styles.css
    app.js
  openspec/changes/2026-11-10-kostku/ (proposal, specs, design, tasks)
  openspec/changes/archive/2026-11-10-kostku/ (setelah selesai)
```

## Deploy target
Artifact static (link Muse). TIDAK deploy Vercel tanpa ACC Junan. TIDAK publish registry (bukan package).
