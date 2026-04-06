# Capability: services-booking

## Purpose

Layanan produksi di situs publik (katalog, detail, WhatsApp, booking web) dan pengelolaan layanan di admin — disinkronkan dari change `services-list-detail-and-booking-request`.

## Requirements

### Requirement: Public service catalog

Sistem SHALL mengekspos daftar dan detail layanan yang `is_published=true`.

#### Scenario: Layanan unpublished tidak tampil di katalog

- **GIVEN** ada layanan dengan `is_published=false`
- **WHEN** publik membuka katalog layanan (mis. `/services`)
- **THEN** layanan tersebut tidak muncul di daftar publik

### Requirement: Service detail content

Detail layanan publik SHALL mencakup title, slug, descriptions, icon/cover bila ada, starting price opsional, dan CTA booking (PRD §13.4).

#### Scenario: Halaman detail menampilkan konten lengkap

- **GIVEN** layanan terpublikasi dengan metadata lengkap
- **WHEN** publik membuka halaman detail via slug
- **THEN** title, slug, deskripsi, aset visual bila ada, harga mulai dari bila dikonfigurasi, dan CTA booking tersedia

### Requirement: Service WhatsApp CTA

CTA WhatsApp SHALL memakai template konteks layanan (PRD §13.6).

#### Scenario: Link atau deep link menyertakan konteks layanan

- **GIVEN** pengguna membuka detail layanan terpublikasi
- **WHEN** pengguna memilih aksi WhatsApp
- **THEN** template pesan atau URL mencerminkan identitas/konteks layanan yang dipilih

### Requirement: Web booking submission

Pengguna terautentikasi SHALL dapat mengirim `service_booking` dengan `service_id` wajib dan field form sesuai §13.6.

#### Scenario: Submit booking valid tersimpan

- **GIVEN** user login di halaman layanan Y
- **WHEN** user mengirim form booking yang valid
- **THEN** inquiry tersimpan dengan `type=service_booking` dan `service_id` layanan Y

### Requirement: Admin service management

Admin SHALL dapat membuat, mengedit, menghapus, dan publish/unpublish layanan.

#### Scenario: Unpublish menghilangkan dari katalog publik

- **GIVEN** admin mengubah `is_published` menjadi false untuk suatu layanan
- **WHEN** publik memuat katalog atau detail publik
- **THEN** layanan tidak lagi tersedia di endpoint publik

### Requirement: Starting price wording

UI SHALL menyatakan harga sebagai "mulai dari" / starting price (PRD §18).

#### Scenario: Label harga konsisten di katalog dan detail

- **GIVEN** layanan memiliki starting price
- **WHEN** pengguna melihat kartu katalog atau halaman detail
- **THEN** penyebutan harga memakai wording "mulai dari" (atau ekuivalen) sesuai PRD §18
