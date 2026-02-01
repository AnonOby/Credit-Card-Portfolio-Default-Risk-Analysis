# Screenshots and brief notes

## 1. Data Acquirement
![Screenshot.credit_card_raw_original.xlsx](./pics/Screenshot.credit_card_raw_original.xlsx.png)
Sourced the primary dataset from the **UCI Machine Learning Repository** (Default of Credit Card Clients). The raw data comprises 30,000 records, featuring demographic attributes, credit limits, repayment history (-2 to 9 months), bill statements, and actual payment amounts. This serves as the foundation for modeling portfolio credit risk.

## 2. Data cleaning & Feature Engineering
![Screenshot.credit_card_final_ready_for_PBI.xlsx](./pics/Screenshot.credit_card_final_ready_for_PBI.xlsx.png)
Implemented rigorous data preprocessing in Excel to enhance model robustness and business logic alignment:

- **Data Normalization & Outlier Handling:**
  - Addressed non-standard encoding in repayment history (`PAY_X`), explicitly interpreting values like `-2` and `0` as "non-delinquent" (e.g., no usage, paid in full) to distinguish them from actual overdue cycles.
  - Encountered negative bill amounts representing credit balances (refunds). To prevent distortion in risk modeling, the **Utilization Rate** logic was refined to cap these values at `0%`.

- **Feature Construction:**
  - **Utilization Metrics:** Computed monthly utilization ratios using dynamic Excel Table structures. Subsequently, a calculated column `Avg_Util_6m` was derived in Power BI DAX to capture sustained credit usage behavior over 6 months.
  - **Risk Scoring Model:** Developed a rule-based **Risk Score** (Base 100) with penalty deductions:
    - *Severity-based penalties*: -40 for >2 months overdue, -20 for 1-2 months overdue.
    - *Leverage penalties*: -20 for utilization exceeding 80%.
  - **Optimized Delinquency Metrics:** Constructed `Max_Overdue_Months` using optimized logic (`IF(MAX(...))`) to strictly identify the "worst-case" historical behavior while filtering out non-delinquent codes.

- **Data Granularity:**
  - Identified and preserved anomalous codes in the `Education` field (`0`, `5`, `6`). Rather than deletion, these were mapped to "Unknown/Other" to maintain data integrity for segmentation analysis.

## 3. Data Analysis with Power BI
![Screenshot.Dashboard of Credit Card Portfolio Default Risk Analysis.pbix.01](./pics/Screenshot.Dashboard%20of%20Credit%20Card%20Portfolio%20Default%20Risk%20Analysis.pbix.01.png)
![Screenshot.Dashboard of Credit Card Portfolio Default Risk Analysis.pbix.02](./pics/Screenshot.Dashboard%20of%20Credit%20Card%20Portfolio%20Default%20Risk%20Analysis.pbix.02.png)
![Screenshot.Dashboard of Credit Card Portfolio Default Risk Analysis.pbix.03](./pics/Screenshot.Dashboard%20of%20Credit%20Card%20Portfolio%20Default%20Risk%20Analysis.pbix.03.png)
Constructed an interactive three-page dashboard to monitor portfolio health and enable granular drill-down:

- **Page 01: Overview**
  - Defined key KPIs: **Total Customers**, **Default Rate** (~22.1%), and **Avg Risk Score**.
  - Validated the scoring model's effectiveness: The "High" risk segment demonstrated a **Default Rate of ~58.9%**, nearly 3x the portfolio average, confirming strong predictive power.

- **Page 02: Risk Analysis**
  - **Utilization vs. Risk:** Binned `Avg_Util_6m` into discrete ranges. Visualized an exponential correlation: users with >80% usage showed significantly elevated default rates.
  - **Historical Impact:** Used Clustered Bar Charts to illustrate that even minor historical delinquency (>0 months) drastically increases future default probability compared to clean records.
  - **Demographic Segmentation:** Analyzed `Education` and `Gender` attributes, retaining specific attention to "Unknown" categories to detect potential data bias or hidden risks.

- **Page 03: Client Detail & Early Warning**
  - Designed an operational matrix for credit officers.
  - Applied **Conditional Formatting (RAG)** to `Risk_Grade` and `DefaultFlag` for instant visual prioritization (Red for High Risk/Defaulted).
  - Utilized the **Filters Pane** to enable rapid isolation of high-risk targets (e.g., filtering by `Risk_Grade="High"`), bridging the gap between analytics and enforcement.
```
