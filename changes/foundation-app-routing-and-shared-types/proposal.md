# Proposal: foundation-app-routing-and-shared-types

## Objective

Menyediakan fondasi aplikasi Lokasinema: struktur routing publik/admin sesuai IA PRD, konvensi App Router, kontrak tipe/DTO bersama (selaras appendix PRD), kerangka `lib/api` + fetcher bertipe, dan layout global (navbar/footer gelap-putih) tanpa mengimplementasikan fitur bisnis penuh.

## Scope In

- Route groups/skeleton untuk rute publik: `/`, `/locations`, `/locations/[slug]`, `/services`, `/services/[slug]`, `/about`, `/contact`, `/login`, `/register`, `/profile` (placeholder halaman).
- Skeleton rute admin: `/admin` dan subpath utama (placeholder).
- Modul `types/` atau ekuivalen: bentuk DTO inti (`Location`, `Service`, `Review`, `Inquiry`, `User`) selaras PRD §14 & §32.
- `lib/api.ts`: base URL, helper fetch bertipe, pola error response konsisten.
- Layout global, tema visual dasar (gelap + surface putih untuk konten) sesuai §8.4.
- Konfigurasi konsisten: TypeScript, Tailwind, struktur folder disarankan §16.3.

## Scope Out

- Data nyata dari database, SWR hooks spesifik domain, Google Maps, Cloudinary, formulir lengkap, auth JWT, SEO dinamis, konten homepage/listing/detail.

## Dependencies

- Tidak ada change OpenSpec lain (ini adalah change pertama).

## Risiko / Asumsi

- Stack tetap Next.js (App Router preferred), NestJS terpisah; base API URL dari env.
- Placeholder page boleh minimal selama navigasi dan struktur folder stabil.

## Done Criteria (konkret)

- [x] Semua path di §12.1 dan §12.2 terwakili oleh route file (boleh `loading`/`not-found` dasar).
- [x] Tipe/DTO inti terdokumentasi di codebase dan dapat diimpor oleh change berikutnya.
- [x] `lib/api` menyediakan minimal satu contoh pemanggilan bertipe (mis. health atau stub) tanpa logika bisnis lokasi.
- [x] Build frontend lolos tanpa error TypeScript terkait fondasi ini.
