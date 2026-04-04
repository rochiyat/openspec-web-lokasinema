# Proposal: location-detail-media-and-cta

## Objective

Halaman detail lokasi publik: galeri + YouTube opsional, metadata lokasi, spesifikasi teknis, fasilitas, starting price, rating ringkasan, CTA WhatsApp (prefill) dan CTA form web (mengarah login jika perlu), related locations — **tanpa** form review lengkap dan moderasi (change reviews terpisah).

## Scope In

- `GET /api/locations/:slug` (PRD §15.1).
- Gallery: cover + thumbnails; lazy load (PRD §19.1).
- YouTube embed hanya jika `youtube_embed_url` valid (PRD §13.3, §17.5).
- Tampilan: title, address/city/province, rating average & count, starting price, featured, description, technical specs (akses, pencahayaan, listrik, suara, fasilitas, catatan), facilities.
- CTA WhatsApp: teks sesuai template §13.6 (location).
- CTA web inquiry: jika guest → redirect/login; tidak submit form di slice ini (form submit di `web-inquiry-submission`).
- Related locations (boleh heuristic sederhana: same city/category).

## Scope Out

- Submit review & daftar review moderasi (change `reviews-and-rating-moderation`).
- Penyimpanan inquiry (change `web-inquiry-submission`).

## Dependencies

- **foundation-app-routing-and-shared-types**
- **location-listing-search-filter-map** (navigasi dari listing; bisa paralel setelah API detail ada)

## Done Criteria (konkret)

- [ ] Semua field utama lokasi dari PRD tampil tanpa ambiguitas untuk data published.
- [ ] WhatsApp membuka `wa.me` dengan body pesan berisi nama lokasi, URL halaman, placeholder nama user.
- [ ] CTA form web memerlukan login: guest diarahkan ke alur auth.
- [ ] Video YouTube hanya render jika URL valid/embed.
- [ ] Galeri mendukung multiple image + cover.
- [ ] Related locations ditampilkan bila data tersedia.
