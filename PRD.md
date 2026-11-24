# PRD — Platform Web Edukasi dan Adopsi Simbolis Konservasi Badak

**Judul skripsi:** Pengembangan Platform Web Edukasi dan Adopsi Simbolis Konservasi Satwa Langka Indonesia (Studi Kasus Relokasi & Perlindungan Badak)
**Nama produk (sementara):** BadakKita
**Versi dokumen:** 1.0 · 24 November 2026
**Prototipe:** https://claude.ai/artifact/Xr7ttEnhm3WGWj6qxPGFsC (gambar per halaman ada di folder `prototipe/`)

---

## 1. Ringkasan

BadakKita adalah platform web yang menggabungkan **edukasi** tentang badak Indonesia (Badak Jawa dan Badak Sumatera), **informasi program relokasi dan perlindungan**, serta **adopsi simbolis**. Lewat adopsi simbolis, pengguna berdonasi dan menerima sertifikat digital beserta kabar berkala tentang badak yang mereka "adopsi". Seluruh alur dana ditampilkan secara transparan.

## 2. Latar belakang dan masalah

- Badak Jawa (*Rhinoceros sondaicus*) dan Badak Sumatera (*Dicerorhinus sumatrensis*) sama-sama berstatus **Kritis (Critically Endangered)** menurut IUCN.
- Badak Jawa hanya tersisa di satu kawasan (TN Ujung Kulon), sehingga sangat rentan terhadap bencana, penyakit, dan perburuan. Inilah alasan dibutuhkannya program habitat kedua (relokasi).
- Masalah yang ingin diselesaikan:
  1. Pengetahuan masyarakat, terutama pelajar dan mahasiswa, tentang badak Indonesia masih rendah, dan materinya tersebar di banyak sumber.
  2. Belum ada saluran partisipasi yang mudah, menarik, dan transparan bagi publik untuk ikut mendukung konservasi badak.
  3. Perkembangan program relokasi dan perlindungan sulit diikuti oleh publik.

> Catatan: angka populasi terbaru dan data program wajib diambil dari sumber resmi (KLHK, IUCN, mitra konservasi) dan dicantumkan sumbernya di Bab 2 skripsi.

## 3. Tujuan dan metrik keberhasilan

| Tujuan | Indikator (untuk evaluasi skripsi) |
|---|---|
| Menyediakan media edukasi yang mudah dipahami | Skor kuis pengguna; skor SUS ≥ 68 (kategori *acceptable*) |
| Menyediakan alur adopsi simbolis yang lengkap | Seluruh skenario Black Box Testing pada modul adopsi lulus |
| Menampilkan transparansi dana | Laporan alokasi dana tampil dan sesuai dengan data transaksi |
| Menginformasikan progres program relokasi | Admin dapat memperbarui tahap; perubahan tampil di halaman publik |

## 4. Ruang lingkup

### Termasuk (in scope)
- Konten edukasi: profil dua spesies, artikel, peta kawasan habitat, kuis.
- Halaman studi kasus relokasi: tahapan program, catatan lapangan, upaya perlindungan.
- Adopsi simbolis: katalog badak, paket, checkout, pembayaran **mode sandbox**, sertifikat PDF ber-QR, verifikasi sertifikat, dashboard adopter.
- Transparansi dana: ringkasan dana terkumpul, persentase penyaluran, alokasi per program.
- Panel admin (CMS) untuk seluruh data di atas.

### Batasan (out of scope)
- Transaksi uang sungguhan. Pembayaran hanya diuji di mode sandbox.
- Pelacakan lokasi badak secara real-time. Lokasi hanya ditampilkan di tingkat kawasan demi keamanan dari perburuan.
- Kepemilikan atau kunjungan fisik. Adopsi bersifat **simbolis**.
- Aplikasi mobile native. Platform berupa web yang responsif.
- Data badak individu bersifat ilustratif kecuali ada kerja sama resmi dengan lembaga konservasi.

## 5. Aktor

| Aktor | Deskripsi | Hak akses utama |
|---|---|---|
| Pengunjung | Publik tanpa akun | Membaca edukasi, mengerjakan kuis, melihat program dan transparansi, memverifikasi sertifikat |
| Adopter | Pengguna terdaftar yang melakukan adopsi | Semua hak pengunjung + adopsi, sertifikat, dashboard adopter, riwayat |
| Admin konten | Pengelola materi | CRUD artikel, kuis, profil spesies, data badak, catatan lapangan, tahap program |
| Admin keuangan | Pengelola transaksi | Verifikasi transaksi, laporan dana, alokasi |

## 6. Kebutuhan fungsional

Prioritas: **M** = wajib (MVP), **N** = nilai tambah, **L** = pengembangan lanjut.

### 6.1 Modul akun
| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-01 | Registrasi dengan email dan password, verifikasi email | M |
| FR-02 | Login, logout, lupa password | M |
| FR-03 | Pengelolaan profil adopter | M |
| FR-04 | Role-based access: pengunjung, adopter, admin konten, admin keuangan | M |

