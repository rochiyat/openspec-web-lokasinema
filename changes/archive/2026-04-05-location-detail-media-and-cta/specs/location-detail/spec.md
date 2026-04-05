# Capability: location-detail

Detail lokasi publik: media, spesifikasi, dan CTA kontak.

## ADDED Requirements

### Requirement: Published location detail data

Halaman detail SHALL menampilkan data lokasi published: title, slug path (tersaji eksplisit dan/atau di breadcrumb), ringkasan `shortDescription` bila tersedia dari API, address/city/province, starting price, currency, description, categories, tags, specs, facilities, media, optional YouTube.

#### Scenario: Detail page renders full published payload

- **GIVEN** API mengembalikan lokasi published dengan field detail lengkap
- **WHEN** halaman detail lokasi selesai dimuat
- **THEN** judul, path slug, alamat/kota/provinsi, harga mulai, mata uang, deskripsi, kategori, tag, spesifikasi, fasilitas, dan media ditampilkan sesuai data

#### Scenario: Short description when present

- **GIVEN** lokasi published memiliki `shortDescription` tidak kosong
- **WHEN** halaman detail dirender
- **THEN** ringkasan singkat ditampilkan di bawah judul

### Requirement: Image gallery

Sistem SHALL menampilkan galeri dengan cover dan thumbnail lain; optimasi gambar (lazy, responsive).

#### Scenario: Gallery shows cover and additional media

- **GIVEN** lokasi memiliki cover dan set media tambahan
- **WHEN** pengguna melihat area galeri
- **THEN** cover dan thumbnail lain dirender dengan lazy loading dan sumber gambar responsif

### Requirement: Conditional YouTube embed

YouTube iframe SHALL hanya dirender jika URL embed valid dan tersedia.

#### Scenario: No iframe when YouTube URL absent

- **GIVEN** lokasi tanpa YouTube URL
- **WHEN** halaman dirender
- **THEN** tidak ada iframe video

#### Scenario: Iframe when valid embed URL present

- **GIVEN** lokasi memiliki URL embed YouTube yang valid
- **WHEN** halaman dirender
- **THEN** iframe video ditampilkan sesuai URL tersebut

### Requirement: WhatsApp contact CTA

Tombol WhatsApp SHALL membuka deep link dengan pesan berisi minimal: judul lokasi, URL halaman, nama/placeholder user (PRD §13.6), ketika nomor WhatsApp bisnis telah dikonfigurasi di environment aplikasi.

#### Scenario: WhatsApp opens with location context

- **GIVEN** pengguna di halaman detail lokasi "Studio A" dan konfigurasi nomor WhatsApp tersedia
- **WHEN** pengguna menekan Hubungi WhatsApp
- **THEN** aplikasi WhatsApp/web dibuka dengan teks yang menyebut "Studio A" dan link halaman

### Requirement: Web message CTA authentication gate

Tombol untuk kirim pesan via web SHALL memastikan hanya user terautentikasi yang melanjutkan; guest diarahkan login.

#### Scenario: Guest redirected to auth for web message

- **GIVEN** guest tidak login
- **WHEN** pengguna menekan Kirim Pesan
- **THEN** pengguna diarahkan ke alur autentikasi dengan return URL ke konteks lokasi

### Requirement: Related locations

Sistem SHALL menampilkan blok lokasi terkait menggunakan heuristik dari API listing publik: lokasi lain di kota yang sama dengan lokasi detail (mengacu filter `city` pada `GET /api/locations`), selalu mengecualikan slug lokasi yang sedang dibuka, ketika kota lokasi tersedia dan listing mengembalikan item lain.

#### Scenario: Related block from listing heuristic

- **GIVEN** lokasi detail memiliki kota dan respons `GET /api/locations` dengan parameter kota tersebut memuat lokasi lain selain slug saat ini
- **WHEN** halaman detail selesai dimuat
- **THEN** blok lokasi terkait menampilkan kartu navigasi ke lokasi lain di kota tersebut
