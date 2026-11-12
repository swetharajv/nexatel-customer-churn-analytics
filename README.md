# NexaTel Customer Churn Analytics

An end-to-end data analytics project on a telecom customer dataset: data cleaning, exploratory analysis, KPI calculation, a 5-page Power BI dashboard and a management report. Built as part of the Internmo Data Analyst internship program.

**Business question:** why do NexaTel customers leave, which customers are most at risk, and what should the company do about it?

## Headline findings

- **Churn is low but rising.** Monthly churn averages 0.65% (target: under 2.1%), but it climbed from 0.44% in April 2025 to 1.25% in March 2026.
- **It is getting more expensive.** Customers who churned in the last 12 months took about Rs.7.7 lakh of monthly recurring revenue with them (roughly Rs.93 lakh a year). The monthly revenue lost grew from Rs.31,972 to Rs.122,854 between April 2025 and March 2026.
- **Unresolved complaints go with much higher churn.** Customers with no unresolved complaint churn at 15.1%. With three or more, churn is 48.3%.
- **Support is the weak spot.** Only 40.4% of tickets are resolved on first contact (target: over 78%), and 44.3% of complaints are unresolved.
- **Churn is concentrated.** Mass-segment customers churn at 26.7% against 11.9% for Enterprise, and Monthly-plan customers churn at 22.5% against 7.2% for Annual plans.

All findings show associations, not proof of cause. See *Assumptions and limitations* below.

## KPIs (Phase 3)

| KPI | Value | Target |
|---|---|---|
| Monthly churn rate (12-month average) | 0.65% (March 2026: 1.25%) | under 2.1% |
| Monthly retention rate | 99.33% | none |
| ARPU | Rs.970 per customer per month | none |
| Customer lifetime value | Rs.60,007 (at an assumed 40% gross margin) | none |
| Revenue lost to churn | Rs.774,988 per month (last 12 months) | none |
| Monthly recurring revenue | Rs.15,031,009 | none |
| First contact resolution | 40.4% | over 78% |
| Average resolution time | 16.0 hours | under 24 hours |
| Contract renewal rate (postpaid and fibre) | 84.0% | over 88% |
| Average tenure (active customers) | 87.1 months | none |

## What I did

| Phase | Work | Output |
|---|---|---|
| 1. Cleaning | Loaded and profiled all 24 tables, then checked and fixed the 20 data-quality issues in the project's issue log. 18 of 20 matched the log exactly; the two that did not (missing emails: 744 found vs 760 logged; capitalisation errors: 560 vs 570) are reported as not reproducible. An 11-check self-test confirms the saved clean files. | `notebooks/Phase1_DataCleaning_Swetha.ipynb` |
| 2. EDA | 10 charts on churn by segment, billing cycle, tenure, complaints, state, data usage, plan price, network quality and retention campaigns, each with a written observation. | `notebooks/Phase2_EDA_Swetha.ipynb`, `charts/` |
| 3. KPIs | 10 KPIs calculated month by month over April 2025 to March 2026, with a summary table against the targets. | `notebooks/Phase3_KPIs_Swetha.ipynb` |
| 4. Dashboard and report | Flat tables prepared for Power BI, a 5-page interactive dashboard with synced segment slicers, and a management report for the Chief Customer Officer. | `notebooks/Phase4_DataPrep_Swetha.ipynb`, `dashboard/`, `report/` |

### Dashboard pages

1. **Executive Overview:** churn, retention and revenue-at-risk cards, with monthly churn and revenue-lost trends.
2. **Customer and Segment Analysis:** churn by segment and tenure, plan-price distribution and a rule-based at-risk watch-list.
3. **Service and Support:** first contact resolution, resolution time, complaints by status and churn by unresolved complaints.
4. **Network and Regional:** churn by dropped-call level, top states by churned customers and by dropped-call rate, and customers by city tier.
5. **Campaigns and Revenue:** retention campaign outcomes, monthly recurring revenue and revenue lost to churn.

## Assumptions and limitations

- **Gross margin (40%) is an assumption.** It is not in the data. Customer lifetime value is shown for comparing segments, not as a forecast.
- **Associations, not causes.** For example, customers with more unresolved complaints churn more, but the analysis does not show that complaints cause churn.
- **Tenure** for churned customers stops at their exit date, so part of the "short tenure means high churn" pattern comes from how tenure is measured.
- **Network data** covers January to March 2026 only, while most churned customers left earlier, so network quality is shown as an association.
- **The retention campaign data has no comparison group** of customers who were not contacted, so the effect of the campaigns cannot be measured.
- **The "top at-risk customers" list is a simple rule** (Monthly plan, two or more unresolved complaints, worst-quarter dropped calls, Mass segment), not a prediction model.
- **Data questions for the business:** 251 customers marked Churned still hold an active subscription, 52 active subscriptions start after 31 March 2026, and 2,947 contracts are past their end date but still show Active or Pending.
- **Map visuals were disabled** on the machine used to build the dashboard, so a bar chart of dropped-call rate by state replaces the planned network map.

## Repository structure

```
nexatel-customer-churn-analytics/
├── README.md
├── notebooks/
│   ├── Phase1_DataCleaning_Swetha.ipynb
│   ├── Phase2_EDA_Swetha.ipynb
│   ├── Phase3_KPIs_Swetha.ipynb
│   └── Phase4_DataPrep_Swetha.ipynb
├── dashboard/
│   └── Phase4_Dashboard_Swetha.pbix
├── report/
│   └── Phase4_Report_Swetha.pdf
├── charts/            (PNG charts from Phase 2 and Phase 3)
└── screenshots/       (images of the 5 dashboard pages)
```

The raw and cleaned data files are not included in this repository.

## How to run it

1. Upload the project's data files to Google Drive in `MyDrive/NexaTel/data/`.
2. Open the notebooks in Google Colab and run them in order: Phase 1, Phase 2, Phase 3, then Phase 4 data prep. Each notebook reads the previous phase's cleaned files from Drive.
3. Open `dashboard/Phase4_Dashboard_Swetha.pbix` in Power BI Desktop (Windows). The data is saved inside the file.

## Tools

Python (pandas, matplotlib), Google Colab, Power BI Desktop (DAX measures, relationships, slicers), GitHub.

## Author

**Swetha**, Bengaluru, India
[LinkedIn](https://www.linkedin.com/in/swetharajv) | [GitHub](https://github.com/swetharajv)
