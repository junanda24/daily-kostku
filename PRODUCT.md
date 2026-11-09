# PRODUCT.md — KOSTKU!

## Product truth
- **Nama**: KOSTKU! — Juragan Kost
- **Untuk siapa**: pemilik kos-kosan di Indonesia (5–50 kamar) yang hari ini nagih pakai buku tulis atau ingatan.
- **Job**: dalam 3 detik tahu siapa yang belum bayar bulan ini, tandai lunas, kirim pengingat WA yang pesannya sudah ditulis.
- **Fakta**: data milik satu pemilik, satu HP → localStorage cukup; tanpa login, tanpa backend.
- **Data contoh**: "Kost Mawar", Batam, 10 kamar, harga Rp 600.000–1.600.000 (grounded riset Mamikos/Infokost 2026). Nama penghuni fiktif.
- **Mode**: Operate. **Asumsi (tanpa wawancara — run terjadwal, user tidak bisa menjawab)**: pemilik kost mengutamakan kecepatan dan kejelasan status di atas estetika; bulan berjalan adalah konteks utama.

## Surface brief — direction contract
- **THESIS**: buku kas kost yang serius tapi hangat. Juragan membuka app dan langsung tahu siapa yang belum bayar — tanpa tabel spreadsheet, tanpa login.
- **OWN-WORLD**: "Buku Kas Hijau" — hijau tua committed (#14532d), kertas #fafaf7, tinta #1c1917; kartu kamar seperti plat nomor pintu; cap stempel LUNAS; angka rupiah tabular; ikon SVG, tanpa emoji.
- **STORY**: pengguna melihat ring progres + tunggakan, menandai kamar lunas (stempel!), menyalin pesan WA untuk yang telat, mencatat listrik — selesai dalam semenit.
- **FIRST VIEWPORT**: header hijau tua (nama kost + bulan ‹ Nov 2026 ›), angka pemasukan besar, ring "7 dari 9 lunas", 4 kartu stat ringkas, lalu daftar kamar. Aksi primer: "Tandai Lunas" di tiap kartu.
- **FORM**: code-led (run terjadwal, tanpa decision page). Signature interaction: cap stempel LUNAS + confetti saat 100% lunas.
- **FINISH**: unreviewed and undocumented is unfinished; this build ends with the finish review, the verdict, DESIGN.md, and every shipping raster carrying its provenance.
