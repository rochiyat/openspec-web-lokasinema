# Capability: homepage

Homepage sebagai marketing dan entry discovery.

## Requirements

### H1 — Keyword search entry

Homepage SHALL menyediakan form pencarian keyword yang mengarahkan ke `/locations` dengan query string.

### H2 — Featured category shortcuts

Homepage SHALL menyediakan shortcut ke listing yang sudah terfilter (kategori unggulan atau ekuivalen).

### H3 — Marketing sections

Homepage SHALL menampilkan section: tentang brand, production and services, trust logos, behind the scene gallery, CTA, dan footer sesuai PRD.

### H4 — Responsive layout

Homepage SHALL render responsif untuk mobile dan desktop.

## Scenarios

### H1

- **Given** user berada di `/`
- **When** user mengisi keyword dan submit
- **Then** browser berada di `/locations` dengan parameter query yang mencerminkan keyword

### H2

- **Given** shortcut kategori "X" ditampilkan
- **When** user mengklik shortcut
- **Then** user dibawa ke halaman listing dengan filter terkait tercermin di URL

### H4

- **Given** viewport mobile dan desktop
- **When** halaman dirender
- **Then** hierarchy hero, CTA, dan footer tetap terbaca tanpa overlap kritis
