# Proposal: seo-metadata-sitemap-and-analytics

## Objective

SEO dasar Next.js: dynamic metadata + Open Graph untuk detail lokasi dan layanan, canonical URL, sitemap, serta hooks analytics opsional (event: search, detail view, WhatsApp click, inquiry/booking submit) sesuai PRD §19.4–§19.5.

## Scope In

- `generateMetadata` (atau ekuivalen) untuk `/locations/[slug]` dan `/services/[slug]` dengan title/description dari entitas, human-readable slug.
- Open Graph tags dasar.
- Canonical URL per halaman konten.
- `sitemap.xml` mencakup URL lokasi dan layanan published (dan halaman statis utama).
- Instrumentasi analytics recommended optional: event tracking sesuai §19.5 (boleh no-op jika env tidak set).

## Scope Out

- Rekomendasi konten AI, structured data kompleks (boleh tambah JSON-LD sederhana jika cepat — tidak wajib di MVP PRD).

## Dependencies

- **location-detail-media-and-cta** (slug pages exist)
- **services-list-detail-and-booking-request** (service pages exist)
- Data published tersedia untuk generate sitemap

## Done Criteria (konkret)

- [ ] Setiap lokasi published memiliki title/meta unik di view source.
- [ ] OG tags tersaji untuk share preview dasar.
- [ ] Canonical mengarah ke URL produksi yang benar.
- [ ] Sitemap memuat entri lokasi & service published.
- [ ] Event analytics terpanggil pada aksi utama (jika provider dikonfigurasi) atau dokumentasi no-op.
