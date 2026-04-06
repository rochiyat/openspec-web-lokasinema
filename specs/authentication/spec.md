# Capability: authentication

## Purpose

Autentikasi pengguna, JWT Bearer, peran `user`/`admin`, guard endpoint dan rute admin — disinkronkan dari change `auth-and-role-guard`.

## Requirements

### Requirement: Register and login

Sistem SHALL mengizinkan registrasi dan login dengan kredensial aman (password hashed).

#### Scenario: Registrasi akun baru

- **GIVEN** email belum terdaftar
- **WHEN** user menyelesaikan registrasi valid
- **THEN** akun tercipta dan user dapat login

### Requirement: Session identity

Sistem SHALL menyediakan endpoint `GET /api/me` untuk profil pengguna terautentikasi.

#### Scenario: Profil terautentikasi

- **GIVEN** user telah login dengan sesi/token valid
- **WHEN** client memanggil `GET /api/me`
- **THEN** response berisi identitas profil pengguna yang sesuai

### Requirement: Logout

Sistem SHALL mengizinkan pengguna mengakhiri sesi (invalidate token/session sesuai implementasi).

#### Scenario: Sesi berakhir setelah logout

- **GIVEN** user sedang terautentikasi
- **WHEN** user meminta logout
- **THEN** sesi/token tidak lagi valid untuk akses terproteksi

### Requirement: Roles

Sistem SHALL mendukung peran `user` dan `admin` dan menegakkannya pada endpoint sensitif.

#### Scenario: User biasa ditolak dari endpoint admin

- **GIVEN** user dengan role `user`
- **WHEN** user memanggil endpoint admin
- **THEN** request ditolak dengan status akses ditolak

### Requirement: Guest versus authenticated access rules

Guest SHALL dapat browsing dan menggunakan WhatsApp CTA; guest SHALL NOT mengirim web form inquiry atau submit review (PRD §18).

#### Scenario: Guest ditolak untuk aksi yang memerlukan login

- **GIVEN** guest tanpa sesi
- **WHEN** guest mencoba submit resource yang memerlukan login (kontrak API)
- **THEN** server menolak dengan 401/403

### Requirement: Admin route protection

Rute admin SHALL hanya dapat diakses oleh role admin.

#### Scenario: Non-admin tidak mengakses rute admin

- **GIVEN** pengguna dengan role bukan `admin`
- **WHEN** pengguna membuka rute di bawah `/admin`
- **THEN** akses diblokir sesuai kebijakan aplikasi (redirect atau 403)
