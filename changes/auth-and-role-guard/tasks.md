# Tasks: auth-and-role-guard

1. Backend: entity User, hash password, login/register endpoints, JWT strategy.
2. Backend: `GET/PATCH /api/me` dengan guard JWT.
3. Frontend: halaman login/register dengan validasi.
4. Frontend: simpan token aman (httpOnly cookie disarankan atau localStorage sesuai keputusan security review).
5. Perluas `lib/api` untuk attach auth header.
6. Admin route guard + fallback UI.
7. Uji negatif: akses admin sebagai user biasa; API protected tanpa token.
