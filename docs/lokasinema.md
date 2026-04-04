---
title: "Lokasinema PRD"
version: "1.0"
status: "Draft for implementation"
last_updated: "2026-04-03"
product_name: "Lokasinema"
product_type: "Location discovery, booking, and lead generation platform for shooting locations and production services"
primary_stack:
  frontend: ["Next.js", "TypeScript", "Tailwind CSS", "SWR", "Google Maps Embed"]
  backend: ["NestJS", "TypeORM", "PostgreSQL"]
  media: ["Cloudinary for optimized images", "YouTube embedded links for video"]
  contact: ["WhatsApp deep link", "Web inquiry form"]
intended_audience:
  - product_manager
  - ui_ux_designer
  - frontend_engineer
  - backend_engineer
  - qa_engineer
  - ai_coding_agent
ai_friendly_notes:
  - "This PRD is intentionally structured with explicit entities, flows, acceptance criteria, and implementation constraints."
  - "Use this file as the single source of truth for MVP scope unless a later version supersedes it."
  - "When ambiguity exists, follow the business rules and acceptance criteria sections before making assumptions."
---

# 1. Executive Summary

Lokasinema adalah platform web untuk membantu user menemukan lokasi shooting, melihat detail teknis lokasi, mengecek harga mulai dari (starting price), melihat galeri foto/video, menemukan layanan produksi tambahan, dan menghubungi admin melalui WhatsApp atau form web. Produk ini menggabungkan fungsi marketing website, listing marketplace, detail lokasi, booking services, dan lead generation.

Produk ini bukan e-commerce checkout penuh pada fase awal. Fokus utamanya adalah:
- discovery lokasi
- evaluasi lokasi
- inquiry dan lead generation
- booking request
- trust building melalui landing page dan detail konten

# 2. Product Vision

Menyediakan platform pencarian lokasi shooting dan layanan produksi yang cepat, informatif, visual, dan mudah dihubungi untuk production house, brand team, creator, dan tim kreatif.

# 3. Product Goals

## 3.1 Business Goals
- Meningkatkan jumlah inquiry lokasi dan layanan produksi.
- Membangun database lokasi shooting yang terstruktur.
- Menjadi landing page dan katalog resmi Lokasinema.
- Membuka peluang monetisasi dari booking, layanan produksi, dan listing unggulan di masa depan.

## 3.2 User Goals
- Menemukan lokasi yang sesuai dengan cepat.
- Melihat detail teknis lokasi sebelum survey.
- Menghubungi admin atau tim Lokasinema dengan mudah.
- Mengajukan pesan via web atau WhatsApp.
- Memesan layanan produksi yang relevan.
- Memberi review dan melihat review sebagai bahan pertimbangan.

# 4. Problem Statement

Pencarian lokasi shooting sering dilakukan secara manual melalui jaringan personal, chat, atau rekomendasi informal. Informasi lokasi biasanya tidak seragam, sulit dibandingkan, minim detail teknis, dan lambat untuk di-follow up.

Lokasinema menyederhanakan proses menjadi:
- search
- filter
- compare
- review details
- contact via WhatsApp or form
- booking request

# 5. Target Users

## 5.1 Primary Users
- Production house
- Videographer
- Filmmaker
- Content creator
- Brand marketing team
- Event organizer
- Photographer

## 5.2 Internal Users
- Admin Lokasinema
- Content operator
- Customer support / sales admin

## 5.3 Non-Goals for MVP
- Tidak ada dashboard owner pihak ketiga.
- Tidak ada booking calendar real-time tingkat lanjut.
- Tidak ada pembayaran online wajib pada fase awal.
- Map tidak digunakan untuk pencarian radius canggih; hanya visual display.

# 6. Product Scope

## 6.1 In Scope for MVP
- Landing page / homepage
- Listing lokasi
- Detail lokasi
- Search dan filter lokasi
- Google Maps embed pada halaman relevan
- Galeri foto lokasi
- Video lokasi via YouTube embedded links
- Form inquiry web
- Redirect atau open WhatsApp dengan data inquiry yang sesuai
- Authentication untuk mengirim pesan via web
- Rating dan review oleh user dan admin
- Listing layanan produksi dan booking request layanan
- Admin panel untuk CRUD lokasi, services, categories, inquiries, dan reviews
- Media upload ke Cloudinary
- SEO metadata dasar

