# Capability: reviews

Rating, ulasan pengguna, moderasi, dan editorial admin.

## Requirements

### Rv1 — Display published reviews

Detail lokasi SHALL menampilkan ulasan dengan status `published` dan placeholder jika kosong.

### Rv2 — Authenticated user submit

User terautentikasi SHALL dapat mengirim review; guest SHALL NOT (PRD §18).

### Rv3 — Moderation state

Review user baru SHALL memiliki status `pending` hingga admin mengubahnya (kebijakan §23).

### Rv4 — Admin editorial

Admin SHALL dapat menambah review dengan tipe admin dan dapat publish, hide, atau menghapus review.

### Rv5 — Rating aggregation

Average rating dan jumlah ulasan SHALL hanya mempertimbangkan review `published` (PRD §18).

### Rv6 — Validation

Rating SHALL antara 1 dan 5; comment memenuhi panjang minimum (PRD §20.2).

## Scenarios

### Rv2

- **Given** guest
- **When** guest mencoba POST review
- **Then** request ditolak

### Rv3

- **Given** user mengirim review baru
- **When** publik membuka detail lokasi
- **Then** review tidak tampil sampai admin publish

### Rv5

- **Given** admin menyembunyikan review yang sebelumnya published
- **When** halaman detail dimuat ulang
- **Then** rating average diperbarui tanpa menyertakan review hidden
