# Design: services-list-detail-and-booking-request

## Inquiry reuse

- Satu tabel `inquiries` dengan `type` enum (PRD §14.11); booking menggunakan field company_name, preferred_date, service_needs, budget_range, dll.

## WhatsApp

- `buildServiceWhatsAppMessage` di `lib/whatsapp.ts` konsisten dengan lokasi.

## Admin

- Form service lebih sederhana dari lokasi; tidak wajib Cloudinary jika hanya `cover_image_url` string opsional.

## Referensi PRD

- §11.3 Flow C, §13.4, §13.6, §14.9, §15.1, §15.3, §21.4.

## Dependency note

Implementasi tim: pastikan `POST /api/inquiries` mendukung kedua tipe sebelum menutup slice ini; jika `web-inquiry-submission` sudah merge, extend validator untuk `service_booking`.
