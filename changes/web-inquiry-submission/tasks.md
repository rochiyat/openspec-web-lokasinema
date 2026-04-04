# Tasks: web-inquiry-submission

1. Backend: module inquiries, entity, migration, POST handler dengan guard JWT.
2. Validasi server: rules §20.3 (location_id wajib untuk location_inquiry).
3. Rate limiter pada route POST.
4. Frontend: form RHF+Zod, prefill nama/email dari `me` jika ada.
5. Integrasi dari halaman detail lokasi (route dedikasi `/locations/[slug]/inquire` atau modal).
6. Uji: guest blocked; user success; invalid payload errors.
7. (Minimal) Admin list inquiries + PATCH status jika belum ada di change lain.
