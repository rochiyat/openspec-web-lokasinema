# Capability: authentication

Autentikasi pengguna dan pembatasan peran.

## Requirements

### A1 — Register and login

Sistem SHALL mengizinkan registrasi dan login dengan kredensial aman (password hashed).

### A2 — Session identity

Sistem SHALL menyediakan endpoint `GET /api/me` untuk profil pengguna terautentikasi.

### A3 — Logout

Sistem SHALL mengizinkan pengguna mengakhiri sesi (invalidate token/session sesuai implementasi).

### A4 — Roles

Sistem SHALL mendukung peran `user` dan `admin` dan menegakkannya pada endpoint sensitif.

### A5 — Business rules guest vs user

Guest SHALL dapat browsing dan menggunakan WhatsApp CTA; guest SHALL NOT mengirim web form inquiry atau submit review (PRD §18).

### A6 — Admin route protection

Rute admin SHALL hanya dapat diakses oleh role admin.

## Scenarios

### A1

- **Given** email belum terdaftar
- **When** user menyelesaikan registrasi valid
- **Then** akun tercipta dan user dapat login

### A4

- **Given** user dengan role `user`
- **When** user memanggil endpoint admin
- **Then** request ditolak dengan status akses ditolak

### A5

- **Given** guest
- **When** guest mencoba submit resource yang memerlukan login (kontrak API)
- **Then** server menolak dengan 401/403
