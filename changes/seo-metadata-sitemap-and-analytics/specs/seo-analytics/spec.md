# Capability: seo-analytics

Metadata SEO, sitemap, dan analytics event.

## Requirements

### E1 — Dynamic page metadata

Halaman detail lokasi dan layanan SHALL memiliki metadata dinamis (title, description) berdasarkan konten entitas.

### E2 — Open Graph

Sistem SHALL menyertakan Open Graph tags untuk halaman detail utama.

### E3 — Canonical URLs

Setiap halaman konten SHALL menyertakan canonical URL yang benar.

### E4 — Sitemap

Sistem SHALL menyediakan sitemap yang mencakup URL lokasi dan layanan published serta halaman statis kunci.

### E5 — Analytics events (optional)

Jika analytics dikonfigurasi, sistem SHOULD mengirim event untuk: penggunaan search, kunjungan detail lokasi, klik WhatsApp, submit inquiry/booking web (PRD §19.5).

## Scenarios

### E1

- **Given** lokasi published "Villa X"
- **When** crawler meminta HTML halaman detail
- **Then** title mengandung identitas lokasi yang unik

### E4

- **Given** ada N lokasi published
- **When** sitemap di-fetch
- **Then** terdapat N URL lokasi yang dapat diindeks

### E5

- **Given** analytics enabled
- **When** user mengklik WhatsApp CTA
- **Then** event tracking terkirim dengan konteks halaman
