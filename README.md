# Telecom Customer Churn Analysis

An analysis of why telecom customers leave: raw CSV → cleaning and analysis in Python → interactive Power BI dashboard with business recommendations.

## Business Problem

Which customers are leaving, and what should the company do to keep them?

## Dataset

[Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) (Kaggle), a sample dataset with 7,043 customers and 21 columns (contract type, tenure, services, monthly charges, payment method and whether the customer left). The CSV file is not included in this repository. Download it from Kaggle.

## Tools

- **Python** (pandas) for cleaning and analysis
- **Power BI** (DAX measures, slicer) for the dashboard

## Process

1. Converted `TotalCharges` from text to numbers. 11 customers had a blank value (all with tenure 0, i.e. brand-new customers who were not billed yet), so these rows were removed, leaving **7,032 customers**.
2. Created a churn flag (1 = left, 0 = stayed) and tenure groups (0-12, 13-24, 25-48, 49-72 months).
3. Calculated the churn rate for each customer group (contract, tenure, internet service, payment method, tech support, senior citizens).
4. Built a Power BI dashboard with DAX measures (Total Customers, Churned Customers, Churn Rate, Avg Monthly Charges, High Risk Churn Rate).

## Key Insights

1. **26.6% of customers left** (1,869 of 7,032), about 1 in 4.
2. **Contract type matters most.** Month-to-month customers churn at **42.7%**, one-year at **11.3%** and two-year at only **2.8%**.
3. **New customers leave the most.** Churn is **47.7%** in the first 12 months and falls to **9.5%** after 49 months.
4. **Highest-risk group:** new customers (12 months or less) on a month-to-month contract. There are 1,994 of them and **51.4% churned**, almost double the overall rate.
5. **Fiber optic customers churn at 41.9%**, compared with 19.0% for DSL.
6. **Electronic check users churn at 45.3%**, while other payment methods are between 15.3% and 19.2%.
7. **Tech support is linked with lower churn:** 15.2% with tech support, 41.6% without.
8. Customers who left paid more per month on average (74.44 vs 61.31), and senior citizens churned more (41.7% vs 23.7%).

These are associations, not proven causes. Many groups overlap (for example a fiber customer may also be on a month-to-month contract and pay by electronic check).

## Recommendations

- Offer discounts to move month-to-month customers to one-year or two-year contracts.
- Give new customers extra support and onboarding in their first 12 months.
- Look into why fiber optic customers leave (price, speed or service quality).
- Encourage automatic payments instead of electronic checks.
- Offer tech support free or at a low price to high-risk customers.

## Dashboard

![Telecom Customer Churn Dashboard](images/churn_dashboard.png)

## Project Structure

```
├── churn_analysis.ipynb     # Data cleaning and analysis in Python
├── powerbi/
│   └── churn_dashboard.pbix
├── images/
│   └── churn_dashboard.png
└── README.md
```

## How to Run

1. Download the dataset from Kaggle and place the CSV in the same folder as the notebook.
2. Install the libraries: `pip install pandas`
3. Run `churn_analysis.ipynb`. It saves a cleaned file, `churn_clean.csv`.
4. Open `powerbi/churn_dashboard.pbix` in Power BI Desktop. If the data source path is different on your computer, update it in *Transform data → Data source settings*.

## Author

**Md Safdar Hossain**
GitHub: [safdar767](https://github.com/safdar767)
Portfolio: [md-safdar-hossain.netlify.app](https://md-safdar-hossain.netlify.app)
