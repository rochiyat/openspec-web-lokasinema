# Proposal: homepage-discovery-entry

## Objective

Mengimplementasikan homepage sebagai entry discovery dan marketing: hero, search keyword, shortcut kategori/lokasi unggulan, section brand, production & services, trust logos, behind-the-scene gallery, CTA, dan footer — dengan perilaku redirect ke listing sesuai PRD §13.1.

## Scope In

- Hero (heading, subheading, search form keyword).
- Search mengarah ke `/locations` dengan query string `q` (dan parameter lain bila relevan).
- Shortcut kategori/lokasi unggulan → `/locations` dengan filter URL (category/featured sesuai kontrak tim).
- Section: tentang Lokasinema, production and services (link ke `/services` atau anchor), trust logos, behind the scene gallery, CTA, footer.
- Responsif (PRD §13.1 AC).

## Scope Out

- Implementasi filter penuh di halaman listing (change terpisah).
- Data dinamis dari CMS untuk semua blok marketing jika belum ada API — boleh static/JSON sementara **hanya** jika tidak mengubah acceptance PRD; preferensi: data dari API jika sudah tersedia di change lain.

## Dependencies

- **foundation-app-routing-and-shared-types**: route `/`, layout, `lib/api` jika hero mengambil data.

## Done Criteria (konkret)

- [ ] Submit search dari homepage membawa user ke `/locations` dengan query tercermin di URL.
- [ ] Klik shortcut kategori unggulan membuka listing dengan state filter terlihat di URL.
- [ ] Section utama (hero, CTA, footer) tampil responsif mobile/desktop.
- [ ] Link ke `/services` dan entry discovery lain tidak broken.
