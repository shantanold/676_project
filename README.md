# CSCE 676 – Data Mining Project

Fashion & E-commerce project: dataset comparison, selection, and exploratory data analysis (EDA) for the Synerise RecSys 2025 challenge.

## Repo contents

| Path | Description |
|------|-------------|
| `Project_Checkpoint1_EDA.ipynb` | Checkpoint 1: comparative analysis + Synerise EDA (funnel, sparsity, temporal, Zipf) |
| `challenge_dataset/` | Synerise RecSys 2025 data (see below – **not in repo**) |
| `h_m_dataset/` | H&M Personalized Recommendations (see below – **not in repo**) |
| `amazon_dataset/` | Amazon Fashion reviews (see below – **not in repo**) |

## Setup

1. **Clone the repo**
   ```bash
   git clone https://github.com/YOUR_USERNAME/CSCE676-676_Project.git
   cd CSCE676-676_Project
   ```

2. **Install dependencies**
   ```bash
   pip install pandas pyarrow matplotlib seaborn numpy
   ```

3. **Download datasets** (not stored in GitHub due to size):
   - **Synerise RecSys 2025:** [recsys.synerise.com](https://recsys.synerise.com/data-set) – place contents so `challenge_dataset/input/` contains the event parquet files.
   - **H&M:** [Kaggle – H&M Personalized Fashion Recommendations](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data) – place `articles.csv`, `customers.csv`, `transactions_train.csv` in `h_m_dataset/`.
   - **Amazon Fashion:** e.g. [Amazon Fashion (McAuley)](https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/) or Kaggle – place the review file in `amazon_dataset/`.

4. **Run the notebook**
   - Open `Project_Checkpoint1_EDA.ipynb` in Jupyter or VS Code.
   - Run cells in order; the data-loading cell uses a 10% sample by default to avoid OOM.

## License

Course project; dataset use follows each source’s terms (Synerise challenge, Kaggle, research licenses).