## 6.2 Out of Scope for MVP
- Owner self-service portal
- Payment gateway
- Real-time chat dalam aplikasi
- Advanced geospatial search
- Multi-vendor contract system
- Automated invoice system
- Full scheduling engine dengan availability matrix

# 7. Core Product Pillars

## 7.1 Discovery
User dapat menemukan lokasi atau layanan melalui homepage, search, filter, kategori, dan listing.

## 7.2 Decision Support
User dapat mengevaluasi lokasi dengan gallery, deskripsi, harga mulai dari, rating, review, fasilitas, akses, listrik, pencahayaan, suara, dan alamat.

## 7.3 Conversion
User dapat menghubungi Lokasinema lewat WhatsApp dan/atau form web. Form web mensyaratkan login.

## 7.4 Operations
Admin dapat mengelola lokasi, services, media, review, inquiry, dan status booking request.

# 8. Interpreted UI from Design

## 8.1 Homepage
Homepage berfungsi sebagai marketing page dan entry point ke discovery. Dari screenshot, homepage mencakup:
- hero dengan branding Lokasinema
- search bar utama
- section lokasi unggulan atau lokasi ideal
- section penjelasan brand
- daftar genre / kategori kebutuhan shooting
- production and services
- partner or trust logos
- behind the scene gallery
- CTA section
- footer

## 8.2 Listing Page
Listing page menampilkan:
- navbar gelap
- search bar
- chips atau kategori filter
- grid card lokasi
- peta di sisi kanan atau area tertentu
- pricing dan rating per card
- CTA lebih lanjut

## 8.3 Detail Location Page
Detail location page menampilkan:
- gallery besar dan thumbnail
- nama lokasi
- rating
- starting price
- tombol Hubungi
- deskripsi lokasi
- informasi teknis seperti akses, pencahayaan, kelistrikan, suara
- kemungkinan accordion untuk detail tambahan

## 8.4 Visual Direction
- Warna dominan gelap untuk frame global
- Konten utama menggunakan white surface agar card dan data mudah dibaca
- Foto lokasi adalah elemen utama dan harus dioptimalkan
- CTA fokus pada eksplorasi dan kontak

# 9. Product Principles

- Visual-first: kualitas gambar dan presentasi media sangat penting.
- Fast exploration: pencarian dan filter harus ringan dan jelas.
- Clear conversion: user harus mudah menghubungi atau memesan.
- Structured information: detail teknis harus konsisten dan mudah dibandingkan.
- AI-friendly and CMS-friendly: data harus bersih, terstruktur, dan mudah dirender oleh frontend.

# 10. User Stories

## 10.1 Discovery Stories
- Sebagai user, saya ingin mencari lokasi berdasarkan keyword agar cepat menemukan lokasi yang relevan.
- Sebagai user, saya ingin memfilter lokasi berdasarkan kategori, kota, dan tag agar hasil lebih sesuai.
- Sebagai user, saya ingin melihat lokasi pada peta agar punya gambaran visual area.

## 10.2 Detail Stories
- Sebagai user, saya ingin melihat galeri foto dan video agar bisa menilai kecocokan lokasi.
- Sebagai user, saya ingin melihat harga mulai dari agar bisa memperkirakan budget.
- Sebagai user, saya ingin membaca spesifikasi teknis seperti akses, kelistrikan, pencahayaan, dan suara.
- Sebagai user, saya ingin membaca review user dan admin agar keputusan lebih yakin.

## 10.3 Conversion Stories
- Sebagai user, saya ingin menghubungi via WhatsApp agar cepat berbicara dengan admin.
- Sebagai user, saya ingin mengirim pesan via form web agar inquiry saya tercatat.
- Sebagai user, saya paham bahwa mengirim pesan via web membutuhkan login.
- Sebagai user, saya ingin memesan layanan produksi selain lokasi.

