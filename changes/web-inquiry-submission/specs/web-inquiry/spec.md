# Capability: web-inquiry

Pengiriman inquiry lokasi melalui form web (terautentikasi).

## Requirements

### I1 — Authenticated submission

Hanya pengguna terautentikasi SHALL dapat mengirim inquiry via form web.

### I2 — Location inquiry payload

Request SHALL memiliki `type=location_inquiry` dan `location_id` wajib; field form sesuai PRD §13.6.

### I3 — Validation

Input SHALL divalidasi (nama, email, phone, message wajib; format email/phone).

### I4 — Persistence

Inquiry SHALL disimpan di database dengan status awal dan `source_channel=web_form`.

### I5 — Rate limiting

Endpoint submit SHALL memiliki rate limit untuk mitigasi spam (PRD §19.2).

### I6 — Error handling

Gagal submit SHALL menampilkan pesan jelas dan mempertahankan input bila aman (PRD §24.2).

## Scenarios

### I1

- **Given** guest tidak memiliki token
- **When** guest mencoba POST inquiry
- **Then** server menolak dengan 401

### I2

- **Given** user login di halaman lokasi X
- **When** user mengirim form lengkap
- **Then** record inquiry terkait `location_id` lokasi X tersimpan

### I4

- **Given** submit sukses
- **When** admin membuka daftar inquiry
- **Then** entri baru terlihat dengan status `new`
