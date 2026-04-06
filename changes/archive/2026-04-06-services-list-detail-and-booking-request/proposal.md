# Proposal: services-list-detail-and-booking-request

## Objective

Layanan produksi di situs publik: listing `/services`, detail `/services/[slug]`, CTA WhatsApp (template service) dan booking request via form web (authenticated) dengan `type=service_booking`, field §13.6 — plus admin minimal: CRUD/publish service (PRD §13.4, §14.9, §15.1 & §15.3).

## Scope In

- Public: `GET /api/services`, `GET /api/services/:slug` — hanya `is_published=true`.
- Halaman list + detail dengan icon/cover, deskripsi, starting price, CTA.
- WhatsApp CTA memakai template layanan (PRD §13.6).
- `POST /api/inquiries` dengan `service_id` wajib untuk service booking; field form §13.6.
- Admin: `POST/PATCH/DELETE /api/admin/services` dan UI `/admin/services` (sesuai IA).

## Scope Out

- Payment gateway, scheduling engine, owner portal (PRD §6.2).

## Dependencies

- **foundation-app-routing-and-shared-types**
- **auth-and-role-guard** (untuk form booking web)
- **web-inquiry-submission** (boleh paralel: jika inquiry module belum ada, slice ini mencakup endpoint generik `inquiries` untuk kedua tipe — koordinasikan urutan implementasi; dependency logis: inquiries API harus ada sebelum booking submit)

## Done Criteria (konkret)

- [x] Publik dapat menjelajah services published.
- [x] Detail service menampilkan konten utama PRD.
- [x] User login dapat mengirim service booking request tervalidasi (§20.3).
- [x] WhatsApp CTA service membuka pesan dengan nama layanan + URL.
- [x] Admin dapat publish/unpublish dan mengedit service.
