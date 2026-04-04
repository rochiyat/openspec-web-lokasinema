# Capability: app-foundation

Fondasi aplikasi web Lokasinema: routing, layout global, dan tipe bersama.

## ADDED Requirements

### Requirement: Public route skeleton

Sistem SHALL menyediakan rute publik yang dapat di-resolve sesuai Information Architecture PRD (`/`, `/locations`, `/locations/[slug]`, `/services`, `/services/[slug]`, `/about`, `/contact`, `/login`, `/register`, `/profile`).

#### Scenario: Locations list route resolves

- **GIVEN** pengguna membuka `/locations`
- **WHEN** halaman dimuat
- **THEN** route ter-resolve dan menampilkan placeholder atau konten minimal tanpa error build

#### Scenario: Public marketing routes exist

- **GIVEN** pengguna membuka `/about` atau `/contact`
- **WHEN** halaman dimuat
- **THEN** route ter-resolve dengan judul atau konten semantik minimal

### Requirement: Admin route skeleton

Sistem SHALL menyediakan rute admin dengan prefix `/admin` untuk modul CMS (placeholder hingga change admin terpisah).

#### Scenario: Admin root resolves

- **GIVEN** pengguna membuka `/admin`
- **WHEN** halaman dimuat
- **THEN** route admin ter-resolve tanpa error build

### Requirement: Shared types

Sistem SHALL mendefinisikan tipe TypeScript untuk entitas inti (Location, Service, Review, Inquiry, User) selaras field PRD §14 dan bentuk DTO §32.

#### Scenario: Location DTO import compiles

- **GIVEN** modul fitur lain mengimpor tipe lokasi yang didefinisikan di fondasi
- **WHEN** proyek di-compile dengan TypeScript
- **THEN** tidak ada bentuk kontradiktif duplikat untuk entitas yang sama dalam package yang sama

### Requirement: Typed API helper

Sistem SHALL menyediakan helper HTTP client bertipe untuk konsumsi API backend tanpa mengikat ke hook domain tertentu.

#### Scenario: Successful JSON parse

- **GIVEN** base URL API dikonfigurasi dan endpoint mengembalikan JSON valid
- **WHEN** helper dipanggil untuk GET endpoint
- **THEN** response di-parse ke generic type yang diminta

#### Scenario: HTTP error propagation

- **GIVEN** endpoint mengembalikan status error (misalnya 4xx/5xx)
- **WHEN** helper menyelesaikan permintaan
- **THEN** error terpropagasi terstruktur agar pemanggil dapat menangani tanpa silent failure

### Requirement: Visual frame

UI global SHALL mengikuti arah visual: frame gelap, konten utama pada surface terang (PRD §8.4).

#### Scenario: Root layout applies theme frame

- **GIVEN** pengguna membuka halaman publik manapun di bawah layout root
- **WHEN** halaman dirender
- **THEN** kerangka visual (navigasi/frame gelap dan area konten terang) konsisten diterapkan
