# Credit Card Portfolio Default Risk Analysis

> A comprehensive end-to-end Risk Analysis Dashboard built with Excel and Power BI to monitor portfolio health and identify high-risk segments.


## Project Overview

This project aims to simulate a real-world credit risk monitoring workflow. Based on the [UCI Default of Credit Card Clients Dataset](https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients), I developed a **Credit Risk Dashboard** that transforms raw transactional data into actionable insights.

**Key Objectives:**
- **Data Quality:** Handle missing values, outliers (e.g., negative bill amounts), and inconsistent coding in repayment history.
- **Risk Modeling:** Construct a custom risk scoring model using behavioral features (utilization, delinquency).
- **Visual Monitoring:** Provide interactive views for executives (KPIs) and credit officers (client detail/early warning).

## Dataset

**Source:** [UCI Machine Learning Repository - Default of Credit Card Clients](https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients)

**Description:**
This project utilizes a real-world dataset containing credit card default data for clients in Taiwan from April 2005 to September 2005.

- **Volume:** 30,000 records (rows).
- **Target Variable:** `default payment next month` (1 = Yes, 0 = No).
- **Key Features:**
  - **Demographic:** Gender, Education, Marital Status, Age.
  - **Financial:** Credit Limit (`LIMIT_BAL`), Bill Statements (`BILL_AMT`), Previous Payments (`PAY_AMT`) over 6 months.
  - **Repayment History:** Payment status tracking (`PAY_0` to `PAY_6`) including delay months.

## Tech Stack & Tools

- **Data Processing:** Microsoft Excel (Advanced Formulas, Table Structures)
- **BI & Visualization:** Power BI Desktop
- **Logic Implementation:** DAX Measures, Calculated Columns, Conditional Formatting

## Key Features

### 1. Robust Data Cleaning & Feature Engineering
- Dealt with anomalous data in repayment status (e.g., interpreting codes -2, 0) and negative bill statements (credit balances) to ensure accurate metric calculation.
- Created behavioral features such as **6-Month Average Utilization** and **Max Overdue Months** to capture long-term risk trends.

### 2. Custom Risk Scoring System
- Developed a rule-based scoring card from scratch (Base 100) with penalties for high utilization and historical delinquency.
- Segmented customers into **Low / Medium / High** risk grades.
- *Validation:* The "High" risk group showed a default rate of **~58.9%**, significantly outperforming the portfolio average of **22.1%**.

### 3. Interactive Dashboard Design
- **Overview Page:** High-level portfolio health metrics and trends.
- **Analysis Page:** Deep dive into risk factors (Utilization vs. Risk, Demographics).
- **Detail Page:** Operational matrix with RAG (Red-Amber-Green) conditional formatting for immediate target identification.

## Project Structure

```text
Credit-Card-Portfolio-Default-Risk-Analysis/
├── data/
│   ├── credit_card_final_ready_for_PBI.xlsx
│   ├── credit_card_raw_original.xlsx
│   └── credit_card_working_v1.xlsx
├── docs/
│   └── References/
│       └── Yeh and Lien - 2009 - The comparisons of data mining techniques for the predictive accuracy of probability of default of c.pdf
├── README.md
├── powerbi/
│   └── Dashboard of Credit Card Portfolio Default Risk Analysis.pbix
├── screenshots/
│   └── pics/
│       ├── Screenshot.Dashboard of Credit Card Portfolio Default Risk Analysis.pbix.01.png
│       ├── Screenshot.Dashboard of Credit Card Portfolio Default Risk Analysis.pbix.02.png
│       ├── Screenshot.Dashboard of Credit Card Portfolio Default Risk Analysis.pbix.03.png
│       ├── Screenshot.credit_card_final_ready_for_PBI.xlsx.png
│       └── Screenshot.credit_card_raw_original.xlsx.png
├── Screenshots and brief notes.md
├── LICENSE
```

## Dashboard Preview

*(For detailed steps on data cleaning logic and DAX formulas, please refer to [Screenshots and brief notes.md](./docs/Screenshots%20and%20brief%20notes.md))*

## Getting Started

1.  Clone this repository.
2.  Download the `.pbix` file from the `/powerbi` folder.
3.  Open with **Power BI Desktop**.
4.  Use the slicers and filters to interact with the data.

## Future Improvements

- [ ] Integrate Machine Learning models (e.g., Logistic Regression) to refine Probability of Default (PD).
- [ ] Apply more advanced data processing methods pertaining to Python and R, add real-time monitors.
- [ ] Expand the dataset to include macroeconomic variables.

## References

1.  **Dataset Source:** UCI Machine Learning Repository. (2005). *Default of Credit Card Clients Data Set*.
2.  **Original Paper:** Yeh, I. C., & Lien, C. H. (2009). The comparisons of data mining techniques for the predictive accuracy of probability of default of credit card clients. *Expert Systems with Applications*, 36(2), 2473-2480.

## Author

**Anon Oby (HE ZHIXIONG)**
- Aspiring Financial Risk Analyst (Work email: mahamahaanonoby@outlook.com)
- [Medium Profile Link](https://medium.com/@anonoby63)
- [Substack Profile Link](https://substack.com/@anonoby?)
