# Processing Notes

## Input Data

Sumber data yang dipakai:

- `train_review_only.csv`
- `review_shopee.csv`
- `dataset_panci_wajan.csv`
- `shopee_ulasan_label7.csv`

`train_review_only.csv` dipakai sebagai label awal. `review_shopee.csv` dipakai untuk menambah kandidat label melalui rule-based screening.

## Text Processing

Kolom review dibersihkan dengan langkah berikut:

- lowercase
- hapus URL
- hapus HTML tag
- hapus emoji dan simbol non-teks
- rapikan spasi
- simpan teks bersih di `clean_review`

Review kosong tidak dimasukkan ke file final handoff.

## Feature Set

Fitur yang disiapkan:

- panjang teks: `char_count`, `word_count`
- variasi kata: `unique_word_count`, `unique_word_ratio`
- repetisi: `repeated_word_count`, `repetition_score`
- gaya teks: `exclamation_count`, `uppercase_ratio`
- rating + teks pendek: `high_rating_short_review`
- agregat user/seller/product dari kolom yang tersedia

## Labeling

Target akhir ada di:

```text
final_label
```

Makna label:

```text
0 = real/original
1 = suspicious/fake-like
```

Sebagian label berasal dari data awal. Sebagian lain berasal dari rule-based candidate labeling pada review Shopee yang belum berlabel.

## Known Limits

Dataset publik tidak memiliki:

- IP address
- device fingerprint
- login behavior
- verified transaction asli
- histori transaksi
- relasi buyer-seller

Fitur tersebut tidak dibuat.

Label tambahan belum setara dengan validasi internal platform. Untuk baseline modeling, dataset ini sudah siap.
