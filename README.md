# NovaX — Credit Card Default Risk Analysis

NovaX analyzes customer financial data to identify patterns of loan default risk using data science techniques. The project helps financial institutions make better loan-approval decisions by predicting which customers are likely to default, using the UCI **"Default of Credit Card Clients"** dataset (30,000 rows × 25 columns).

## Project Pipeline

The notebook (`NovaX.ipynb`) is organized into sequential phases, each handled by a different team member.

### 1. Data Engineering (Member 1)
- Loads the raw dataset and validates its shape (handles the known extra header row in the source CSV)
- Cleans column names, fixes data types, removes duplicates, standardizes categories
- Handles missing values and flags/removes invalid records (impossible age, invalid repayment codes)
- Engineers new features: average bill/payment amounts, payment-to-bill ratio, age bands, limit tiers
- Runs a final data-quality check and exports:
  - `cleaned_credit_data.csv` — the cleaned dataset
  - `data_dictionary_cleaned.csv` — column-level data dictionary

### 2. Exploratory Data Analysis (Member 2)
- Loads the cleaned dataset and verifies it's analysis-ready
- Calculates overall default rate with Wilson confidence intervals
- Segments default rate by age, education, marital status, and credit-limit tier
- Analyzes delinquency history (months delayed, max delay) by default outcome
- Ranks repayment-status months by point-biserial correlation with default (early-warning signal strength)
- Runs Mann-Whitney U tests and rank-biserial effect sizes on financial features
- Builds age-band × limit-tier cross-tabulations of default rate

### 3. Data Visualization (Member 3)
- Applies a consistent visual style/color scheme across all charts
- Produces 8+ report-ready charts, including:
  - Default distribution
  - Default rate by age band, education, marital status, credit-limit tier
  - Credit limit and credit-utilisation boxplots by default outcome
  - Default rate vs. months delayed
  - Correlation heatmap of key numeric features
- Exports all figures as PNGs to the `report_figures/` folder

### 4. Risk Model & Segmentation (Member 4)
- Loads the cleaned dataset delivered by Member 1 and re-confirms shape, missing values, and default rate
- Ranks features by absolute Pearson correlation with default to select scoring dimensions
- Builds **3 risk dimension scores (1–5 scale)**, each independently validated against default rate:
  - **Delinquency score** — based on `num_months_delayed` (via `pd.cut`) with a severe-delay bonus for `max_delay_months >= 4`
  - **Capacity score** — based on `payment_to_bill_ratio` (via `pd.qcut`, reversed so low payment ratio = high risk)
  - **Exposure score** — based on `credit_utilisation` (via `pd.qcut`)
- Combines the three scores into a single **composite risk score** using a documented, reusable weighted user-defined function (`compute_overall_risk_score`): 50% delinquency + 30% capacity + 20% exposure
- Maps the composite score to 4 business-friendly **segments**: Healthy (≤2.0), Watchlist (≤2.8), At-Risk (≤3.6), Critical (>3.6)
- Validates the segmentation by confirming default rate increases **monotonically** from Healthy → Critical, and investigates a high-exposure/low-payment risk pocket
- Produces 5 additional charts: feature-correlation bar chart, segment-size bar chart, default-rate-by-segment bar chart, risk-score boxplot by segment, dimension-score validation charts, and a portfolio donut chart
- Exports the fully scored dataset:
  - `segmented_data.csv` — cleaned data plus `delinquency_score`, `capacity_score`, `exposure_score`, `risk_score`, and `segment` columns

**Validated results:** Critical-segment customers default at **~60.8%** versus **~12.7%** for Healthy customers, with Watchlist (~16.7%) and At-Risk (~34.4%) in between — confirming the segmentation is predictive.

### 5. Business Strategy & API Integration (Member 5) — 

Per the project plan, Member 5 takes the segmented dataset from Member 4 and:
- Integrates external economic indicators (e.g., USD exchange rate, inflation) via the `requests` library and a public API such as exchangerate-api
- Merges external data as reference columns or supplementary context for the risk model
- Develops business strategy recommendations tied to each segment, e.g.:
  - **Critical** → reject / require collateral
  - **At-Risk** → approve with higher interest rate
  - **Watchlist** → approve with monitoring
  - **Healthy** → approve on standard terms
- Writes the report's introduction, methodology, and business-insights sections and prepares final presentation slides


## Requirements

```
python >= 3.9
pandas
numpy
matplotlib
seaborn
scipy
```

Install with:
```bash
pip install pandas numpy matplotlib seaborn scipy
```

## Data

Place the raw dataset in the project root as:
```
default of credit card clients - default of credit card clients.csv
```
Running the notebook will generate `cleaned_credit_data.csv` and `data_dictionary_cleaned.csv`, which are used by the later (EDA and visualization) sections.

## Usage

1. Open `NovaX.ipynb` in Jupyter Notebook / JupyterLab / VS Code.
2. Run all cells in order — the Data Engineering section must run first to produce `cleaned_credit_data.csv`.
3. Exported chart images will appear in `report_figures/`.

## Outputs

| File | Description |
|---|---|
| `cleaned_credit_data.csv` | Cleaned, feature-engineered dataset (from Member 1) |
| `data_dictionary_cleaned.csv` | Data dictionary for the cleaned dataset |
| `report_figures/*.png` | Report-ready visualizations (from Member 3) |
| `member4_correlations.png` | Feature correlation with default |
| `member4_segments.png` | Segment sizes, default rate, risk-score boxplot |
| `member4_dimension_validation.png` | Delinquency/capacity score vs. default rate |
| `member4_donut.png` | Portfolio share by segment (donut chart) |
| `segmented_data.csv` | Final dataset with risk scores & segments (from Member 4, → delivered to Member 5) |

## Team

| Member | Role | Status |
|---|---|---|
| Member 1 | Data Engineer — cleaning, feature engineering | ✅ Implemented |
| Member 2 | Data Analyst — exploratory data analysis & statistical testing | ✅ Implemented |
| Member 3 | Visualization Specialist — charts & report figures | ✅ Implemented |
| Member 4 | Risk Model Developer — 3-dimension weighted risk scoring & segmentation | ✅ Implemented |
| Member 5 | Business Analyst + API Developer — external economic data, strategy & recommendations | ✅ Implemented |