# Synerise RecSys 2025 Challenge Dataset

Data is **not stored in the repo** (too large). To match the project’s current layout, download and place files as below.

## Source

- **Challenge:** [RecSys 2025 by Synerise](https://recsys.synerise.com/)
- **Dataset / sign-up:** [recsys.synerise.com – data set](https://recsys.synerise.com/data-set) (registration may be required)

## Target layout (same as current instantiation)

Place files so the structure is:

```
challenge_dataset/
├── README.md                    (this file)
├── product_properties.parquet
├── input/
│   ├── add_to_cart.parquet
│   ├── page_visit.parquet
│   ├── product_buy.parquet
│   ├── relevant_clients.npy
│   ├── remove_from_cart.parquet
│   └── search_query.parquet
└── target/
    ├── active_clients.npy
    ├── popularity_propensity_category.npy
    ├── popularity_propensity_new_sku.npy
    ├── popularity_propensity_price.npy
    ├── popularity_propensity_sku.npy
    ├── propensity_category.npy
    ├── propensity_new_sku.npy
    ├── propensity_price.npy
    ├── propensity_sku.npy
    ├── train_target.parquet
    └── validation_target.parquet
```

## Steps

1. Download the Synerise RecSys 2025 dataset from the link above (e.g. as a zip or split archives).
2. Unpack so that:
   - All **event parquet** files and `relevant_clients.npy` are in `676_Project/challenge_dataset/input/`.
   - `product_properties.parquet` is in `676_Project/challenge_dataset/`.
   - All **target** `.npy` and target parquet files are in `676_Project/challenge_dataset/target/`.
3. If the official pack uses different folder names (e.g. `train/` or `test/`), move or copy files into the `input/` and `target/` paths above so the names match exactly.

After this, the notebook’s `CHALLENGE_DIR` will resolve to the same structure as in the current repo.
