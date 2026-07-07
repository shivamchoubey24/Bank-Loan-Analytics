# Bank Loan Analytics Dashboard

An interactive Power BI dashboard that monitors a bank's lending portfolio — tracking loan volume, funding, repayment health, and risk indicators across time, geography, and loan purpose — to support data-driven lending decisions.

## 📌 Project Overview

Banks need continuous visibility into their loan book: how much is being lent, how much is coming back, and where risk is concentrated. This project builds a two-page Power BI report that turns 38,500+ raw loan records into a live, filterable view of the bank's lending performance — replacing static, backward-looking reports with a self-serve analytics tool.

## 🎯 Objective

Per the project's problem statement, the dashboard is designed to:
- Monitor and assess the bank's lending activity and performance over time
- Track loan portfolio health through the **Good Loan vs. Bad Loan** lens (are loans being repaid, or charged off?)
- Break down applications and funding by loan purpose, term, home ownership status, state, and month
- Give stakeholders a single source of truth for lending KPIs instead of manual reporting

## 🗂️ Dataset

- **Source:** Bank loan/lending records — [`Financial_loan_data.xlsx`](./Financial_loan_data.xlsx)
- **Size:** 38,576 loan applications, 23 fields
- **Key fields:** `ISSUE_DATE`, `PURPOSE`, `VERIFICATION_STATUS`, `GRADE`/`SUB_GRADE`, `HOME_OWNERSHIP`, `ADDRESS_STATE`, `LOAN_STATUS`, `EMP_LENGTH`, `TERM`, `ANNUAL_INCOME`, `DTI`, `INSTALLMENT`, `INT_RATE`, `LOAN_AMOUNT`, `TOTAL_PAYMENT`, `TOTAL_ACC`
- Full column dictionary and business definitions: [`Bank_Loan_Description.pdf`](./Bank_Loan_Description.pdf)

## 🛠️ Tools & Techniques

| Area | Details |
|---|---|
| **Tool** | Microsoft Power BI Desktop |
| **Pages** | 2-page report — **Summary** (portfolio health) and **Overview** (application trends & breakdowns) |
| **DAX Measures** | Total Loan Applications, Total Funded Amount, Total Amount Received, Average Interest Rate, Average DTI Ratio, Good Loan % / Bad Loan % (based on `LOAN_STATUS`) |
| **Visuals** | KPI cards, donut charts (Good vs. Bad loan split), clustered column charts (by loan status), line chart (monthly application trend), filled map (applications by state), treemap (applications by purpose), horizontal bar chart (by home ownership), donut chart (by term) |
| **UX / Design** | Custom dark theme (`#0B0D12` canvas, `#11151C` visual background, `#F5A524` gold accent) for a modern fintech look; button-based page navigation (Summary / Overview); purpose-based slicer buttons (Car, Credit Card, Debt Consolidation, Education, Home Improvement, etc.) with a Reset Filters button |

## 📊 Key Insights

- **38,576 total loan applications**, with **$435.8M funded** and **$473.1M received back**
- **86.18% of loans are classified as "Good"** (Current or Fully Paid) vs. **13.82% "Bad"** (Charged Off) — the bank's core portfolio health metric
- Charged-off loans still carry a real cost: **$65.5M funded** against them, with only **$37.3M recovered**
- Average interest rate sits at **12.05%**, with charged-off loans carrying a noticeably higher average rate (13.9%) than fully-paid loans (11.6%) — consistent with risk-based pricing
- Average DTI (debt-to-income) ratio is **13.33%**, and again trends higher for charged-off loans than for fully-paid ones
- Monthly loan applications show a **consistent upward trend across the year**, nearly doubling from ~2,300 in January to ~4,300 in December
- **Debt Consolidation** is by far the top loan purpose (18K applications), followed by Credit Card
- Most borrowers are renters (18,439) or have a mortgage (17,198), with very few outright homeowners applying (2,838)
- 36-month terms make up **73.2%** of applications vs. 26.8% for 60-month terms

## 🖱️ Dashboard Features

- **Page navigation:** toggle between Summary and Overview via in-report buttons
- **Purpose filters:** one-click slicer buttons for every loan purpose (Car, Medical, Vacation, Wedding, etc.) with a Reset Filters button
- **Cross-filtering:** all charts filter each other when a value is selected
- **Geospatial view:** filled map of loan applications by U.S. state
- **Good vs. Bad loan comparison cards:** side-by-side KPI breakdown for portfolio risk monitoring

## 🚀 How to Use

1. Download [`Bank_Loan_Analytics_Dashboard.pbix`](./Bank_Loan_Analytics_Dashboard.pbix)
2. Open in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
3. Use the purpose slicer buttons on the left to filter the whole report
4. Switch between the **Summary** and **Overview** pages using the top navigation buttons
5. Click **Reset Filters** to clear selections

## 📁 Repository Structure

```
├── Bank Loan Analytics Dashboard.pbix   # Power BI project file
├── Financial loan data.xlsx             # Source dataset (38,576 records)
├── Bank Loan Description.pdf            # Column dictionary & business context
├── screenshot-summary.png               # Summary page preview
├── screenshot-overview.png              # Overview page preview
└── README.md
```

## 🔮 Possible Next Steps

- Add a drill-through page per loan grade (A–G) to analyze risk-tier performance
- Build a cohort view of charge-off rate by issue month to spot seasonal risk patterns
- Layer in a simple credit-risk score model using DTI, income, and employment length