## 10.4 Admin Stories
- Sebagai admin, saya ingin membuat dan mengedit lokasi.
- Sebagai admin, saya ingin upload banyak gambar ke Cloudinary.
- Sebagai admin, saya ingin menautkan video YouTube untuk tiap lokasi bila ada.
- Sebagai admin, saya ingin melihat dan memproses inquiry.
- Sebagai admin, saya ingin mengelola reviews dari user dan review editorial dari admin.
- Sebagai admin, saya ingin mengelola layanan produksi dan status booking request.

# 11. Primary User Flows

## 11.1 Flow A: Search to Location Inquiry via WhatsApp
1. User membuka homepage atau listing page.
2. User memasukkan keyword atau memilih kategori.
3. User melihat hasil listing.
4. User membuka detail lokasi.
5. User klik tombol Hubungi via WhatsApp.
6. Sistem membentuk pesan WhatsApp berisi konteks lokasi dan intent user.
7. User diarahkan ke WhatsApp.

## 11.2 Flow B: Search to Web Inquiry
1. User membuka homepage atau listing page.
2. User mencari lokasi.
3. User membuka detail lokasi.
4. User klik Kirim Pesan via Web.
5. Jika belum login, user diarahkan ke login/register.
6. Setelah login, user mengisi form inquiry.
7. Inquiry tersimpan ke database.
8. Admin melihat inquiry dan menindaklanjuti.

## 11.3 Flow C: Service Booking Request
1. User membuka halaman layanan atau detail service.
2. User membaca detail service.
3. User klik booking request.
4. User bisa diarahkan ke form web atau WhatsApp tergantung CTA yang dipilih.
5. Booking request tersimpan jika via form.

## 11.4 Flow D: Review Submission
1. User login.
2. User membuka detail lokasi.
3. User mengisi rating dan review.
4. Review masuk sebagai pending atau published sesuai kebijakan moderasi.
5. Admin dapat mengelola review tersebut.

# 12. Information Architecture

## 12.1 Public Routes
- `/`
- `/locations`
- `/locations/[slug]`
- `/services`
- `/services/[slug]`
- `/about`
- `/contact`
- `/login`
- `/register`
- `/profile`

## 12.2 Admin Routes
- `/admin`
- `/admin/locations`
- `/admin/locations/new`
- `/admin/locations/[id]`
- `/admin/services`
- `/admin/services/[id]`
- `/admin/categories`
- `/admin/reviews`
- `/admin/inquiries`
- `/admin/bookings`
- `/admin/users`

# 13. Functional Requirements

## 13.1 Homepage

### Purpose
Menjadi entry point utama untuk branding, trust, dan pencarian.

### Features
- Hero section dengan heading, subheading, dan search form.
- Search by keyword.
- Shortcut kategori atau lokasi unggulan.
- Section tentang Lokasinema.
- Section production and services.
- Trust logos.
- Behind the scene gallery.
- CTA section.
- Footer.

### Acceptance Criteria
- Search form mengarah ke `/locations` dengan query string.
- Klik kategori unggulan mengarah ke listing yang sudah terfilter.
- Semua section tampil responsif.
- Hero, CTA, dan footer tampil sesuai hierarchy desain.

## 13.2 Location Listing Page

### Purpose
Memudahkan eksplorasi banyak lokasi secara cepat.

### Features
- Search input.
- Filter chips dan/atau side filter.
- Sorting.
- Grid card lokasi.
- Google Maps embedded visual panel.
- Pagination atau load more.

### Filters for MVP
- keyword
- city
- category
- tags
- featured
- min price
- max price
- sort

### Listing Card Fields
- cover image
- title
- short location label
- rating average
- review count
- starting price
- featured badge if relevant

### Acceptance Criteria
- Search dan filter memengaruhi hasil listing.
- Query state tersimpan pada URL.
- Google Maps embedded tampil sebagai visual support.
- Klik card membuka detail lokasi.
- Hasil kosong memiliki empty state yang jelas.

## 13.3 Location Detail Page

### Purpose
Memberi informasi lengkap untuk keputusan inquiry atau booking.

### Features
- gallery image
- optional YouTube embed
- title
- address / city / province
- rating average and review count
- starting price
- featured badge
- description
- technical specs
- facilities
- CTA buttons: WhatsApp and Web Form
- related locations
- review list
- review form for logged-in users

### Technical Specs Sections
- akses
- pencahayaan
- kelistrikan
- suara
- fasilitas
- catatan tambahan

