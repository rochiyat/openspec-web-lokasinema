# Tasks: foundation-app-routing-and-shared-types

Environment: set `NEXT_PUBLIC_API_URL` di `frontend/.env.local` (lihat `frontend/.env.example`).

- [x] Inisialisasi/verifikasi project Next.js + TS + Tailwind sesuai monorepo repo.
- [x] Buat struktur `app/(public)/...` dan `app/admin/...` dengan `page.tsx` placeholder per rute PRD §12.
- [x] Tambah `layout.tsx` root: meta default, font, wrapper tema gelap/putih.
- [x] Definisikan `types/location.ts`, `service.ts`, `review.ts`, `inquiry.ts`, `user.ts` dari PRD §14 & §32.
- [x] Implementasi `lib/api.ts`: `getJson<T>`, base URL env, handling HTTP error.
- [x] Halaman placeholder `about`, `contact` dengan judul semantik untuk uji navigasi.
- [x] `not-found.tsx` global atau per-segment untuk slug tidak valid (stub).
- [x] Dokumentasikan env wajib: `frontend/.env.example` + catatan di task ini.

**Catatan**: Implementasi di folder `frontend/`; change OpenSpec lain tidak diubah.
