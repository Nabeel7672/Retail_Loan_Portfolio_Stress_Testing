# Retail Loan Portfolio Stress Testing

## 📌 Project Overview
This project simulates the financial impact of various economic downturns on a retail loan portfolio. It represents **Phase 2 of my credit risk analysis work**, moving from individual default prediction to **portfolio-wide risk management**.

By applying shocks to borrower **Probability of Default (PD)**, we calculate the potential **Expected Loss (EL)** under different severity levels to evaluate bank stability.

---

## 🔄 Project Evolution: From Prediction to Stress Testing

This repository builds directly upon a previous **Credit Risk Modeling project**.

**Phase 1 – Credit Risk Modeling**
- Developed a **Logistic Regression model** to predict borrower default probability.

**The Bridge**
- Predicted probabilities were exported as `predicted_PD.csv`.

**Phase 2 – Portfolio Stress Testing (This Project)**
- Imported predicted PD values and applied **economic stress scenarios** to simulate portfolio risk.

---

## 🧮 Methodology

### 1. Scenario Definition
Three economic environments were simulated:

| Scenario | Description |
|--------|-------------|
| Baseline | 0% change in income or interest rates |
| Adverse | 10% income decrease, 2% interest rate increase |
| Extreme | 20% income decrease, 4% interest rate increase |

---

### 2. Stressing the Probability of Default (PD)

The predicted probabilities were adjusted using the following formula:

```
PD_stressed = PD_original × (1 + income_decrease + interest_increase)
```

Values were **capped at 1.0** to ensure probabilities do not exceed 100%.

---

### 3. Expected Loss (EL) Calculation

Expected Loss estimates the **potential financial loss faced by a lender**.

```
EL = PD × LGD × EAD
```

Where:

- **PD** = Stressed Probability of Default  
- **LGD (Loss Given Default)** = 40% (industry assumption)  
- **EAD (Exposure at Default)** = Loan amount (`loan_amnt`)

---

## 📊 Results Summary

Portfolio expected loss increases under worsening economic conditions.

| Scenario | Total Expected Loss |
|--------|--------------------|
| Baseline | ~9.11M |
| Adverse | ~10.21M |
| Extreme | ~11.28M |

---

## 📂 Repository Files

```
project/
│
├── Stress_testing.ipynb      # Notebook containing simulation logic
├── predicted_PD.csv          # Output from the Logistic Regression model
├── cr_loan2.csv              # Raw loan dataset used for exposure values
└── README.md
```

---

## 🛠 Tech Stack

- **Python**
- **Pandas**
- **Jupyter Notebook**

Used for **data manipulation, stress scenario simulation, and portfolio risk analysis**.

---

