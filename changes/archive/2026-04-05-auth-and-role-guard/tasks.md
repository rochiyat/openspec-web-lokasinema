# Tasks: auth-and-role-guard

- [x] Backend: entity User, hash password, login/register endpoints, JWT strategy.
- [x] Backend: `GET/PATCH /api/me` dengan guard JWT.
- [x] Frontend: halaman login/register dengan validasi.
- [x] Frontend: simpan token aman (httpOnly cookie disarankan atau localStorage sesuai keputusan security review).
- [x] Perluas `lib/api` untuk attach auth header.
- [x] Admin route guard + fallback UI.
- [x] Uji negatif: akses admin sebagai user biasa; API protected tanpa token.
