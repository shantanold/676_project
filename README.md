# The Aspiration Descent: Price Trajectory Mining for E-commerce Conversion Prediction

**CSCE 676: Data Mining — Texas A&M University**

Does the way a shopper moves through price tiers during a single session reveal whether they will buy? We mined 300K+ shopping sessions from a real-world fashion e-commerce event log to find out. Using FP-Growth for unordered co-occurrence patterns and PrefixSpan for ordered sequential patterns, we discovered that **tier commitment** — repeatedly adding items from the same price band — is the strongest behavioral signal of purchase intent, with mid-tier repetition (Mid→Mid→Mid) converting at 1.67x the rate of abandoned sessions.

---

## Start here

**The main deliverable is [`main_notebook.ipynb`](main_notebook.ipynb)** — it walks through the full analysis from data preparation to conclusions, with narrative throughout.

**Project video:** [Watch on YouTube](https://www.youtube.com/watch?v=RVF4_KB3dA8)

---

## Research Questions

1. Does a shopper's price-tier trajectory within a session (moving from high-price to low-price items) predict whether that session converts to a purchase?
2. Which ordered price-tier sequences distinguish converting sessions from abandoned ones?
3. Are these patterns temporally stable across the five-month observation window?

---

## Results Summary

- 23.2% overall conversion rate across ~296K cart-active sessions
- Descending price trajectories convert at 25.7% vs. 19.5% for Mixed/Stable (statistically significant, weak effect: Cramér's V = 0.036)
- FP-Growth found one multi-tier co-occurrence pattern: Budget + Mid at 1.31x support ratio
- PrefixSpan found 9 ordered patterns; the strongest is Mid→Mid→Mid (1.67x)
- The original aspiration-descent hypothesis (premium anchoring → budget settlement) is not supported at scale; tier commitment is the real signal
- Temporal trend test is inconclusive due to low power at n=6 months; a mild upward drift in Descending conversion rates (τ=+0.733, p=0.056) may reflect holiday seasonality

---

## Repo Structure

```
.
├── main_notebook.ipynb          # Final curated analysis (start here)
├── requirements.txt             # Colab environment snapshot
├── make_slides.py               # Script to generate the 2-minute pitch deck (python-pptx)
├── README.md
├── .gitignore
├── checkpoints/
│   ├── checkpoint_1.ipynb       # Checkpoint 1: dataset comparison + Synerise EDA
│   └── checkpoint_2.ipynb       # Checkpoint 2: research question formulation + early analysis
├── challenge_dataset/
│   └── README.md                # Download instructions for Synerise RecSys 2025 data
├── h_m_dataset/
│   └── README.md                # Download instructions for H&M dataset (explored, not used)
└── amazon_dataset/
    └── README.md                # Download instructions for Amazon Fashion (explored, not used)
```

---

## Data

**Primary dataset:** Synerise RecSys 2025 — Fashion E-commerce Event Log

The dataset contains timestamped e-commerce events (add-to-cart, remove-from-cart, product-buy, page-visit) from a major European fashion retailer, spanning June–November 2022. Product names and categories are anonymized; `price` is the only interpretable numeric feature.

**Download:** Request access at [recsys.synerise.com](https://recsys.synerise.com). Once downloaded, place the files so the layout matches:

```
challenge_dataset/
├── input/
│   ├── add_to_cart.parquet
│   ├── remove_from_cart.parquet
│   ├── product_buy.parquet
│   ├── page_visit.parquet
│   └── search_query.parquet
└── product_properties.parquet
```

The notebook points to `/content/drive/MyDrive/CSCE676/FinalProject/dataset_project/` (Colab + Google Drive). Update `PROJECT_ROOT` in Section 0 to match your local path.

Two additional datasets were explored during the checkpoint phase and are not used in the final analysis:
- **H&M Personalized Recommendations** — [Kaggle](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data)
- **Amazon Fashion** — [McAuley Lab](https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/)

All large data files are excluded from the repo via `.gitignore`.

---

## How to Reproduce

This project was built in **Google Colab** with Python 3.12.

1. Upload `main_notebook.ipynb` to Colab.
2. Mount your Google Drive and place the Synerise dataset as described above.
3. Run `pip install prefixspan mlxtend seaborn scipy` (already in the first cell).
4. Run all cells in order from top to bottom.

Full environment: see [`requirements.txt`](requirements.txt).

---

## Key Dependencies

| Package | Version |
|---|---|
| Python | 3.12 |
| pandas | 2.2.2 |
| numpy | 2.0.2 |
| scipy | 1.16.3 |
| scikit-learn | 1.6.1 |
| mlxtend | 0.23.4 |
| prefixspan | 0.5.2 |
| matplotlib | 3.10.0 |
| seaborn | 0.13.2 |
| pyarrow | — |

---

## Citations

- Han, J., Pei, J., & Yin, Y. (2000). Mining frequent patterns without candidate generation. *SIGMOD Record*, 29(2), 1–12.
- Pei, J., Han, J., Mortazavi-Asl, B., et al. (2001). PrefixSpan: Mining sequential patterns by prefix-projected pattern growth. *ICDE*, 215–224.
- Kendall, M. G. (1975). *Rank Correlation Methods* (4th ed.). Griffin.
