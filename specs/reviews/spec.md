# Capability: reviews

## Purpose

Rating, ulasan pengguna, moderasi, dan editorial admin — disinkronkan dari change `reviews-and-rating-moderation`.

## Requirements

### Requirement: Display published reviews

Halaman detail lokasi SHALL menampilkan ulasan dengan status `published` dan placeholder jika tidak ada ulasan.

#### Scenario: Hanya ulasan published yang tampil

- **GIVEN** lokasi memiliki review `published` dan `pending`
- **WHEN** publik membuka halaman detail lokasi
- **THEN** hanya review `published` yang ditampilkan

#### Scenario: Placeholder jika tidak ada ulasan

- **GIVEN** lokasi tidak memiliki review `published`
- **WHEN** publik membuka halaman detail lokasi
- **THEN** UI menampilkan placeholder atau state kosong yang jelas

### Requirement: Authenticated user submit

Pengguna terautentikasi SHALL dapat mengirim review; guest SHALL NOT mengirim review (PRD §18).

#### Scenario: Guest ditolak mengirim review

- **GIVEN** guest tidak memiliki sesi terautentikasi
- **WHEN** guest mencoba POST review
- **THEN** request ditolak (misalnya 401)

#### Scenario: User terautentikasi dapat mengirim

- **GIVEN** user login
- **WHEN** user mengirim review valid untuk lokasi
- **THEN** review diterima untuk diproses (status sesuai kebijakan moderasi)

### Requirement: Moderation state

Review baru dari pengguna SHALL memiliki status `pending` hingga admin mengubah statusnya (kebijakan §23).

#### Scenario: Review baru tidak tampil publik sebelum publish

- **GIVEN** user mengirim review baru
- **WHEN** publik membuka detail lokasi
- **THEN** review tersebut tidak tampil sampai admin mempublish

### Requirement: Admin editorial

Admin SHALL dapat menambah review bertipe admin serta mempublish, menyembunyikan, atau menghapus review.

#### Scenario: Admin mempublish review pending

- **GIVEN** ada review user berstatus `pending`
- **WHEN** admin mempublish review tersebut
- **THEN** review menjadi `published` dan dapat tampil sesuai aturan tampilan

#### Scenario: Admin menyembunyikan review

- **GIVEN** ada review `published`
- **WHEN** admin menyembunyikan review
- **THEN** review tidak lagi ditampilkan sebagai published kepada publik

### Requirement: Rating aggregation

Rata-rata rating dan jumlah ulasan SHALL hanya mempertimbangkan review berstatus `published` (PRD §18).

#### Scenario: Perubahan status memperbarui agregat

- **GIVEN** admin menyembunyikan review yang sebelumnya `published`
- **WHEN** halaman detail lokasi dimuat ulang
- **THEN** rata-rata rating dan jumlah ulasan diperbarui tanpa menyertakan review yang tidak lagi published

### Requirement: Validation input review

Rating SHALL bernilai antara 1 dan 5; komentar memenuhi panjang minimum (PRD §20.2).

#### Scenario: Rating atau komentar di luar aturan ditolak

- **GIVEN** user terautentikasi
- **WHEN** user mengirim rating di luar 1–5 atau komentar di bawah minimum
- **THEN** server menolak dengan pesan validasi yang jelas
