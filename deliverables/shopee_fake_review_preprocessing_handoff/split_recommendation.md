# Split Recommendation

## Recommended Split

Gunakan kolom `split_hint` untuk baseline pertama.

| Split | Label 0 | Label 1 |
|---|---:|---:|
| train | 776 | 776 |
| valid | 166 | 166 |
| test | 167 | 167 |

Split ini menjaga distribusi label tetap seimbang.

## Alternative Check

Gunakan `group_split_hint_user` untuk mengecek apakah performa model turun ketika user yang sama tidak tersebar bebas antar split.

Ini berguna karena beberapa user punya lebih dari satu review. Kalau split acak murni dipakai, model bisa belajar pola user tertentu.

## Columns to Exclude from Features

Jangan pakai kolom ini sebagai fitur:

- `final_label`
- `label_name`
- `label_quality`
- `candidate_category`
- `split_hint`
- `group_split_hint_user`

Kolom target, audit, dan split tidak boleh masuk ke input model.
