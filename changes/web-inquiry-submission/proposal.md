# Proposal: web-inquiry-submission

## Objective

Alur **location inquiry** via form web: hanya user login, field sesuai PRD §13.6, validasi §20.3, `POST /api/inquiries` dengan `type=location_inquiry`, penyimpanan DB, feedback sukses/gagal — plus tampilan admin melihat inquiry (read + status) dapat menjadi bagian slice yang sama atau follow-up minimal di task.

## Scope In

- Form fields: full_name, email, phone, project_name, shoot_date, duration, crew_size, message (+ `location_id` wajib untuk tipe ini).
- Autentikasi wajib pada submit (PRD §13.6 AC).
- Validasi client (Zod) + server.
- Backend: entity Inquiry, enum type, status default `new`, `source_channel=web_form`.
- Rate limit submit (PRD §19.2).
- UI: halaman atau modal dari konteks detail lokasi setelah login.

## Scope Out

- **Service booking** form (`type=service_booking`) — termasuk di change `services-list-detail-and-booking-request`.
- WhatsApp channel (sudah ada di detail via CTA terpisah).
- Payment, scheduling.

## Dependencies

- **auth-and-role-guard** (wajib login).
- **location-detail-media-and-cta** (konteks lokasi, slug → id; bisa kirim locationId dari halaman detail).

## Done Criteria (konkret)

- [ ] User terautentikasi dapat mengirim location inquiry; guest tidak.
- [ ] Validasi field wajib dan email/phone sesuai aturan tim/PRD.
- [ ] Record tersimpan dengan `location_id`, `type=location_inquiry`, status `new`.
- [ ] Error submit menampilkan pesan jelas; input dipertahankan jika aman (PRD §24.2).
- [ ] (Opsional same slice) Admin dapat melihat daftar inquiry di `/admin/inquiries` read-only minimal.
