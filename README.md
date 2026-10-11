# Exploratory Data Analysis (EDA) — FIFA 22 Player Dataset

## 📋 Project Overview & Scope
This project performs rigorous Exploratory Data Analysis (EDA) on the FIFA 22 complete player dataset. The primary objective is to clean raw public data, handle missing values and outliers mathematically, generate professional statistical visualizations, and derive actionable business and scouting insights.

* **Dataset Dimensions:** 19,239 rows and 110 columns.
* **Recommended Stack:** Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook.

---

## 🧹 Data Cleaning & Preprocessing Methodology
1. **Missing Value Treatment:** 
   * Numerical performance metrics lacking values (e.g., specific stats for goalkeepers or non-recorded attributes) were imputed with `0` to maintain dataset shape and structural integrity.
   * Categorical text fields lacking data were standardized to `'Unknown'`.
2. **Outlier Detection & Capping:**
   * Used the **Interquartile Range (IQR)** method on player market values (`value_eur`).
   * Outliers exceeding the upper bound ($Q3 + 1.5 \times IQR$) were treated via **Winsorization (Capping)** rather than dropped, preserving elite talent data while preventing model skewness.

---

## 📊 Key Visualizations & Analytical Insights

### 1. Correlation Heatmap (`correlation_heatmap.png`)
* **Observation:** A strong positive correlation ($0.82$) exists between player `potential` and market `value_eur`. Wage metrics also scale heavily alongside market valuation.
* **Practical Implication:** Clubs evaluating young prospects should heavily weigh projected growth metrics, as overall market evaluation is directly tethered to player ceiling rather than current output alone.

### 2. Player Age Distribution (`age_distribution.png`)
* **Observation:** The age distribution is right-skewed, concentrating the vast majority of professional players between 21 and 28 years old.
* **Practical Implication:** Long-term squad planning must account for a sharp performance drop-off or retirement cluster as players cross the 30-year threshold.

### 3. Ratings by Position Boxplot (`position_boxplots.png`)
* **Observation:** Central Midfielders (CM) and Strikers (ST) exhibit a wider variance in overall ratings, whereas specialized roles maintain tighter performance spreads.
* **Practical Implication:** Scouting departments should allocate a wider search net when acquiring flexible midfield talent due to high performance variability across leagues.

---

## 📂 Deliverables Structure
```text
├── data/
│   └── male_players.csv          # Raw dataset source
├── figures/
│   ├── correlation_heatmap.png   # High-res correlation matrix
│   ├── age_distribution.png      # Age histogram with KDE curve
│   └── position_boxplots.png     # Position vs. overall rating boxplots
├── notebook.ipynb                # Fully executed Jupyter Notebook with markdown commentary
└── README.md                     # Project summary and key insights