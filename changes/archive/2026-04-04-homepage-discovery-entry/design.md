# Design: homepage-discovery-entry

## Alur

1. User landing `/` → melihat hero + search.
2. User submit keyword → `router.push` atau `<form action>` ke `/locations?q=...`.
3. User klik chip kategori → `/locations?category=<slug>` (atau kontrak query sama dengan listing change).

## Data

- Kategori unggulan: `GET /api/categories` (PRD §15.1) bila tersedia — di frontend dipanggil sebagai path `/api/categories` relatif ke `NEXT_PUBLIC_API_URL` (base URL tanpa suffix `/api`; jangan menggandakan prefix di env).
- Fallback static (`FALLBACK_FEATURED_CATEGORIES` di `src/lib/categories.ts`) hanya bila env kosong atau request gagal; tidak mengganti AC produksi saat API sudah hidup.

## Boundary

- Tidak termasuk peta, card listing, atau pagination (change `location-listing-search-filter-map`).

## Referensi PRD

- §8.1 Homepage, §13.1, §21.1, Phase 1 §27.
