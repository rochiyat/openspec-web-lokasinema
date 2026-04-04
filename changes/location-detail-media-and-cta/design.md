# Design: location-detail-media-and-cta

## WhatsApp helper

- Pusatkan pembentukan string di `lib/whatsapp.ts` (PRD §16.3, §30) agar konsisten dengan inquiry/services nanti.

## Auth gate untuk form CTA

- Tombol "Kirim Pesan" → jika tidak ada session, `redirect` ke `/login?returnUrl=...`.

## YouTube validation

- Validasi format embed `https://www.youtube.com/embed/{id}` sebelum render iframe (PRD §17.5).

## Referensi PRD

- §13.3, §11.1–§11.2, §18 Business Rules (guest boleh WA, form web butuh login), §21.3 (partial: tanpa review submit).
