# Proposal: auth-and-role-guard

## Objective

Autentikasi end-to-end: register, login, logout, profil minimal (`GET/PATCH /api/me`), JWT (atau session) aman, role `user` vs `admin`, guard untuk endpoint dan rute admin — selaras PRD §13.5, §15.2–§15.3, §19.2.

## Scope In

- Alur UI `/login`, `/register`, `/profile` (dasar).
- Penyimpanan token/session; integrasi header `Authorization` di `lib/api`.
- Backend: auth module (NestJS), hash password aman, issue JWT, rate limit login (PRD §19.2).
- Role-based access: guest browse; user untuk form web & review; admin untuk CMS routes.
- Middleware atau layout guard untuk `/admin/**`.

## Scope Out

- Owner dashboard pihak ketiga (non-goal).
- OAuth sosial (hanya jika PRD tidak mewajibkan — tidak ada di PRD, maka out).

## Dependencies

- **foundation-app-routing-and-shared-types**

## Done Criteria (konkret)

- [x] User dapat register, login, logout.
- [x] `GET /api/me` mengembalikan profil untuk user terautentikasi.
- [x] Request ke `POST /api/inquiries` tanpa auth ditolak (401) — endpoint stub terproteksi JWT; penyimpanan data pada change web-inquiry-submission.
- [x] Akses `/admin` tanpa role admin ditolak (redirect atau 403).
- [x] Rate limiting aktif pada login (dan sesuai kebijakan untuk submit inquiry/review di change terkait).