### Acceptance Criteria
- Semua data utama lokasi tampil tanpa ambiguity.
- WhatsApp CTA membentuk pesan yang relevan.
- Web form CTA memerlukan login.
- Video embed YouTube hanya ditampilkan jika link tersedia.
- Gallery mendukung cover image dan multiple thumbnails.

## 13.4 Services Listing and Detail

### Purpose
Menampilkan layanan produksi tambahan yang dapat dibooking.

### Features
- daftar services
- detail service
- service description
- icon or cover
- CTA booking via WhatsApp and/or web form

### Acceptance Criteria
- Services dapat dilihat di public site.
- Service dapat diajukan booking request.
- Admin dapat mengaktifkan dan menonaktifkan service.

## 13.5 Authentication

### Requirements
- Register
- Login
- Logout
- Role-based access
- Protected form submission for web inquiry and review creation

### Roles
- guest
- user
- admin

### Business Rule
- Guest boleh browsing, search, lihat detail, dan klik WhatsApp.
- Guest tidak boleh mengirim pesan via web form.
- Guest tidak boleh submit review.
- User login boleh kirim pesan via web dan submit review.
- Admin punya akses CMS.

## 13.6 Inquiry System

### Types
- location inquiry
- service booking request

### Channels
- WhatsApp
- web form

### WhatsApp Behaviour
Sistem harus membangun teks WhatsApp yang sesuai konteks. Minimal mencakup:
- nama lokasi atau nama layanan
- URL halaman terkait
- nama user jika tersedia
- intent: tanya harga, survey, booking, atau info umum

### Example WhatsApp Message Template for Location
Halo Lokasinema, saya tertarik dengan lokasi: {location_title}.\nLink: {page_url}.\nNama saya: {user_name_or_placeholder}.\nSaya ingin bertanya mengenai ketersediaan, harga mulai dari, dan proses booking.

### Example WhatsApp Message Template for Service
Halo Lokasinema, saya tertarik dengan layanan: {service_title}.\nLink: {page_url}.\nNama saya: {user_name_or_placeholder}.\nSaya ingin bertanya mengenai detail layanan dan booking.

### Web Form Fields for Location Inquiry
- full_name
- email
- phone
- project_name
- shoot_date
- duration
- crew_size
- message

### Web Form Fields for Service Booking Request
- full_name
- email
- phone
- company_name
- project_name
- preferred_date
- service_needs
- budget_range
- message

### Acceptance Criteria
- CTA WhatsApp membuka `wa.me` atau deep link WhatsApp dengan pesan terisi.
- CTA web form hanya dapat submit jika user login.
- Semua form tervalidasi.
- Submission tersimpan di database.
- Admin dapat melihat status inquiry.

## 13.7 Reviews and Ratings

### Sources
- User review
- Admin review or editorial review

### Review Fields
- reviewer type
- reviewer display name
- rating
- comment
- status
- created at

### Business Rules
- User review memerlukan login.
- Review user dapat dimoderasi sebelum tayang.
- Admin dapat menambahkan review editorial.
- Rating average dihitung dari review yang published.

### Acceptance Criteria
- Review tampil di detail lokasi.
- User login dapat submit review.
- Admin dapat publish, hide, atau delete review.

## 13.8 Admin CMS

### Modules
- dashboard
- locations
- services
- categories
- tags
- inquiries
- bookings
- reviews
- users

### Location CRUD Fields
- title
- slug
- short_description
- description
- city
- province
- address
- latitude
- longitude
- starting_price
- cover image
- gallery images
- youtube_embed_url
- featured flag
- publish status
- categories
- tags
- technical specs
- facilities

### Acceptance Criteria
- Admin dapat create, read, update, delete lokasi.
- Admin dapat upload image ke Cloudinary.
- Admin dapat menyimpan YouTube URL.
- Admin dapat manage service dan booking request.
- Admin dapat publish/unpublish lokasi dan layanan.

# 14. Data Model Requirements

## 14.1 Users
Fields:
- id
- full_name
- email
- phone
- password_hash
- role
- avatar_url nullable
- created_at
- updated_at

