# Design: foundation-app-routing-and-shared-types

## Arsitektur

- **Frontend**: Next.js App Router; segment `(public)` vs `admin` untuk pemisahan layout bila perlu.
- **Kontrak data**: Interface TypeScript mirror PRD appendix §32 (camelCase di FE, mapping di fetcher jika API snake_case).
- **API client**: Fungsi fetch terpusat dengan generic; siap dipakai SWR di change berikutnya (keys stabil = path + query).

## Keputusan

| Keputusan | Pilihan | Alasan |
|-----------|---------|--------|
| Router | App Router | PRD §16.2 |
| Tipe lokasi | Satu `LocationDto` rich | §32.1, dipakai listing & detail |
| Admin layout | Nested layout `/admin` | IA §12.2 |

## Boundary

- Change ini **tidak** menambah endpoint NestJS baru; hanya menyiapkan konsumen di FE.
- Environment: `NEXT_PUBLIC_API_URL` (atau nama setara) dokumentasikan di README openspec/tasks bila perlu.

## Non-goals (MVP PRD)

- Payment, owner dashboard, geospatial search, real-time chat, scheduling engine (§6.2, §5.3).

## Referensi PRD

- §12 Information Architecture, §16 Frontend Technical Requirements, §32 Appendix DTO.
