# Design: location-listing-search-filter-map

## URL sebagai source of truth

- Gunakan `useSearchParams` + `router.replace/push` untuk round-trip filter (PRD §16.2).
- Hindari state filter murni client yang tidak tercermin di URL.

## Maps

- Embed URL dari lat/long jika ada; else address string (PRD §16.5, §24.4).
- Satu peta agregat atau peta statis konteks wilayah — pilih yang paling sederhana untuk MVP asalkan memenuhi "visual support".

## Performance

- Pagination atau load more; hindari payload besar (PRD §19.1).

## Referensi PRD

- §13.2, §15.1, §15.4, §16.4–§16.5, §21.2.