## 14.2 Locations
Fields:
- id
- title
- slug
- short_description
- description
- city
- province
- address
- latitude nullable
- longitude nullable
- starting_price
- currency
- featured boolean
- is_published boolean
- youtube_embed_url nullable
- created_by_admin_id
- created_at
- updated_at

## 14.3 LocationMedia
Fields:
- id
- location_id
- public_id
- secure_url
- width
- height
- format
- bytes
- alt_text nullable
- sort_order
- is_cover boolean
- created_at

Notes:
- Images are uploaded to Cloudinary.
- Frontend renders Cloudinary optimized URLs or stored secure_url.

## 14.4 Categories
Fields:
- id
- name
- slug
- description nullable
- is_active

## 14.5 Tags
Fields:
- id
- name
- slug
- is_active

## 14.6 LocationCategories
Join table between locations and categories.

## 14.7 LocationTags
Join table between locations and tags.

## 14.8 LocationSpecs
Fields:
- id
- location_id
- access_info nullable
- lighting_info nullable
- electricity_info nullable
- sound_info nullable
- facilities_info nullable
- parking_info nullable
- additional_notes nullable

## 14.9 Services
Fields:
- id
- title
- slug
- short_description
- description
- icon_key nullable
- cover_image_url nullable
- starting_price nullable
- is_bookable boolean
- is_published boolean
- created_at
- updated_at

## 14.10 Reviews
Fields:
- id
- location_id
- user_id nullable
- reviewer_type enum(user, admin)
- reviewer_name
- rating
- comment
- status enum(pending, published, hidden)
- created_at
- updated_at

## 14.11 Inquiries
Fields:
- id
- type enum(location_inquiry, service_booking)
- location_id nullable
- service_id nullable
- user_id nullable
- full_name
- email
- phone
- company_name nullable
- project_name nullable
- preferred_date nullable
- duration nullable
- crew_size nullable
- budget_range nullable
- message
- status enum(new, contacted, qualified, booked, closed)
- source_channel enum(web_form, whatsapp)
- created_at
- updated_at

# 15. API Requirements

## 15.1 Public Endpoints
- `GET /api/locations`
- `GET /api/locations/:slug`
- `GET /api/categories`
- `GET /api/tags`
- `GET /api/services`
- `GET /api/services/:slug`
- `GET /api/reviews?locationId=...`

## 15.2 Authenticated User Endpoints
- `POST /api/inquiries`
- `POST /api/reviews`
- `GET /api/me`
- `PATCH /api/me`

## 15.3 Admin Endpoints
- `POST /api/admin/locations`
- `PATCH /api/admin/locations/:id`
- `DELETE /api/admin/locations/:id`
- `POST /api/admin/locations/:id/media`
- `DELETE /api/admin/locations/:id/media/:mediaId`
- `POST /api/admin/services`
- `PATCH /api/admin/services/:id`
- `DELETE /api/admin/services/:id`
- `GET /api/admin/inquiries`
- `PATCH /api/admin/inquiries/:id/status`
- `GET /api/admin/reviews`
- `PATCH /api/admin/reviews/:id/status`
- `POST /api/admin/categories`
- `PATCH /api/admin/categories/:id`
- `POST /api/admin/tags`
- `PATCH /api/admin/tags/:id`

## 15.4 Query Parameters for Locations
Supported query parameters:
- `q`
- `city`
- `category`
- `tag`
- `featured`
- `minPrice`
- `maxPrice`
- `sort`
- `page`
- `limit`

Example:
`/api/locations?q=bogor&category=kampung&featured=true&page=1&limit=12`

# 16. Frontend Technical Requirements

## 16.1 Framework and Libraries
- Next.js
- TypeScript
- Tailwind CSS
- SWR for data fetching
- React Hook Form recommended
- Zod recommended for validation
- Google Maps embedded for location visualization

## 16.2 Frontend Architectural Constraints
- Gunakan App Router atau Pages Router secara konsisten. Prefer App Router jika project baru.
- Semua data fetching di client yang dinamis gunakan SWR.
- SEO page penting dapat menggunakan server rendering atau pre-render sesuai kebutuhan Next.js.
- Query string listing harus sinkron dengan UI filter.
- Hindari state filter yang tidak tercermin di URL untuk halaman listing public.

