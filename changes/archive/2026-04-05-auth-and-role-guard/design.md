# Design: auth-and-role-guard

## Token

- JWT di header Bearer; refresh policy sesuai keputusan tim (document di implementasi).

### Logout (JWT stateless)

- **Revoke di praktik:** hapus cookie httpOnly di BFF Next (`POST /api/auth/logout`) sehingga browser tidak lagi mengirim JWT.
- **Batasan:** token yang sudah dikeluarkan tetap **cryptographically valid** sampai `exp` (tidak ada denylist server). Mitigasi lanjutan (refresh token pendek, blacklist, rotasi) opsional di change berikutnya.

## Frontend

- Context atau hook `useAuth` (PRD §16.3) dengan sync ke SWR `me`.
- Form login/register: React Hook Form + Zod disarankan PRD §16.1.

## Backend

- Guards NestJS: `JwtAuthGuard` (kelas di `auth/guards/jwt-auth.guard.ts`), `RolesGuard` untuk admin.
- Enum role: `user`, `admin` (PRD §26.3).

### Bootstrap admin (dev)

- **User pertama** yang berhasil `register` mendapat role `admin`; pendaftar berikutnya `user`. Ini memudahkan lingkungan dev/staging — di production pertimbangkan seed terpisah atau nonaktifkan kebijakan ini jika tidak diinginkan.

## Referensi PRD

- §13.5, §14.1 Users, §15.2–§15.3, §18, §19.2.
