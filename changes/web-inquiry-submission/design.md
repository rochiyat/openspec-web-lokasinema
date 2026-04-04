# Design: web-inquiry-submission

## API

- `POST /api/inquiries` body selaras `CreateInquiryDto` PRD §32.2 dengan `type: 'location_inquiry'`.

## UX

- Salin prinsip CTA: teks bahwa form membutuhkan login (PRD §22.2).
- Setelah sukses: toast atau halaman konfirmasi + opsi WhatsApp tetap tersedia.

## Admin follow-up

- Status enum: new, contacted, qualified, booked, closed (PRD §26.1) — update status bisa task terpisah kecil atau gabung jika tim ingin satu slice; proposal ini fokus **submission** end-user.

## Referensi PRD

- §11.2 Flow B, §13.6, §14.11, §15.2, §20.3.
