## Phase 2: Exploratory Data Analysis (EDA)

In this phase, we thoroughly explore the cleaned credit risk dataset to uncover underlying trends, behavioral patterns, and correlations between customer financial metrics and the target risk variable (`default_next_month`).

### 📊 Key Analysis Steps & Insights:

* **1. Initial Inspection & Summary**
  * Loaded the dataset and examined its structural integrity (`shape`, `info`), validating data types and checking for null values.
  * Generated a comprehensive statistical summary (`describe`) to understand the baseline distribution of numerical features.

* **2. Target Variable Distribution**
  * Visualized the class balance of the target variable (`default_next_month`) using a combined **Pie Chart** and **Count Plot**.
  * Quantified the exact overall default rate to assess dataset skewness and its potential impact on predictive model performance.

* **3. Demographic Risk Propensity Analysis**
  * Evaluated how various customer background traits correlate with financial default risk through a multi-panel comparison grid:
    * **Gender:** Comparing default tendencies between male and female segments.
    * **Education Level:** Analyzing risk variations across different educational attainment tiers.
    * **Age Groups:** Identifying vulnerable or high-risk age brackets.
    * **Marital Status:** Exploring how marital status influences financial reliability.

* **4. Correlation & Multicollinearity Assessment**
  * Constructed a specialized **Correlation Heatmap** (`coolwarm`) focusing on key financial metrics (credit limits, ages, bill amounts, repayment histories, and default statuses).
  * Identified linear dependencies and structural relationships to prevent multicollinearity issues prior to model training.

* **5. Advanced Behavioral & Financial Visualizations**
  * **Viz 5 (Credit Limit Distribution):** Used boxplots to compare credit limit balances between defaulters and non-defaulters.
  * **Viz 6 (Age-based Frequencies):** Tracked default concentrations across detailed age segments.
  * **Viz 7 (Payment Delays Impact):** Measured the direct risk escalation caused by the total number of delayed payment months.
  * **Viz 8 (Bill vs. Payment Scatter Plot):** Examined spending behavior by plotting average bill amounts against average payment amounts (with a focused zoom on lower ranges).
