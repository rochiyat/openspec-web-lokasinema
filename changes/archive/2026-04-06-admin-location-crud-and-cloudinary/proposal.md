# Proposal: admin-location-crud-and-cloudinary

## Objective

Panel admin untuk CRUD lokasi, upload gambar ke Cloudinary (metadata di `LocationMedia`), simpan YouTube embed URL, kategori/tag, spesifikasi teknis, publish/featured — sesuai PRD §13.8, §14.2–§14.8, §15.3, §17.3–§17.4, §20.1.

## Scope In

- Rute admin: list, new, edit `/admin/locations`, `/admin/locations/new`, `/admin/locations/[id]`.
- API: `POST/PATCH/DELETE /api/admin/locations`, `POST/DELETE .../media` (PRD §15.3).
- Integrasi Cloudinary SDK: upload, simpan `public_id`, `secure_url`, dimensi, `is_cover`, `sort_order`.
- Validasi publish: minimal satu cover image sebelum `is_published=true` (PRD §18, §20.1).
- YouTube URL validasi embed.

## Scope Out

- CRUD services, categories standalone (boleh minimal read untuk dropdown jika perlu — task terinci).
- Reviews, bookings modules penuh.

## Dependencies

- **auth-and-role-guard** (admin only).

## Done Criteria (konkret)

- [x] Admin dapat membuat, mengedit, menghapus lokasi.
- [x] Upload banyak gambar ke Cloudinary; set cover; urutan sort.
- [x] Lokasi unpublished tidak muncul di API publik.
- [x] Slug unik; validasi field wajib §20.1.
- [x] Hapus media menghapus referensi DB (kebijakan hapus asset Cloudinary: definisikan di implementasi — optional hard delete).
