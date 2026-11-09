# DESIGN.md — KOSTKU!

Ditulis setelah build, dari dunia visual yang benar-benar terpasang.

## Tokens
- `--green-900: #14532d` (header, aksi primer), `--green-600: #15803d` (lunas), `--paper: #fafaf7` (ground), `--ink: #1c1917`, `--amber: #b45309` (jatuh tempo), `--red: #b91c1c` (terlambat), `--muted: #78716c`.
- Font: Plus Jakarta Sans (400/500/700/800). Angka rupiah tabular.
- Radius 14–18px, shadow lembut ber-offset + blur (bukan hard shadow), tanpa gradient dekoratif.

## Komponen
- **Plat kamar**: kartu dengan nomor kamar besar (700), harga, chip fasilitas, nama penghuni, badge status (Lunas/Menunggu/Jatuh tempo/Terlambat N hari/Kosong).
- **Stempel LUNAS**: teks "LUNAS" border ganda hijau, rotate −8°, animasi scale-in 300ms saat ditandai.
- **Ring progres**: SVG circle, persentase kamar lunas bulan berjalan.
- **Grafik batang**: 6 bulan terakhir, bar CSS, nilai di atas bar.
- **Tab bawah**: Kamar / Pembayaran / Pengeluaran / Pengingat (mobile-first, sticky).
- **Toast**: bawah layar, 2,5 detik. **Confetti**: canvas burst sekali saat 100% lunas.
- **Modal**: tambah/edit kamar, isi penghuni, tambah pengeluaran — form sederhana, validasi saat submit.
