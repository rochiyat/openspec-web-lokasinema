# Design: reviews-and-rating-moderation

## Model

- Entity Review §14.10: `reviewer_type` user|admin, `status` pending|published|hidden.

## Public API

- Endpoint publik boleh mengembalikan aggregate `averageRating` dan `reviewCount` dari lokasi (sudah di DTO §32.1) — pastikan konsisten dengan sumber reviews published.

## Moderation UI

- Admin table di `/admin/reviews` dengan filter status dan aksi cepat.

## Referensi PRD

- §11.4 Flow D, §13.7, §14.10, §15.1–§15.3, §18, §20.2, §21.3, §23.
