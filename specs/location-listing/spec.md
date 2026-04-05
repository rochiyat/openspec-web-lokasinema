# Capability: location-listing

## Purpose

Listing lokasi publik dengan pencarian, filter, dan peta embed — disinkronkan dari change `location-listing-search-filter-map`.

## Requirements

### Requirement: Query-driven listing

Sistem SHALL memuat daftar lokasi dari API publik dengan parameter query yang didukung PRD §15.4 (`q`, `city`, `category`, `tag`, `featured`, `minPrice`, `maxPrice`, `sort`, `page`, `limit`).

#### Scenario: Listing reflects API query parameters

- **GIVEN** pengguna membuka halaman listing dengan query string yang valid
- **WHEN** permintaan data ke API publik lokasi selesai
- **THEN** daftar lokasi yang ditampilkan sesuai parameter query yang dikirim

### Requirement: URL sync for search and filter

Sistem SHALL mencerminkan search dan filter pada URL sehingga refresh dan share link konsisten.

#### Scenario: Filter change updates URL

- **GIVEN** pengguna mengubah kota di filter
- **WHEN** hasil listing diperbarui
- **THEN** URL berisi parameter kota dan hasil sesuai filter

### Requirement: Listing card content

Setiap card SHALL menampilkan: cover image, title, label lokasi singkat (`shortDescription` jika ada, selain itu kota + provinsi), average rating, review count, starting price, featured badge jika relevan.

#### Scenario: Card shows required fields when data exists

- **GIVEN** API mengembalikan lokasi published dengan field card lengkap
- **WHEN** grid listing dirender
- **THEN** setiap card memuat cover, judul, label lokasi singkat, rating rata-rata, jumlah review, harga mulai, dan badge featured bila lokasi featured

### Requirement: Map embed visual-only

Sistem SHALL menampilkan Google Maps embedded sebagai pendukung visual tanpa pencarian radius.

#### Scenario: Map or fallback per location data

- **GIVEN** lokasi memiliki koordinat atau alamat
- **WHEN** halaman listing dirender
- **THEN** panel peta menampilkan embed atau fallback sesuai PRD §24.4

### Requirement: Empty and loading states

Sistem SHALL menampilkan loading skeleton dan empty state yang jelas jika tidak ada lokasi cocok.

#### Scenario: Empty state when no results

- **GIVEN** API mengembalikan array kosong untuk filter saat ini
- **WHEN** halaman selesai loading
- **THEN** pesan empty state mengarahkan pengguna mengubah filter (PRD §24.1)

#### Scenario: Loading skeleton while fetching

- **GIVEN** permintaan listing masih berlangsung
- **WHEN** pengguna melihat area daftar
- **THEN** skeleton loading ditampilkan hingga data tersedia atau error ditangani

### Requirement: Navigate to location detail

Klik card SHALL membuka detail lokasi di `/locations/[slug]`.

#### Scenario: Card click opens detail route

- **GIVEN** grid listing menampilkan card lokasi dengan slug
- **WHEN** pengguna mengklik card tersebut
- **THEN** navigasi ke `/locations/[slug]` untuk slug lokasi yang dipilih
