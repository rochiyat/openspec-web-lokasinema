# Proposal: location-listing-search-filter-map

## Objective

Halaman listing lokasi publik: search, filter (keyword, kota, kategori, tag, featured, min/max price, sort), grid card, pagination/load more, Google Maps embed visual-only, empty/loading state — dengan state filter **tersinkron URL** (PRD §13.2, §16.2).

## Scope In

- Konsumsi data listing lewat **`GET /api/locations` pada origin Next.js** (App Router Route Handler) yang mem-proxy query string ke backend Nest di `NEXT_PUBLIC_API_URL/api/locations`, agar pemanggilan dari browser tetap same-origin (hindari CORS, pola BFF ringan).
- Query yang didukung: `q`, `city`, `category`, `tag`, `featured`, `minPrice`, `maxPrice`, `sort`, `page`, `limit` (PRD §15.4).
- UI: search input, chips/side filter, sorting, grid card dengan field: cover, title, label lokasi singkat, rating avg, review count, starting price, badge featured (PRD §13.2).
- Panel Google Maps embedded (visual; tanpa radius search) (PRD §16.5, §5.3).
- SWR dengan key stabil dari pathname + query (PRD §16.4).
- Empty state copy sesuai §24.1.

## Scope Out

- Halaman detail lokasi penuh (change `location-detail-media-and-cta`).
- Advanced geospatial search (non-goal PRD).

## Dependencies

- **foundation-app-routing-and-shared-types**: types, api helper, route `/locations`.
- **Backend**: endpoint publik `GET /api/locations` mengembalikan data published saja (`is_published=true`) dan field card (bisa di scope implementasi bersamaan di repo backend dalam slice yang sama).

## Done Criteria (konkret)

- [ ] Setiap perubahan filter/search memperbarui URL dan hasil listing.
- [ ] Refresh halaman mempertahankan filter dari URL.
- [ ] Card memuat cover, title, rating, review count, starting price, featured bila ada.
- [ ] Maps embed tampil sebagai dukungan visual (atau fallback alamat/koordinat per PRD §24.4).
- [ ] Empty state tampil jika tidak ada hasil.
- [ ] Klik card navigasi ke `/locations/[slug]`.
