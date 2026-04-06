# Design: admin-location-crud-and-cloudinary

## Cloudinary

- Transformasi ramah web via URL atau upload preset (PRD §17.4).
- Tidak simpan binary di PostgreSQL (PRD §17.2).

## Data model

- `Location`, `LocationMedia`, `LocationSpecs`, join categories/tags sesuai §14.

## Security

- Semua route `/api/admin/locations*` dilindungi JWT + role admin (PRD §19.2).

## Referensi PRD

- §13.8, §14.2–§14.8, §15.3, §17.3–§17.5, §20.1, §21.5 (partial locations).
