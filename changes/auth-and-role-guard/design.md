# Design: auth-and-role-guard

## Token

- JWT di header Bearer; refresh policy sesuai keputusan tim (document di implementasi).

## Frontend

- Context atau hook `useAuth` (PRD §16.3) dengan sync ke SWR `me`.
- Form login/register: React Hook Form + Zod disarankan PRD §16.1.

## Backend

- Guards NestJS: `JwtAuthGuard`, `RolesGuard` untuk admin.
- Enum role: `user`, `admin` (PRD §26.3).

## Referensi PRD

- §13.5, §14.1 Users, §15.2–§15.3, §18, §19.2.
