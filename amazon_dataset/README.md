# Amazon Fashion Dataset

Data is **not stored in the repo** (too large). To match the project’s current layout, obtain the fashion reviews file and place it as below.

## Source

- **Option 1 (recommended):** [Amazon Reviews (2023) – Fashion](https://www.kaggle.com/datasets/karkavelrajaj/amazon-reviews-2023) or similar Kaggle “Amazon Fashion” / “Amazon Reviews” dataset that provides a single JSONL file for fashion.
- **Option 2:** [UCSD Amazon Review Data](https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/) (McAuley et al.) – use the **Fashion** subset and convert/save as one `.jsonl` if the project expects a single file.

## Target layout (same as current instantiation)

Place the file so the structure is:

```
amazon_dataset/
├── README.md           (this file)
└── Amazon_Fashion.jsonl
```

## Steps

1. Download the **Amazon Fashion** reviews dataset from one of the sources above.
2. If you get a single file named something else (e.g. `Fashion.jsonl` or `reviews_Fashion.jsonl`), copy or rename it to:
   - `676_Project/amazon_dataset/Amazon_Fashion.jsonl`
3. If you get multiple files (e.g. by category or chunk), concatenate or select the fashion reviews and save as `Amazon_Fashion.jsonl` in `676_Project/amazon_dataset/`.

After this, `AMAZON_DIR` will point at the same layout as the current instantiation.
