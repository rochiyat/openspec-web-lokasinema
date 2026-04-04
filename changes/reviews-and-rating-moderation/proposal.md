# Proposal: reviews-and-rating-moderation

## Objective

Review & rating di detail lokasi: tampilkan review `published`, hitung average dari published saja, form submit user (login) → `pending`, admin moderasi publish/hide/delete + review editorial — API PRD §15.1–§15.3, §13.7, §23.

## Scope In

- `GET /api/reviews?locationId=...` publik: hanya published untuk display count/rating konsisten.
- `POST /api/reviews` (auth user) — validasi §20.2.
- Detail lokasi: list review + form untuk user login; placeholder jika belum ada review (§24.3).
- Admin: `GET/PATCH /api/admin/reviews` untuk status; kemampuan tambah review `reviewer_type=admin` (editorial).
- Recompute average rating saat perubahan status published (PRD §18, §23).

## Scope Out

- Trust score kompleks, anti-fraud ML.

## Dependencies

- **auth-and-role-guard**
- **location-detail-media-and-cta** (tempat render list/form; bisa dikembangkan bersamaan)

## Done Criteria (konkret)

- [ ] Review published tampil di detail lokasi; pending tidak tampil ke publik.
- [ ] User login dapat submit; guest tidak.
- [ ] Rating 1–5, comment min length sesuai §20.2.
- [ ] Admin dapat publish, hide, delete; admin editorial dapat langsung published (§23).
- [ ] Average rating dan count konsisten dengan aturan PRD §18.
