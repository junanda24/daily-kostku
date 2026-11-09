# KOSTKU! — Juragan Kost

Aplikasi manajemen kos-kosan untuk pemilik kost: kelola kamar dan penghuni, lacak pembayaran bulanan, catat pengeluaran operasional, dan kirim pengingat tagihan via WhatsApp. Semua data tersimpan di browser (localStorage) — tanpa login, tanpa backend, tanpa instalasi.

> Dibuat 2026-11-10 dalam program "1 Hari 1 Project".
> Buka di: artifact `kostku-juragan-kost` (link dibagikan lewat chat/WA)

## Kenapa ide ini dipilih

Di Indonesia ada jutaan pemilik kost — dari yang punya 5 kamar sampai 50 kamar — dan hampir semuanya masih nagih pakai buku tulis atau ingatan. Aplikasi yang ada (Mamikos dkk.) dibuat untuk **pencari** kost, bukan pemiliknya; yang untuk pemilik biasanya SaaS berbayar dan ribet. KOSTKU! membalik sudut pandang: ini alat untuk **juragan kost**.

Efek kejutnya ada di detail kecil: tombol **Tandai Lunas** memberi cap stempel LUNAS animasi di kartu kamar, dan kalau semua kamar lunas, confetti meledak. Pengingat WhatsApp-nya sudah dituliskan sopan dengan angka yang benar — tinggal salin atau buka WhatsApp. Itu fitur yang langsung terasa "kok kepikiran sih".

## Fitur

- **Dashboard bulan berjalan** — pemasukan bulan ini (count-up), ring progres "X dari Y kamar lunas", 4 kartu stat (Kamar Terisi, Kamar Kosong, Tunggakan, Pemasukan Bersih), grafik batang pemasukan 6 bulan terakhir.
- **Navigasi bulan** — tombol ‹ › untuk melihat bulan lain; semua angka, status kamar, dan grafik ikut berubah.
- **Manajemen kamar** — tambah/edit/hapus kamar (nomor, harga/bulan, fasilitas: AC, WiFi, kamar mandi dalam, kasur, lemari, kipas, TV; tanggal jatuh tempo 1–28). Isi kamar dengan penghuni (nama + nomor WhatsApp) atau kosongkan.
- **Pembayaran** — status per kamar per bulan: Lunas / Menunggu / Jatuh tempo hari ini / Terlambat N hari. Tandai lunas dengan metode (Tunai/Transfer/QRIS), batalkan pelunasan, riwayat pembayaran lengkap dengan filter bulan.
- **Pengeluaran operasional** — catat Listrik/Air/WiFi/Perbaikan/Lainnya; total pengeluaran mengurangi pemasukan kotor jadi pemasukan bersih.
- **Pengingat WhatsApp** — pesan tagihan otomatis per penghuni yang belum lunas (nama, kamar, jumlah, jatuh tempo), tombol Salin Pesan dan Buka WhatsApp (`wa.me`).
- **Data contoh realistis** — "Kost Mawar", Batam, 10 kamar, harga Rp 600.000–1.600.000 (berdasarkan riset harga kost Batam 2026 di Mamikos/Infokost), lengkap dengan riwayat pembayaran Juli–Oktober 2026 dan pengeluaran November. Berlabel "Data contoh" dan bisa diganti lewat "Mulai dari nol" / "Muat data contoh".
- **Persistensi** — semua perubahan tersimpan otomatis di localStorage dan bertahan setelah reload.

## Cara pakai

1. Buka link artifact di HP.
2. Saat pertama dibuka, data contoh Kost Mawar sudah terisi — langsung bisa dicoba: tandai Kamar 03 lunas, salin pesan tagihan untuk Kamar 04, tambah pengeluaran.
3. Untuk memakai dengan kost sendiri: buka Pengaturan Data → "Mulai dari nol", lalu tambah kamar dan penghuni satu per satu.
4. Tiap awal bulan: pindah ke bulan berjalan, tagih yang belum bayar lewat tab Pengingat, tandai lunas begitu uang masuk.

## Cara menjalankan dari source

File `src/index.html` adalah aplikasi lengkap dalam satu file (HTML + CSS + JS, tanpa build step, tanpa dependency):

```bash
# cara 1: buka langsung
open src/index.html

# cara 2: server statis apa pun, contoh:
npx serve src
# atau
python3 -m http.server --directory src 8000
```

Lalu buka `http://localhost:8000` di browser. Data tersimpan per browser (localStorage key `kostku-v1`).

## Tech stack

- HTML + CSS + JavaScript murni (tanpa framework, tanpa dependency runtime)
- Font: Plus Jakarta Sans (Google Fonts, dengan fallback sistem)
- Penyimpanan: localStorage (satu modul `store`)
- Ikon: inline SVG (tanpa emoji di label, sesuai preferensi produk)

## Struktur folder

```
2026-11-10-kostku/
  README.md
  PRODUCT.md            # konteks produk (impeccable)
  DESIGN.md             # dunia visual "Buku Kas Hijau"
  src/
    index.html          # aplikasi lengkap (export artifact)
  openspec/changes/2026-11-10-kostku/
    proposal.md
    specs/kostku/spec.md
    design.md
    tasks.md
  openspec/changes/archive/2026-11-10-kostku/   # arsip setelah selesai
```

## Catatan / temuan saat build

- **Tunggakan = semua kamar terisi yang belum lunas** di bulan berjalan, termasuk yang jatuh temponya masih di depan ("Menunggu"). Jadi di data contoh November: Rp 3.350.000 (Kamar 03, 04, 06, 07). Ini sesuai spec R1.
- **Status memakai tanggal perangkat.** Audit builder berjalan saat jam browser masih 9 Nov, jadi badge terbaca "Terlambat 6/8 hari" dan Kamar 03 "Menunggu"; di perangkat pengguna (10 Nov 2026) statusnya persis seperti brief: Kamar 03 "Jatuh tempo hari ini", Kamar 04 "Terlambat 7 hari", Kamar 06 "Terlambat 9 hari".
- **Nomor WhatsApp data contoh fiktif** (628111111101 dst, berpola) — ganti dengan nomor asli penghuni sebelum dipakai menagih.
- **Tidak dibuat (sengaja):** sinkronisasi antar perangkat dan multi-pengguna — butuh backend dan login; di luar kebutuhan pemilik kost satu HP. Kalau nanti dibutuhkan, ini kandidat upgrade ke fullstack.
- **Tidak di-deploy ke Vercel** — keputusan deploy ada di Junan.
