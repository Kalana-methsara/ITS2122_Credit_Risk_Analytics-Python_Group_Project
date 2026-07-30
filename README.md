Data Cleaning & Preprocessing

Performed data preparation tasks:

- Loaded dataset using Pandas
- Checked dataset structure using:
  - `info()`
  - `describe()`
  - `value_counts()`
- Renamed columns into meaningful names
- Converted categorical codes into readable labels:
  - Gender
  - Education
  - Marriage status
- Checked and removed duplicate records
- Validated data values

---

## Feature Engineering

Created new behavioural features:

### Average Bill Amount

Calculates the average monthly bill amount across six months.

```
avg_bill_amount
```

### Average Payment Amount

Calculates the average monthly payment amount.

```
avg_payment_amount
```

### Payment to Bill Ratio

Measures repayment capacity.

```
payment_to_bill_ratio
```

### Delayed Months

Counts the number of months with payment delays.

```
delayed_months
```

### Age Group

Customers were categorized into:

- Young Adult
- Middle-Aged
- Senior-Aged
- Elderly

---
