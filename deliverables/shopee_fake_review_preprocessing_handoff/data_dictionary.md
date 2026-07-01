# Data Dictionary

## Target dan Split

| Column | Description | Use |
|---|---|---|
| `row_id` | ID baris dataset handoff | tracking |
| `final_label` | 0 real/original, 1 suspicious/fake-like | target |
| `label_name` | versi teks dari `final_label` | reference |
| `split_hint` | train/valid/test stratified split | split |
| `group_split_hint_user` | split alternatif berbasis `userid` | split check |
| `label_quality` | sumber kualitas label | audit |
| `candidate_category` | kategori hasil kandidat label | audit |

## Text Columns

| Column | Description | Use |
|---|---|---|
| `text_for_model` | teks utama untuk model | feature |
| `clean_review` | review setelah preprocessing | feature/reference |
| `comment` | review asli | reference |
| `product_title` | nama produk | optional feature |

## Rating and IDs

| Column | Description | Use |
|---|---|---|
| `rating` | nilai rating mentah dari dataset | feature |
| `rating_star` | rating bintang | feature |
| `userid` | ID reviewer | group split / aggregate |
| `shop_id` | ID toko/seller | group split / aggregate |
| `item_id` | ID produk | group split / aggregate |
| `ctime` | timestamp review | optional feature |

## Text Features

| Column | Description |
|---|---|
| `char_count` | jumlah karakter teks bersih |
| `word_count` | jumlah kata |
| `unique_word_count` | jumlah kata unik |
| `unique_word_ratio` | rasio kata unik terhadap total kata |
| `repeated_word_count` | jumlah pengulangan kata |
| `repetition_score` | rasio repetisi kata |
| `exclamation_count` | jumlah tanda seru pada teks asli |
| `uppercase_ratio` | rasio huruf kapital pada teks asli |
| `high_rating_short_review` | flag rating tinggi dengan review pendek |
| `is_empty_review` | 0 di file final; review kosong sudah dibuang |

## Aggregate Features

| Column | Description |
|---|---|
| `user_review_count` | jumlah review per user dalam dataset |
| `user_avg_rating` | rata-rata rating user |
| `user_rating_std` | variasi rating user |
| `seller_review_count` | jumlah review per seller |
| `seller_avg_rating` | rata-rata rating seller |
| `product_review_count` | jumlah review per produk |
| `product_avg_rating` | rata-rata rating produk |

## Do Not Use as Model Features

- `final_label`
- `label_name`
- `label_quality`
- `candidate_category`
- `split_hint`
- `group_split_hint_user`
