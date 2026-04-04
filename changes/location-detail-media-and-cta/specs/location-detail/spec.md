# Capability: location-detail

Detail lokasi publik: media, spesifikasi, dan CTA kontak.

## Requirements

### D1 — Detail data

Halaman detail SHALL menampilkan data lokasi published: title, slug path, address/city/province, starting price, currency, description, categories, tags, specs, facilities, media, optional YouTube.

### D2 — Gallery

Sistem SHALL menampilkan galeri dengan cover dan thumbnail lain; optimasi gambar (lazy, responsive).

### D3 — YouTube conditional

YouTube iframe SHALL hanya dirender jika URL embed valid dan tersedia.

### D4 — WhatsApp CTA

Tombol WhatsApp SHALL membuka deep link dengan pesan berisi minimal: judul lokasi, URL halaman, nama/placeholder user (PRD §13.6).

### D5 — Web form CTA gate

Tombol untuk kirim pesan via web SHALL memastikan hanya user terautentikasi yang melanjutkan; guest diarahkan login.

### D6 — Related locations

Sistem SHOULD menampilkan lokasi terkait untuk eksplorasi lanjutan.

## Scenarios

### D4

- **Given** user di halaman detail lokasi "Studio A"
- **When** user menekan Hubungi WhatsApp
- **Then** aplikasi WhatsApp/web dibuka dengan teks yang menyebut "Studio A" dan link halaman

### D5

- **Given** guest tidak login
- **When** user menekan Kirim Pesan via Web
- **Then** user diarahkan ke alur autentikasi dengan return URL ke konteks lokasi

### D3

- **Given** lokasi tanpa YouTube URL
- **When** halaman dirender
- **Then** tidak ada iframe video
