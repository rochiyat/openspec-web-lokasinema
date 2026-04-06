# Design: services-list-detail-and-booking-request

## Inquiry reuse

- Satu tabel `inquiries` dengan `type` enum (PRD §14.11); booking memakai field yang sama dengan inquiry lokasi: `company_name`, `preferred_date`, `budget_range`, `message`, dll.
- **Pemetaan PRD §13.6:** teks kebutuhan layanan (“service needs”) disimpan di kolom **`message`** (panjang teks), bukan kolom terpisah — sama seperti ringkasan kebutuhan pada `location_inquiry`. Form web mengirim `message` wajib; field opsional lain mengikuti DTO `CreateInquiryDto`.

## WhatsApp

- `buildServiceWhatsAppMessage` di `lib/whatsapp.ts` konsisten dengan lokasi.

## Admin

- Form service lebih sederhana dari lokasi; tidak wajib Cloudinary jika hanya `cover_image_url` string opsional.

## Referensi PRD

- §11.3 Flow C, §13.4, §13.6, §14.9, §15.1, §15.3, §21.4.

## Dependency note

`POST /api/inquiries` mendukung `location_inquiry` dan `service_booking` (validator + `service_id` wajib bila tipe `service_booking`).
