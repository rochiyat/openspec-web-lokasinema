# Capability: homepage

## Purpose

Homepage sebagai marketing dan entry discovery — disinkronkan dari change `homepage-discovery-entry`.

## Requirements

### Requirement: Keyword search entry

Homepage SHALL menyediakan form pencarian keyword yang mengarahkan ke `/locations` dengan query string.

#### Scenario: Search submit navigates to listing with query

- **GIVEN** pengguna berada di `/`
- **WHEN** pengguna mengisi keyword dan mengirim form pencarian
- **THEN** browser berada di `/locations` dengan parameter query yang mencerminkan keyword

### Requirement: Featured category shortcuts

Homepage SHALL menyediakan shortcut ke listing yang sudah terfilter (kategori unggulan atau ekuivalen).

#### Scenario: Category shortcut applies filter in URL

- **GIVEN** shortcut kategori ditampilkan di homepage
- **WHEN** pengguna mengklik shortcut tersebut
- **THEN** pengguna dibawa ke halaman listing dengan filter terkait tercermin di URL

### Requirement: Marketing sections

Homepage SHALL menampilkan section: tentang brand, production and services, trust logos, behind the scene gallery, CTA, dan footer sesuai PRD.

#### Scenario: Core marketing blocks are present

- **GIVEN** pengguna membuka `/`
- **WHEN** halaman homepage selesai dimuat
- **THEN** halaman memuat section brand, layanan/produksi, trust, galeri behind the scene, CTA, dan footer secara terbaca

### Requirement: Responsive layout

Homepage SHALL render responsif untuk mobile dan desktop.

#### Scenario: Layout remains usable across viewports

- **GIVEN** viewport mobile dan desktop
- **WHEN** halaman homepage dirender
- **THEN** hierarchy hero, CTA, dan footer tetap terbaca tanpa overlap kritis
