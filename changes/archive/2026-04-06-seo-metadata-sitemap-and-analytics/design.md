# Design: seo-metadata-sitemap-and-analytics

## Metadata

- Gunakan data dari fetch server-side untuk metadata agar crawler melihat judul benar (PRD §16.2 SEO).

## Sitemap

- Generate static paths + dynamic dari API atau build-time fetch; invalidasi sesuai deployment (ISR/revalidate sesuai stack).

## Analytics

- Wrapper `track(event, payload)` agar tidak coupling ke satu vendor; §19.5 events.

## Referensi PRD

- §19.4 SEO, §19.5 Analytics, §27 Phase 3 (SEO enhancement — slice ini adalah inti MVP+ yang diminta user urutan #10).

## Phase alignment

PRD Phase 3 menyebut SEO enhancement; user meminta priority 10 untuk slice ini — treat sebagai penutup MVP delivery untuk discoverability.