### 6.2 Modul edukasi
| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-10 | Profil spesies: nama, nama latin, status IUCN, ciri, habitat, ancaman, populasi beserta sumber | M |
| FR-11 | Artikel dengan kategori (Spesies, Relokasi, Perlindungan), pencarian, dan filter | M |
| FR-12 | Peta interaktif kawasan habitat (Leaflet + OpenStreetMap), **tanpa koordinat individu** | N |
| FR-13 | Kuis pilihan ganda dengan skor dan umpan balik per jawaban | N |
| FR-14 | Badge untuk pengguna yang menyelesaikan kuis dengan skor penuh | L |

### 6.3 Modul relokasi dan perlindungan
| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-20 | Halaman program: latar belakang, kawasan asal dan tujuan (nama boleh disamarkan) | M |
| FR-21 | Progress tracker 5 tahap (Kajian habitat → Persiapan → Translokasi → Adaptasi → Pemantauan) dengan status Selesai/Berjalan/Menunggu | N |
| FR-22 | Catatan lapangan (judul, tanggal, isi, foto) yang dikelola admin | N |
| FR-23 | Informasi upaya perlindungan (patroli, kamera jebak, habitat, edukasi masyarakat) | M |

### 6.4 Modul adopsi simbolis
| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-30 | Katalog badak: nama, spesies, jenis kelamin, perkiraan umur, cerita, foto | M |
| FR-31 | Paket adopsi bertingkat (nama, harga, durasi, benefit) yang dikelola admin | M |
| FR-32 | Ringkasan pesanan dan persetujuan syarat adopsi simbolis (wajib dicentang) | M |
| FR-33 | Opsi adopsi sebagai hadiah (nama, email, dan pesan untuk penerima) | N |
| FR-34 | Pembayaran via payment gateway (Midtrans/Xendit) mode sandbox, termasuk webhook/callback status | M |
| FR-35 | Pembuatan sertifikat PDF otomatis dengan nomor unik (format `BK-YYYY-NNNNNN`) dan QR code | M |
| FR-36 | Halaman publik verifikasi keaslian sertifikat (dari scan QR atau input nomor) | M |
| FR-37 | Pengiriman email konfirmasi beserta sertifikat | N |
| FR-38 | Dashboard adopter: riwayat adopsi, unduh ulang sertifikat, kabar berkala, sisa masa adopsi | M |
| FR-39 | Pengingat dan perpanjangan adopsi sebelum masa berlaku habis | L |

### 6.5 Modul transparansi dana
| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-40 | Ringkasan publik: total dana terkumpul, jumlah adopter aktif, persentase tersalurkan | M |
| FR-41 | Alokasi dana per program (relokasi, patroli, edukasi, operasional) | N |
| FR-42 | Laporan penyaluran yang dapat diunduh (PDF) | N |

### 6.6 Modul admin
| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-50 | Dashboard statistik: donasi per bulan, adopsi baru, transaksi menunggu, kuis selesai | M |
| FR-51 | CRUD artikel, kuis, profil spesies, data badak, paket, tahap program, catatan lapangan | M |
| FR-52 | Daftar transaksi dengan filter status (Berhasil/Menunggu/Gagal) dan verifikasi manual | M |
| FR-53 | Kelola pengguna dan role | M |
| FR-54 | Ekspor laporan transaksi dan dana | N |

## 7. Alur utama: adopsi simbolis

1. Pengguna membuka katalog → memilih badak → memilih paket → (opsional) menandai sebagai hadiah.
2. Login atau registrasi bila belum masuk.
3. Mengisi data adopter → memilih metode bayar → mencentang persetujuan adopsi simbolis.
4. Sistem membuat transaksi berstatus **Menunggu** → pengguna diarahkan ke payment gateway (sandbox).
5. Callback dari gateway mengubah status menjadi **Berhasil** atau **Gagal**. Admin keuangan bisa memverifikasi transaksi secara manual.
6. Jika berhasil: sistem membuat nomor sertifikat dan PDF ber-QR, lalu mengirim email, dan adopsi aktif tampil di dashboard adopter.
7. Siapa pun dapat memindai QR untuk membuka halaman verifikasi sertifikat.

## 8. Kebutuhan non-fungsional

| ID | Kategori | Kebutuhan |
|---|---|---|
| NFR-01 | Keamanan lokasi satwa | Tidak menyimpan atau menampilkan koordinat individu badak. Peta hanya di tingkat kawasan. |
| NFR-02 | Keamanan aplikasi | Password di-hash (bcrypt), proteksi CSRF, validasi input, signature key untuk callback pembayaran |
| NFR-03 | Privasi | Data adopter tidak ditampilkan publik. Halaman verifikasi hanya menampilkan nama di sertifikat dan masa berlaku. |
| NFR-04 | Responsif | Tampilan layak di lebar 360 px (ponsel) hingga desktop |
| NFR-05 | Aksesibilitas | Kontras teks minimal 4.5:1, elemen interaktif bisa diakses keyboard, alt text pada foto |
| NFR-06 | Performa | Halaman publik termuat < 3 detik pada koneksi 4G; gambar dikompresi (WebP) |
| NFR-07 | Hak cipta konten | Setiap foto mencantumkan sumber dan lisensi (mis. Wikimedia Commons CC BY) |

