# Capability: admin-locations

CMS admin untuk lokasi dan media Cloudinary.

## ADDED Requirements

### Requirement: Admin location CRUD

Admin SHALL dapat membuat, membaca, memperbarui, dan menghapus lokasi.

#### Scenario: Admin mengelola siklus hidup lokasi

- **GIVEN** admin terautentikasi dengan peran admin
- **WHEN** admin membuat lokasi baru, memperbarui field, membaca detail, dan menghapus lokasi
- **THEN** setiap operasi berhasil sesuai kontrak API admin dan data konsisten

### Requirement: Cloudinary media upload

Admin SHALL dapat mengunggah gambar ke Cloudinary; sistem SHALL menyimpan metadata sesuai PRD §14.3.

#### Scenario: Upload dan penetapan cover

- **GIVEN** admin di form lokasi
- **WHEN** admin mengunggah tiga gambar dan menetapkan satu sebagai cover
- **THEN** media tersimpan dengan `is_cover` benar dan tampil di API admin serta publik sesuai aturan publish

### Requirement: Cover image required to publish

Sistem SHALL mencegah publish lokasi tanpa minimal satu cover image (PRD §18, §20.1).

#### Scenario: Publish tanpa cover ditolak

- **GIVEN** lokasi tanpa gambar cover
- **WHEN** admin mencoba set `is_published=true`
- **THEN** sistem menolak dengan pesan validasi

### Requirement: YouTube embed URL

Admin SHALL dapat menyimpan URL embed YouTube yang divalidasi (PRD §17.5).

#### Scenario: URL embed valid diterima

- **GIVEN** admin mengedit lokasi
- **WHEN** admin menyimpan URL embed YouTube yang valid
- **THEN** URL tersimpan dan dapat ditampilkan di tampilan publik sesuai aturan

### Requirement: Unpublished location not public

Lokasi dengan `is_published=false` SHALL tidak diexpose di endpoint publik.

#### Scenario: Lokasi draft tersembunyi dari publik

- **GIVEN** lokasi ada dengan `is_published=false`
- **WHEN** klien publik memanggil endpoint listing atau detail lokasi
- **THEN** lokasi tersebut tidak muncul di respons publik

### Requirement: Admin-only location endpoints

Hanya admin SHALL dapat mengakses endpoint admin lokasi.

#### Scenario: Non-admin ditolak memanggil admin API

- **GIVEN** user biasa dengan token valid
- **WHEN** user memanggil POST admin locations
- **THEN** request ditolak
