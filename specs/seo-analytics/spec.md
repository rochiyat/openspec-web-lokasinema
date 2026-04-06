# seo-analytics Specification

## Purpose
TBD - created by archiving change seo-metadata-sitemap-and-analytics. Update Purpose after archive.
## Requirements
### Requirement: Dynamic page metadata

Halaman detail lokasi dan layanan SHALL memiliki metadata dinamis (title, description) berdasarkan konten entitas.

#### Scenario: crawler melihat metadata lokasi

- **GIVEN** lokasi published "Villa X" memiliki `name` dan deskripsi singkat
- **WHEN** crawler meminta HTML halaman detail lokasi
- **THEN** title mengandung identitas lokasi yang unik
- **AND** description relevan dengan konten lokasi

### Requirement: Open Graph

Sistem SHALL menyertakan Open Graph tags untuk halaman detail utama.

#### Scenario: share preview halaman detail

- **GIVEN** halaman detail lokasi memiliki title dan cover image (jika tersedia)
- **WHEN** halaman di-preview oleh Open Graph crawler
- **THEN** OG title dan OG description terisi
- **AND** OG image digunakan jika tersedia, jika tidak maka fallback default digunakan

### Requirement: Canonical URLs

Setiap halaman konten SHALL menyertakan canonical URL yang benar.

#### Scenario: canonical mengarah ke URL produksi

- **GIVEN** user membuka halaman `/locations/[slug]` atau `/services/[slug]`
- **WHEN** HTML dirender
- **THEN** canonical URL mengarah ke URL produksi yang benar untuk halaman tersebut

### Requirement: Sitemap

Sistem SHALL menyediakan sitemap yang mencakup URL lokasi dan layanan published serta halaman statis kunci.

#### Scenario: sitemap memuat semua entri published

- **GIVEN** ada N lokasi published dan M layanan published
- **WHEN** `sitemap.xml` di-fetch
- **THEN** terdapat N+M URL konten yang dapat diindeks
- **AND** halaman statis utama juga terdaftar

### Requirement: Analytics events (optional)

Jika analytics dikonfigurasi, sistem SHALL mengirim event untuk: penggunaan search, kunjungan detail lokasi, klik WhatsApp, submit inquiry/booking web (PRD §19.5).

#### Scenario: tracking WhatsApp click saat analytics aktif

- **GIVEN** analytics enabled
- **AND** user berada di halaman detail lokasi
- **WHEN** user mengklik WhatsApp CTA
- **THEN** event tracking terkirim dengan konteks halaman (mis. `page_type=location`, `slug`, dan sumber CTA)