## 9. Model data (entitas utama)

| Entitas | Atribut penting |
|---|---|
| users | id, nama, email, password, role, created_at |
| species | id, nama, nama_latin, status_iucn, ciri, habitat, populasi, sumber_data |
| threats | id, species_id, nama |
| rhinos | id, species_id, nama, jenis_kelamin, perkiraan_umur, cerita, foto, status_adopsi |
| packages | id, nama, harga, durasi_bulan, benefit (JSON), aktif |
| adoptions | id, user_id, rhino_id, package_id, is_gift, nama_penerima, email_penerima, pesan, mulai, berakhir, status |
| transactions | id, adoption_id, kode, nominal, metode, status, gateway_ref, paid_at |
| certificates | id, adoption_id, nomor, nama_di_sertifikat, file_pdf, issued_at |
| updates | id, rhino_id, judul, isi, foto, tanggal (kabar untuk adopter) |
| programs | id, nama, kawasan_asal, kawasan_tujuan, deskripsi |
| program_stages | id, program_id, urutan, judul, periode, status, deskripsi |
| field_notes | id, program_id, judul, isi, foto, tanggal, tim |
| articles | id, kategori, judul, slug, isi, thumbnail, penulis_id, published_at |
| quizzes / questions / options / quiz_attempts | soal, pilihan, jawaban benar, skor pengguna |
| fund_allocations | id, periode, program, persentase, nominal |

## 10. Peta halaman (sesuai prototipe)

| No | Halaman | Gambar |
|---|---|---|
| 1 | Beranda | `prototipe/01-main.png` |
| 2 | Pusat Edukasi | `prototipe/02-edukasi.png` |
| 3 | Relokasi & Perlindungan | `prototipe/03-relokasi.png` |
| 4 | Katalog & Paket Adopsi | `prototipe/04-adopsi.png` |
| 5 | Checkout | `prototipe/05-checkout.png` |
| 6 | Sertifikat & Verifikasi | `prototipe/06-sertifikat.png` |
| 7 | Dashboard Admin | `prototipe/07-admin.png` |

## 11. Integrasi pihak ketiga

- **Payment gateway:** Midtrans atau Xendit (sandbox) → Snap/Invoice API + webhook.
- **Peta:** Leaflet + tile OpenStreetMap.
- **PDF:** DomPDF (Laravel) atau sejenisnya.
- **QR code:** library QR (mis. `simplesoftwareio/simple-qrcode`).
- **Email:** SMTP (Mailtrap untuk pengujian).

## 12. Rekomendasi teknologi (boleh disesuaikan)

- Backend: Laravel (PHP) + MySQL/MariaDB
- Frontend: Blade + Tailwind CSS (atau Inertia/Vue bila diperlukan)
- Admin panel: Filament (opsional, mempercepat CRUD)
- Hosting uji: VPS atau shared hosting dengan PHP 8.2+

## 13. Rencana pengujian

| Jenis | Cakupan |
|---|---|
| Black Box Testing | Semua FR prioritas M: skenario normal dan skenario gagal (validasi form, pembayaran gagal, nomor sertifikat salah) |
| Pengujian integrasi | Callback payment gateway → status transaksi → sertifikat terbit |
| UAT | Responden dari target pengguna (pelajar/mahasiswa, calon donatur) |
| SUS (System Usability Scale) | 10 pernyataan, minimal 20–30 responden; target skor ≥ 68 |

## 14. Risiko dan mitigasi

| Risiko | Mitigasi |
|---|---|
| Data badak sungguhan sensitif atau tidak tersedia | Gunakan data ilustratif, tulis di batasan masalah |
| Penggalangan dana publik memerlukan izin | Prototipe memakai mode sandbox; implementasi nyata bekerja sama dengan lembaga resmi |
| Foto berhak cipta | Gunakan foto berlisensi terbuka (Wikimedia Commons) dengan atribusi |
| Lingkup terlalu luas untuk waktu skripsi | Kerjakan prioritas M dulu, lalu N jika waktu cukup; L masuk saran penelitian |

## 15. Tahapan pengerjaan (usulan, metode Prototyping)

1. Pengumpulan kebutuhan dan studi literatur
2. Prototipe UI (sudah ada) → evaluasi dengan pengguna
3. Perancangan: use case, activity diagram, ERD, desain database
4. Implementasi modul M: akun → edukasi → katalog & paket → checkout & pembayaran sandbox → sertifikat & verifikasi → admin
5. Implementasi modul N
6. Pengujian Black Box, UAT, dan SUS
7. Perbaikan dan penulisan laporan

## 16. Lampiran: sumber foto yang disarankan

- `Sumatran_Rhinoceros_Way_Kambas_2008.jpg`: Willem v Strien, CC BY 2.0 (Wikimedia Commons)
- `Sumatran_rhinoceros_and_juvenile.jpg`: Wikimedia Commons
- `Rhinoceros_sondaicus_in_London_Zoo.jpg`: domain publik (Wikimedia Commons)
