# KOSTKU! — Spec

## Requirements

### R1 — Dashboard bulan berjalan
- **SHALL**: App menampilkan ringkasan bulan yang dipilih: jumlah kamar terisi, kamar kosong, total pemasukan (pembayaran lunas bulan itu), total tunggakan (kamar terisi yang belum lunas), dan pemasukan bersih (pemasukan − pengeluaran bulan itu).
- **WHEN** pengguna membuka app **THEN** bulan default adalah bulan kalender berjalan (November 2026) dan semua angka dihitung dari data bulan itu.
- **WHEN** pengguna pindah bulan (tombol ‹ ›) **THEN** semua angka, status kamar, dan grafik ikut berubah ke bulan tersebut.

### R2 — Manajemen kamar
- **SHALL**: Pengguna dapat menambah kamar (nomor, harga/bulan, fasilitas: AC / WiFi / kamar mandi dalam / kasur / lemari, tanggal jatuh tempo bulanan 1–28).
- **SHALL**: Pengguna dapat mengisi kamar dengan penghuni (nama, nomor WhatsApp) atau mengosongkannya (penghuni lama masuk arsip riwayat, bukan terhapus).
- **SHALL**: Pengguna dapat mengedit harga/fasilitas kamar dan menghapus kamar kosong.
- **WHEN** kamar kosong **THEN** kartu menampilkan status "Kosong" dan tidak masuk hitungan tunggakan.

### R3 — Pembayaran & status
- **SHALL**: Setiap kamar terisi punya status di bulan berjalan: `lunas`, `menunggu` (jatuh tempo belum lewat), `jatuh tempo hari ini`, `terlambat N hari`.
- **SHALL**: Pengguna dapat menandai kamar lunas (dengan tanggal bayar = hari ini, metode: Tunai/Transfer/QRIS) dan membatalkan pelunasan.
- **WHEN** kamar ditandai lunas **THEN** kartu kamar mendapat cap stempel "LUNAS" animasi dan riwayat pembayaran bertambah satu baris.
- **WHEN** semua kamar terisi lunas di bulan berjalan **THEN** confetti muncul sekali dan toast "Semua kamar sudah lunas bulan ini".

### R4 — Riwayat pembayaran
- **SHALL**: Tab Pembayaran menampilkan daftar pembayaran (bulan, kamar, penghuni, jumlah, tanggal bayar, metode), bisa difilter per bulan.
- **SHALL**: Grafik batang menampilkan pemasukan 6 bulan terakhir (termasuk bulan berjalan).

### R5 — Pengeluaran operasional
- **SHALL**: Pengguna dapat mencatat pengeluaran (tanggal, kategori: Listrik/Air/WiFi/Perbaikan/Lainnya, keterangan, jumlah) dan menghapusnya.
- **SHALL**: Total pengeluaran bulan berjalan mengurangi pemasukan kotor menjadi pemasukan bersih di dashboard.

### R6 — Pengingat WhatsApp
- **SHALL**: Tab Pengingat menampilkan penghuni yang belum lunas di bulan berjalan, masing-masing dengan pesan tagihan yang sudah ditulis (nama, kamar, jumlah, jatuh tempo, sapaan sopan).
- **SHALL**: Setiap pesan punya tombol "Salin Pesan" dan "Buka WhatsApp" (link `wa.me/<nomor>?text=<pesan>`).
- **WHEN** tidak ada yang menunggak **THEN** tab menampilkan empty state "Semua sudah lunas" (bukan daftar kosong tanpa penjelasan).

### R7 — Persistensi & data contoh
- **SHALL**: Semua data (kamar, penghuni, pembayaran, pengeluaran, nama kost) tersimpan di localStorage dan bertahan setelah reload.
- **SHALL**: Saat pertama dibuka, app memuat data contoh "Kost Mawar" (Batam, 10 kamar, harga Rp 600.000–1.600.000) beserta riwayat pembayaran Jul–Okt 2026.
- **SHALL**: Pengguna dapat mengosongkan semua data ("Mulai dari nol") dan memuat ulang data contoh.

### R8 — Kualitas
- **SHALL**: Mobile-first, nyaman di layar 390px; tanpa error console; tanpa teks placeholder/lorem ipsum; tanpa tombol mati.
- **SHALL**: Semua angka rupiah diformat konsisten (`Rp 1.250.000`), tanggal dalam Bahasa Indonesia.
- **SHALL**: Tidak ada emoji sebagai ikon/label UI; ikon memakai inline SVG.
