# Shopee Fake Review Dataset Handoff

Repository folder ini berisi dataset hasil preprocessing untuk baseline fake review detection.

## File Utama

```text
shopee_fake_review_modeling_dataset.csv
```

Gunakan kolom:

- `text_for_model` sebagai input teks.
- `final_label` sebagai target.
- `split_hint` sebagai pembagian awal train/valid/test.

## Ringkasan Dataset

| Item | Nilai |
|---|---:|
| Baris | 2.218 |
| Kolom | 34 |
| Missing value | 0 |
| Label 0 - real/original | 1.109 |
| Label 1 - suspicious/fake-like | 1.109 |

## Struktur File

| File | Isi |
|---|---|
| `shopee_fake_review_modeling_dataset.csv` | Dataset utama untuk modeling |
| `dataset_summary.md` | Ringkasan ukuran data, label, dan split |
| `data_dictionary.md` | Penjelasan kolom |
| `b2b_feature_mapping.md` | Mapping fitur ke NLP, behavior proxy, seller/product context, dan trust score candidate |
| `split_recommendation.md` | Saran pembagian train/valid/test |
| `processing_notes.md` | Catatan preprocessing dan batasan data |
| `manifest.md` | Daftar file, ukuran, dan checksum |

## Catatan Penggunaan

Jangan gunakan kolom berikut sebagai fitur model:

- `final_label`
- `label_name`
- `label_quality`
- `candidate_category`
- `split_hint`
- `group_split_hint_user`

Kolom itu dipakai untuk target, audit label, dan split data.

Dataset ini siap untuk baseline modeling. Label tambahan berasal dari rule-based candidate labeling, bukan validasi internal Shopee.
