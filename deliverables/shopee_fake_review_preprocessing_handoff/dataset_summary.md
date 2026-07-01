# Dataset Summary

## File

```text
shopee_fake_review_modeling_dataset.csv
```

## Shape

| Metric | Value |
|---|---:|
| Rows | 2.218 |
| Columns | 34 |
| Missing cells | 0 |
| Empty review rows | 0 |

## Label Distribution

| final_label | Meaning | Count |
|---:|---|---:|
| 0 | real/original | 1.109 |
| 1 | suspicious/fake-like | 1.109 |

## Split Hint

| Split | Label 0 | Label 1 | Total |
|---|---:|---:|---:|
| train | 776 | 776 | 1.552 |
| valid | 166 | 166 | 332 |
| test | 167 | 167 | 334 |

## Notes

- `text_for_model` berisi teks yang sudah dipreproses.
- `final_label` adalah target modeling.
- `split_hint` disiapkan agar baseline pertama tidak perlu membuat split dari nol.
- Label tambahan berasal dari rule-based candidate labeling. Belum ada validasi internal Shopee.
