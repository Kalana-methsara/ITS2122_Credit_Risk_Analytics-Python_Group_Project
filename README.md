# Phase 4 – Strategic Recommendations

## Overview

This phase focuses on transforming the analytical results from previous phases into practical business strategies. 
The analysis evaluates customer credit utilisation, financial exposure, and repayment behaviour to provide actionable recommendations 
for reducing credit default risk.

---

## Objectives

- Calculate customer Credit Utilisation.
- Analyze the relationship between credit utilisation and default risk.
- Compare financial exposure across customer segments.
- Generate strategic business recommendations for each customer segment.

---

## Dataset

Input Dataset:
- `cleaned_credit_risk_data.csv`

Required Features:
- `limit_balance`
- `avg_bill_amt`
- `pay_to_bill_ratio`
- `delayed_months_count`
- `default_next_month`

---

## Credit Utilisation

Credit Utilisation represents the percentage of the available credit limit currently being used by a customer.

Formula:

Credit Utilisation (%) = (Average Bill Amount / Credit Limit) × 100

A higher utilisation percentage generally indicates greater financial exposure and a higher likelihood of default.

---

## Analysis Performed

### 1. Credit Utilisation Calculation

A new feature named `credit_utilisation` was created using the customer's average bill amount and credit limit.

### 2. Customer Risk Segmentation

Customers were categorized into four financial health groups:

- Healthy
- Watchlist
- At-Risk
- Critical

The segmentation is based on:

- Number of delayed payment months
- Payment-to-Bill Ratio
- Credit Utilisation

### 3. Exposure Analysis

Average values of:

- Credit Utilisation
- Credit Limit
- Average Bill Amount

were compared across all customer segments to identify financial exposure.

### 4. Default Rate Analysis

The default percentage of each customer segment was calculated to evaluate the relationship between customer behaviour and repayment risk.

---

## Visualizations

The following visualizations were generated:

- Credit Utilisation Distribution (Histogram)
- Credit Utilisation by Customer Segment (Box Plot)

These visualizations help identify utilisation patterns and compare financial behaviour among customer segments.

---

## Business Recommendations

### Healthy Customers
- Reward loyalty
- Offer cashback programs
- Consider credit limit increases

### Watchlist Customers
- Send payment reminders
- Monitor repayment behaviour
- Provide budgeting guidance

### At-Risk Customers
- Review credit limits
- Offer installment payment plans
- Provide repayment restructuring options

### Critical Customers
- Immediate intervention
- Debt restructuring
- Financial counselling
- Restrict additional credit until repayment improves

---

## Technologies Used

- Python
- Pandas
- Matplotlib
- Seaborn

---

## Expected Business Value

This analysis enables financial institutions to:

- Identify high-risk customers early.
- Reduce future default rates.
- Improve credit management decisions.
- Increase customer retention through personalized strategies.
- Minimize financial losses by applying risk-based interventions.

---

## Author

**Thakshila Kavindi**

Phase 4 – Strategic Recommendations & Credit Utilisation Analysis
