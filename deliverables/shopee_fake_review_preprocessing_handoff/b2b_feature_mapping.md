# B2B Feature Mapping

Dokumen ini memetakan dataset handoff ke konsep B2B “Gembok Ganda”: NLP Core, behavior/seller/product context, dan trust score candidate.

## 1. NLP Core

Kolom utama:

- `text_for_model`
- `clean_review`
- `comment`

Fitur teks yang tersedia:

- `char_count`
- `word_count`
- `unique_word_count`
- `unique_word_ratio`
- `repeated_word_count`
- `repetition_score`
- `exclamation_count`
- `uppercase_ratio`
- `high_rating_short_review`

Contoh sinyal yang bisa dipakai:

- review terlalu pendek
- review repetitif
- rating tinggi dengan teks minim
- teks terlalu generik
- pola huruf kapital atau tanda seru berlebihan

## 2. User Behavior Proxy

Dataset publik tidak punya histori login atau transaksi user. Proxy yang tersedia hanya dari pola review.

Kolom ID:

- `userid`

Fitur:

- `user_review_count`
- `user_avg_rating`
- `user_rating_std`

Contoh sinyal:

- user memberi banyak review
- user cenderung selalu memberi rating tinggi
- variasi rating user rendah

## 3. Seller Context Proxy

Kolom ID:

- `shop_id`

Fitur:

- `seller_review_count`
- `seller_avg_rating`

Contoh sinyal:

- seller punya banyak review
- rata-rata rating seller tinggi
- seller bisa dianalisis lebih lanjut dari rasio review mencurigakan setelah model berjalan

## 4. Product Context Proxy

Kolom ID:

- `item_id`
- `product_title`

Fitur:

- `product_review_count`
- `product_avg_rating`

Contoh sinyal:

- produk punya banyak review
- produk rating tinggi
- produk dengan banyak review pendek/repetitif bisa diprioritaskan untuk monitoring

## 5. Trust Score Candidate

Dataset ini belum membuat final AI Trust Score. Namun, fitur yang tersedia sudah bisa dipakai untuk membuat trust score candidate pada tahap modeling/scoring berikutnya.

Contoh komponen:

- text quality risk dari `word_count`, `unique_word_ratio`, dan `repetition_score`
- high-rating-short-review risk dari `high_rating_short_review`
- user behavior proxy dari `user_review_count`, `user_avg_rating`, dan `user_rating_std`
- seller/product context dari `seller_review_count`, `seller_avg_rating`, `product_review_count`, dan `product_avg_rating`

Contoh output tahap berikutnya:

```text
trust_score_candidate = 0 sampai 100
```

Interpretasi yang bisa dipakai saat scoring:

```text
80-100 = likely trusted
50-79  = needs monitoring
0-49   = suspicious
```

Angka tersebut belum ada di dataset handoff ini dan tidak boleh dianggap skor final.

## 6. Data Internal yang Tidak Tersedia

Dataset publik tidak menyediakan:

- IP address
- device fingerprint
- login behavior
- verified transaction asli
- payment/order behavior
- histori transaksi
- relasi buyer-seller
- jaringan fake order

Fitur tersebut tidak dibuat dan tidak diimputasi.

## 7. Kesimpulan Teknis

Dataset ini mendukung baseline “Gembok Ganda” versi dataset publik:

- NLP Core: tersedia melalui teks review dan fitur teks.
- Behavior/Seller/Product Context: tersedia sebagai proxy dari user, seller, dan product aggregate.
- AI Trust Score: belum final, tapi fitur dasar untuk trust score candidate sudah tersedia.
