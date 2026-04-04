# Capability: admin-locations

CMS admin untuk lokasi dan media Cloudinary.

## Requirements

### M1 — CRUD location

Admin SHALL dapat membuat, membaca, memperbarui, dan menghapus lokasi.

### M2 — Cloudinary media

Admin SHALL dapat mengunggah gambar ke Cloudinary; sistem SHALL menyimpan metadata PRD §14.3.

### M3 — Cover requirement for publish

Sistem SHALL mencegah publish lokasi tanpa minimal satu cover image (PRD §18, §20.1).

### M4 — YouTube embed URL

Admin SHALL dapat menyimpan URL embed YouTube yang divalidasi (PRD §17.5).

### M5 — Visibility rules

Lokasi dengan `is_published=false` SHALL tidak diexpose di endpoint publik.

### M6 — Authorization

Hanya admin SHALL dapat mengakses endpoint admin lokasi.

## Scenarios

### M2

- **Given** admin di form lokasi
- **When** admin mengunggah tiga gambar dan menetapkan satu sebagai cover
- **Then** media tersimpan dengan `is_cover` benar dan tampil di API admin/publik sesuai publish

### M3

- **Given** lokasi tanpa gambar cover
- **When** admin mencoba set `is_published=true`
- **Then** sistem menolak dengan pesan validasi

### M6

- **Given** user biasa dengan token valid
- **When** user memanggil POST admin locations
- **Then** request ditolak
