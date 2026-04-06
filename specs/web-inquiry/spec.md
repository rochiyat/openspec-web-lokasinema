# Capability: web-inquiry

## Purpose

Pengiriman inquiry lokasi melalui form web untuk pengguna terautentikasi, penyimpanan DB, rate limit, dan admin melihat/mengubah status — disinkronkan dari change `web-inquiry-submission`.

## Requirements

### Requirement: Authenticated submission

Hanya pengguna terautentikasi SHALL dapat mengirim inquiry via form web.

#### Scenario: Guest ditolak submit inquiry

- **GIVEN** guest tidak memiliki token
- **WHEN** guest mencoba POST inquiry
- **THEN** server menolak dengan 401

### Requirement: Location inquiry payload

Request SHALL memiliki `type=location_inquiry` dan `location_id` wajib; field form sesuai PRD §13.6.

#### Scenario: Submit lengkap tersimpan per lokasi

- **GIVEN** user login di halaman lokasi X
- **WHEN** user mengirim form lengkap
- **THEN** record inquiry terkait `location_id` lokasi X tersimpan

### Requirement: Validation

Input SHALL divalidasi (nama, email, phone, message wajib; format email/phone).

#### Scenario: Payload tidak valid ditolak

- **GIVEN** user terautentikasi
- **WHEN** user mengirim inquiry tanpa field wajib atau format email/phone tidak valid
- **THEN** server menolak dengan pesan validasi yang jelas

### Requirement: Persistence

Inquiry SHALL disimpan di database dengan status awal dan `source_channel=web_form`.

#### Scenario: Entri baru terlihat di admin

- **GIVEN** submit sukses
- **WHEN** admin membuka daftar inquiry
- **THEN** entri baru terlihat dengan status `new`

### Requirement: Rate limiting

Endpoint submit SHALL memiliki rate limit untuk mitigasi spam (PRD §19.2).

#### Scenario: Burst submit dibatasi

- **GIVEN** klien mengirim banyak request submit dalam jendela singkat
- **WHEN** batas rate tercapai
- **THEN** request berikutnya ditolak atau di-throttle sesuai kebijakan rate limit

### Requirement: Error handling

Gagal submit SHALL menampilkan pesan jelas dan mempertahankan input bila aman (PRD §24.2).

#### Scenario: Kegagalan jaringan tidak menghapus input aman

- **GIVEN** user mengisi form inquiry
- **WHEN** submit gagal karena error server atau jaringan
- **THEN** UI menampilkan pesan error yang jelas dan mempertahankan nilai input yang aman untuk diperbaiki user
