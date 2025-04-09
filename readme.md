
# 💰 American Option Pricing using Binomial Method

> Predicting fair value of participation rights in a real asset using the **Binomial Method for American Options**. This project simulates the price of an option using real-world assumptions on capex, financial structures, and asset price movements.

---

## 📌 Project Overview

ABC Company uses **American call option pricing (binomial model)** to determine the fair value of Company XYZ's participation rights in Project X. The participation right is valid for 5 years, during which ABC can purchase 30% of the underlying asset at any point in time.

---

## 📘 What is an Option?

An **option** is a financial contract allowing the buyer to buy or sell an underlying asset at a predefined price (strike price) before or at expiration. The buyer is **not obligated** to execute the contract.

---

## 🗽 What is an American Option?

An **American option** allows execution at **any time** before or on expiration. This differs from a **European option**, which can only be exercised on the expiration date.

---

## 🧮 Formula Overview

- **Budgeted Capex Cost** = Base Price × (1 + Interest) × FX Adjustment × Incentives × Nameplate Capacity  
- **Exercise Price** = (Budgeted Capex Cost - Capex Loan - Accrued Capex) - First PR Deduction  
- **Option Price** = max(Underlying Asset Value - Exercise Price, 0)

---

## 📈 Business Assumptions

- Project X has a 20-year lifetime but XYZ's participation right only lasts 5 years.
- Capex and asset values are estimated and adjusted every 6 months.
- The option is based on the assumption that future value of the project decreases over time.

---

## 🛠️ Libraries

```python
import pandas as pd
import numpy as np
```

---

## ⚙️ Input Assumptions

- Duration: 5 years
- Trading days/year: 252
- 6-month parameter updates for: base price, interest, FX adjustment, incentives, capex loan, and others.

The 6-month values are converted to daily using a helper function and then used in capex calculations.

---

## 🧠 Core Calculations

### 🧾 Budgeted Capex

```python
budgetedCapex = basePrice * ((1 + interest) * fxAdjustment + incentives) * nameplateCapacity
budgetedCapex /= 1e6  # in million USD
```

### 🧾 Exercise Price

```python
exercisePrice = budgetedCapex - capexLoan - accruedCapex - firstprDeduction
exercisePrice *= 0.3  # 30% stake in asset
```

### 📉 Option Pricing Logic (Binomial)

```python
volatility = 0.5282
rf = 0.0438  # risk-free rate
dt = period / numberofDays
...
# Loop through binomial tree to calculate optionPrice[j][i]
```

---

## 📊 Final Result

```text
Option Price: 710.01 million USD
```

✅ This is the fair price for ABC to acquire 30% of the underlying asset over 5 years.

---

## 📁 Repository Structure

```
American_Option_Price/
├── main.ipynb       # Full pricing simulation
└── readme.md        # You're here
```

---

## 👤 Author

**Alexander Tiopan**  
📧 alexandertiopan1212@gmail.com  
🔗 GitHub: [alexandertiopan1212](https://github.com/alexandertiopan1212)