## 16.3 Suggested Frontend Folder Structure
```text
src/
  app/
    (public)/
      page.tsx
      locations/
        page.tsx
        [slug]/page.tsx
      services/
        page.tsx
        [slug]/page.tsx
      about/page.tsx
      contact/page.tsx
      login/page.tsx
      register/page.tsx
    admin/
      page.tsx
      locations/
      services/
      inquiries/
      reviews/
      categories/
  components/
    ui/
    layout/
    home/
    locations/
    services/
    forms/
  hooks/
    useLocations.ts
    useLocationDetail.ts
    useServices.ts
    useReviews.ts
    useAuth.ts
  lib/
    api.ts
    auth.ts
    utils.ts
    whatsapp.ts
  types/
    location.ts
    service.ts
    inquiry.ts
    review.ts
```

## 16.4 SWR Usage Guidelines
- Use stable keys based on route and query params.
- Gunakan fallback data atau loading skeleton untuk UX yang halus.
- Revalidate setelah submit review atau inquiry jika perlu.
- Pisahkan typed fetcher di `lib/api.ts`.

## 16.5 Google Maps Embedded Guidelines
- Map bersifat visual only.
- Use Google Maps embed URL based on address or coordinates.
- Jangan implementasi search radius pada MVP.
- Jika latitude/longitude tidak tersedia, fallback ke address-based embed.

# 17. Backend Technical Requirements

## 17.1 Framework and Libraries
- NestJS
- TypeORM
- PostgreSQL
- JWT-based auth
- Cloudinary SDK for image upload and transformation

## 17.2 Backend Architectural Constraints
- Media image tidak disimpan sebagai binary di PostgreSQL.
- Gambar diupload ke Cloudinary, lalu metadata dan URL disimpan ke database.
- Video tidak diupload ke server; hanya simpan YouTube embedded URL.
- Inquiry via web harus authenticated.
- WhatsApp link generation dapat dilakukan di frontend atau backend helper, namun source format harus konsisten.

## 17.3 Suggested NestJS Modules
- auth
- users
- locations
- location-media
- categories
- tags
- services
- reviews
- inquiries
- admin
- common

## 17.4 Cloudinary Requirements
- Upload image dengan transformasi yang ramah web.
- Simpan minimal `public_id` dan `secure_url`.
- Simpan metadata width, height, format jika tersedia.
- Gunakan ukuran responsif atau transformation preset untuk listing dan detail.

## 17.5 YouTube Requirements
- Simpan URL embed yang valid, misalnya `https://www.youtube.com/embed/{videoId}`.
- Validasi agar bukan arbitrary iframe URL.
- Render hanya jika URL valid.

# 18. Business Rules

- Harga pada lokasi dan layanan ditampilkan sebagai starting price, bukan harga final pasti.
- Pihak ketiga tidak memiliki owner dashboard pada MVP.
- Booking dan inquiry ditangani admin internal Lokasinema.
- Map hanya untuk visual, bukan mesin pencarian berbasis jarak.
- Guest boleh menghubungi via WhatsApp tanpa login.
- User harus login untuk kirim pesan via web.
- User harus login untuk submit review.
- Admin dapat membuat review editorial.
- Hanya review dengan status `published` yang dihitung ke rating average.
- Lokasi dan layanan hanya muncul publik jika `is_published = true`.
- Setiap lokasi publik wajib memiliki minimal satu cover image.

# 19. Non-Functional Requirements

## 19.1 Performance
- Homepage dan listing harus cepat dimuat.
- Gunakan optimasi gambar dan lazy loading.
- Hindari payload berlebihan untuk listing.
- Gunakan pagination.

## 19.2 Security
- Auth menggunakan JWT atau session yang aman.
- Password di-hash dengan algoritma aman.
- Rate limit untuk login, review submit, dan inquiry submit.
- Sanitasi input untuk mencegah XSS dan injection.
- Admin endpoints harus terlindungi role guard.

## 19.3 Accessibility
- Semantic HTML.
- Fokus keyboard jelas.
- Kontras warna memadai.
- Form field memiliki label.
- Alt text pada image penting.

## 19.4 SEO
- Dynamic metadata per location dan service detail page.
- Open Graph tags.
- Sitemap.
- Canonical URLs.
- Human-readable slug.

