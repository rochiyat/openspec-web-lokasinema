# Capability: location-listing

Listing lokasi publik dengan pencarian, filter, dan peta embed.

## Requirements

### L1 — Query-driven listing

Sistem SHALL memuat daftar lokasi dari API publik dengan parameter query yang didukung PRD §15.4.

### L2 — URL sync

Sistem SHALL mencerminkan search dan filter pada URL sehingga refresh dan share link konsisten.

### L3 — Listing card

Setiap card SHALL menampilkan: cover image, title, short location label, average rating, review count, starting price, featured badge jika relevan.

### L4 — Map embed (visual)

Sistem SHALL menampilkan Google Maps embedded sebagai pendukung visual tanpa pencarian radius.

### L5 — Empty and loading states

Sistem SHALL menampilkan loading skeleton dan empty state yang jelas jika tidak ada lokasi cocok.

### L6 — Navigate to detail

Klik card SHALL membuka detail lokasi di `/locations/[slug]`.

## Scenarios

### L2

- **Given** user mengubah kota di filter
- **When** hasil diperbarui
- **Then** URL berisi parameter kota dan hasil sesuai filter

### L4

- **Given** lokasi memiliki koordinat atau alamat
- **When** listing dirender
- **Then** panel peta menampilkan embed atau fallback sesuai §24.4

### L5

- **Given** API mengembalikan array kosong
- **When** halaman selesai loading
- **Then** pesan empty state mengarahkan user mengubah filter (§24.1)
