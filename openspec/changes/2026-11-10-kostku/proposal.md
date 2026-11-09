# KOSTKU! — Juragan Kost

## Apa
Web app manajemen kos-kosan untuk pemilik kost: kelola kamar + penghuni, lacak pembayaran bulanan, catat pengeluaran operasional, dan kirim pengingat tagihan via WhatsApp — semua tersimpan di browser (localStorage), tanpa login, tanpa backend.

## Kenapa
Di Indonesia ada jutaan pemilik kost — dari yang punya 5 kamar sampai 50 kamar — dan hampir semuanya masih nagih pakai buku tulis atau ingatan. Aplikasi manajemen properti yang ada (Mamikos dkk.) dibuat untuk pencari kost, bukan pemiliknya; yang untuk pemilik biasanya SaaS berbayar dan ribet. KOSTKU! adalah "buku kas kost" yang langsung bisa dipakai: buka, lihat siapa yang belum bayar, ketuk "Tandai Lunas", kirim pengingat WA yang pesannya sudah dituliskan. Masalah nyata, solusi langsung.

## Kenapa ini mengejutkan
- Sudut pandang terbalik: bukan app cari kost (sudah ada puluhan), tapi app **juragan kost** — sisi yang tidak pernah dibuatkan alat.
- Efek "wah": tombol **Tandai Lunas** memberi cap stempel LUNAS animasi di kartu kamar, dan kalau semua kamar lunas, confetti meledak — momen kecil yang bikin nagih.
- Pengingat WA otomatis: pesan tagihan dituliskan dengan sopan + angka yang benar, tinggal salin atau buka WhatsApp. Ini fitur yang langsung terasa "kok kepikiran sih".
- Data contoh realistis: Kost Mawar di Batam, 10 kamar, harga Rp 600rb–1,6jt (grounded riset Mamikos/Infokost 2026), lengkap dengan penghuni yang telat bayar — jadi dari detik pertama app terasa hidup, bukan kosong.

## Kenapa bentuk output ini (web app static, tanpa backend)
- Semua data milik satu pemilik kost dan dipakai di satu HP — localStorage cukup, tanpa login/database.
- Harus bisa dibuka di HP kapan saja, offline-friendly, tanpa instalasi.
- Backend tidak menambah apa-apa di sini (tidak ada multi-user, tidak ada sinkronisasi) — pakai backend cuma biar kelihatan canggih, dilarang oleh brief program.

## Uji bar scope
Bukan utilitas satu fungsi: 5 fitur saling nyambung (kamar → pembayaran → pengeluaran → pengingat → grafik), state bertahan antar sesi, alur end-to-end (tambah penghuni → jatuh tempo → tagih → lunas → laporan). Selevel ArisanKu/KondanganKu, bukan kata-angka/Berani Resign. Lolos.

## IP check
Semua aset original (SVG digambar sendiri via kode, tanpa foto/stock). Tidak ada karakter atau merek berlisensi. Nama penghuni di data contoh adalah nama fiktif.

## Anti-AI-slop
Copy Bahasa Indonesia natural, tanpa emoji di label (preferensi Junan), tanpa kata-kata generik "selamat datang di aplikasi". Tombol menamai aksinya ("Tandai Lunas", "Kirim Pengingat"), error menamai masalah + jalan keluarnya.