## 19.5 Analytics
Recommended but optional for MVP:
- track search usage
- track location detail visits
- track WhatsApp click events
- track web inquiry submits
- track service booking submits

# 20. Validation Rules

## 20.1 Location Validation
- title wajib
- slug wajib unik
- starting_price wajib bernilai >= 0
- city wajib
- description wajib
- minimal satu cover image saat publish

## 20.2 Review Validation
- rating wajib antara 1 sampai 5
- comment wajib minimal panjang tertentu, misalnya 10 karakter
- user harus login untuk submit review user

## 20.3 Inquiry Validation
- full_name wajib
- email wajib valid
- phone wajib valid
- message wajib
- type wajib valid
- jika type adalah location inquiry maka `location_id` wajib
- jika type adalah service booking maka `service_id` wajib

# 21. Acceptance Criteria Summary by Module

## 21.1 Homepage Done When
- Search bekerja.
- CTA dan section utama tampil responsif.
- Kategori unggulan dapat diklik.

## 21.2 Listing Done When
- Search dan filter sinkron ke URL.
- Card menampilkan foto, title, rating, starting price.
- Map embedded tampil sebagai visual support.
- Empty state dan loading state tersedia.

## 21.3 Detail Location Done When
- Gallery dan optional YouTube embed tampil.
- Technical specs tampil rapi.
- WhatsApp CTA menghasilkan pesan yang sesuai.
- Web inquiry CTA memerlukan login.
- Review tampil dan user login bisa submit review.

## 21.4 Services Done When
- Service list dan detail bisa dilihat public.
- Service booking request dapat dilakukan.

## 21.5 Admin Done When
- Admin dapat CRUD lokasi, services, categories, tags.
- Admin dapat melihat dan mengubah status inquiries dan reviews.
- Admin dapat upload image ke Cloudinary.

# 22. UX Content and CTA Requirements

## 22.1 Primary CTAs
- Cari Lokasi
- Hubungi via WhatsApp
- Kirim Pesan
- Booking Layanan

## 22.2 Copy Principles
- Gunakan bahasa yang jelas, ringkas, dan meyakinkan.
- Jelaskan bahwa harga adalah mulai dari.
- Jelaskan bahwa form web membutuhkan login.
- CTA harus konsisten di seluruh halaman.

# 23. Review Moderation Policy

Recommended policy for MVP:
- User review baru masuk ke status `pending`.
- Admin review boleh langsung `published`.
- Admin dapat edit, publish, hide, atau delete review.
- Rating average dihitung ulang setiap ada perubahan review published.

# 24. Error States and Empty States

## 24.1 Empty Listing
Tampilkan pesan seperti:
"Belum ada lokasi yang cocok dengan filter ini. Coba ubah kata kunci atau kategori."

## 24.2 Failed Inquiry Submit
Tampilkan pesan jelas dan pertahankan input user jika aman.

## 24.3 No Reviews Yet
Tampilkan placeholder agar halaman tidak terasa kosong.

## 24.4 Missing Map Coordinates
Fallback ke embedded map berbasis alamat atau sembunyikan panel jika tidak bisa dirender.

# 25. Suggested Database Indexing

Recommended indexes:
- locations.slug unique index
- categories.slug unique index
- tags.slug unique index
- services.slug unique index
- locations.city index
- locations.is_published index
- locations.featured index
- inquiries.status index
- reviews.status index
- full text search support untuk title dan description bila diperlukan

# 26. Suggested Status Enums

## 26.1 Inquiry Status
- new
- contacted
- qualified
- booked
- closed

## 26.2 Review Status
- pending
- published
- hidden

## 26.3 User Role
- user
- admin

# 27. MVP Delivery Priority

## Phase 1
- Public homepage
- Location listing
- Location detail
- Auth
- WhatsApp CTA
- Web inquiry form
- Admin CRUD lokasi
- Cloudinary image upload

## Phase 2
- Services listing and detail
- Service booking requests
- Reviews and moderation
- Improved admin dashboard

## Phase 3
- SEO enhancement
- analytics enhancement
- richer content blocks
- recommendation / related logic improvement

# 28. Risks and Mitigations

