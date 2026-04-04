# Capability: services-booking

Layanan produksi publik dan booking request.

## Requirements

### S1 — Public service catalog

Sistem SHALL mengekspos daftar dan detail layanan yang `is_published=true`.

### S2 — Service detail content

Detail SHALL mencakup title, slug, descriptions, icon/cover bila ada, starting price opsional, CTA booking (PRD §13.4).

### S3 — Service WhatsApp CTA

WhatsApp SHALL menggunakan template konteks layanan (PRD §13.6).

### S4 — Web booking submission

User terautentikasi SHALL dapat mengirim `service_booking` dengan `service_id` wajib dan field form §13.6.

### S5 — Admin service management

Admin SHALL dapat membuat, mengedit, menghapus, dan publish/unpublish layanan.

### S6 — Starting price wording

UI SHALL menyatakan harga sebagai "mulai dari" / starting price (PRD §18).

## Scenarios

### S1

- **Given** ada layanan unpublished
- **When** publik membuka `/services`
- **Then** layanan tersebut tidak muncul

### S4

- **Given** user login di halaman layanan Y
- **When** user mengirim booking form valid
- **Then** inquiry tersimpan dengan `type=service_booking` dan `service_id` layanan Y

### S5

- **Given** admin mengubah `is_published` menjadi false
- **When** publik memuat catalog
- **Then** layanan tidak lagi tersedia di endpoint publik