## Risk 1: Media-heavy pages become slow
Mitigation:
- Use Cloudinary optimization
- lazy loading
- responsive images

## Risk 2: Inquiry spam
Mitigation:
- auth requirement for web form
- rate limiting
- validation
- CAPTCHA optional

## Risk 3: Inconsistent admin data entry
Mitigation:
- structured form fields
- validation rules
- required fields before publish

## Risk 4: Review abuse
Mitigation:
- moderation workflow
- login requirement
- admin review controls

# 29. Open Decisions Resolved in This Version

The following decisions are considered locked for this PRD version:
- Maps use Google Maps embedded.
- Frontend data fetching uses SWR.
- Images are stored in Cloudinary and rendered using optimized links.
- Videos use embedded YouTube links.
- Contact flows support WhatsApp and web form.
- Sending message via web requires login.
- Prices are starting prices.
- There is no owner dashboard for third parties.
- Map is visual only.
- Services are bookable.
- Reviews can come from user and admin.

# 30. AI Agent Implementation Notes

When generating code from this PRD:
- Prefer modular components and typed interfaces.
- Use reusable section and card components.
- Ensure listing filters round-trip through query params.
- Treat Cloudinary URLs as canonical image sources.
- Treat YouTube embed links as optional media fields.
- Do not implement owner dashboard or payment system in MVP.
- Do not implement advanced geolocation search in MVP.
- Enforce auth only for web form and review submission, not for browsing or WhatsApp CTA.
- Use starting price wording consistently in UI and API.

# 31. Definition of Done

A release candidate for MVP is considered done when:
- Public homepage, listing, detail, services, and contact flows are functional.
- Web inquiry requires login and stores data correctly.
- WhatsApp CTA opens correct prefilled message.
- Admin can manage locations, services, media, reviews, and inquiries.
- Images are served from Cloudinary.
- YouTube embeds work where configured.
- Reviews and ratings function according to moderation rules.
- Core pages are responsive and usable on mobile and desktop.

# 32. Appendix: Suggested TypeScript DTO Shapes

## 32.1 Location DTO
```ts
export interface LocationDto {
  id: string;
  title: string;
  slug: string;
  shortDescription: string;
  description: string;
  city: string;
  province: string;
  address: string;
  latitude?: number | null;
  longitude?: number | null;
  startingPrice: number;
  currency: string;
  featured: boolean;
  isPublished: boolean;
  youtubeEmbedUrl?: string | null;
  averageRating: number;
  reviewCount: number;
  categories: { id: string; name: string; slug: string }[];
  tags: { id: string; name: string; slug: string }[];
  media: {
    id: string;
    secureUrl: string;
    altText?: string | null;
    isCover: boolean;
    sortOrder: number;
  }[];
  specs?: {
    accessInfo?: string | null;
    lightingInfo?: string | null;
    electricityInfo?: string | null;
    soundInfo?: string | null;
    facilitiesInfo?: string | null;
    parkingInfo?: string | null;
    additionalNotes?: string | null;
  };
}
```

## 32.2 Inquiry DTO
```ts
export interface CreateInquiryDto {
  type: 'location_inquiry' | 'service_booking';
  locationId?: string;
  serviceId?: string;
  fullName: string;
  email: string;
  phone: string;
  companyName?: string;
  projectName?: string;
  preferredDate?: string;
  duration?: string;
  crewSize?: string;
  budgetRange?: string;
  message: string;
}
```

## 32.3 Review DTO
```ts
export interface CreateReviewDto {
  locationId: string;
  rating: number;
  comment: string;
}
```

# 33. Appendix: Suggested Frontend UI States

- `loading`
- `empty`
- `error`
- `success`
- `unauthenticated`
- `pending moderation`

# 34. Appendix: Suggested QA Checklist

## Public Experience
- Search works.
- Filters work.
- Query params persist.
- Detail pages render correctly.
- WhatsApp CTA opens expected message.
- Map embed renders.
- Responsive layout works.

## Authenticated Experience
- Login works.
- Web form requires login.
- Review submit requires login.
- Logout works.

## Admin Experience
- Can CRUD locations.
- Can upload Cloudinary images.
- Can manage services.
- Can manage reviews.
- Can manage inquiries.

