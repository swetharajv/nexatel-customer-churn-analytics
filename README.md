# NexaTel Customer Churn Analytics

This is my project for the Internmo Data Analyst internship program. I worked with a telecom customer dataset (24 tables) to find out why customers leave NexaTel, and what the company could do about it. It covers data cleaning, exploratory analysis, 10 KPIs, a 5-page Power BI dashboard and a short management report.

## What I found

- Monthly churn averages 0.65%, which is inside the 2.1% target. But it has been rising, from 0.44% in April 2025 to 1.25% in March 2026.
- Customers who left in the last 12 months were paying about Rs.7.7 lakh a month, roughly Rs.93 lakh a year. The monthly amount lost grew from Rs.31,972 to Rs.122,854 between April 2025 and March 2026.
- Customers with no unresolved complaint churn at 15.1%. With three or more unresolved complaints it is 48.3%.
- Support is the weak spot. Only 40.4% of tickets are solved on the first contact (target 78%), and 44.3% of complaints are unresolved.
- Mass-segment customers churn at 26.7% against 11.9% for Enterprise. Monthly-plan customers churn at 22.5% against 7.2% for Annual plans.

These are patterns in the data. They show which groups leave more, not why they leave.

## The 10 KPIs

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

## What is in this repository

All the files are in the main folder.

| File | What it is |
|---|---|
| `Phase1_DataCleaning_Swetha.ipynb` | Phase 1: loading, profiling and cleaning all 24 tables, with my data quality report |
| `Phase2_EDA_Swetha.ipynb` | Phase 2: 10 charts, each with my observation |
| `Phase3_KPIs_Swetha.ipynb` | Phase 3: the 10 KPIs and a summary table |
| `Phase4_DataPrep_Swetha.ipynb` | Phase 4: builds the small tables the dashboard uses |
| `Phase4_Dashboard_Swetha.pbix` | Phase 4: the 5-page Power BI dashboard (open it in Power BI Desktop) |
| `Phase4_Report_Swetha.pdf` | Phase 4: the management report |
| `README.md` | This file |

I have not included the data files.

## How I went about it

**Phase 1, cleaning.** I loaded and checked all 24 tables, then worked through the 20 data quality issues listed in the project's issue log. 18 of them matched the log exactly. The other two I could not reproduce: I found 744 missing emails where the log says 760, and 560 capitalisation errors where it says 570. I have reported those as they are. I also wrote 11 checks that read the saved clean files and confirm the fixes are really there.

**Phase 2, exploring the data.** I made 10 charts looking at churn by segment, billing cycle, tenure, complaints, state, data usage, plan price, network quality and retention campaigns.

**Phase 3, KPIs.** I calculated the 10 KPIs month by month from April 2025 to March 2026.

**Phase 4, dashboard and report.** I prepared flat tables for Power BI, built a 5-page dashboard (Executive Overview, Customer and Segment, Service and Support, Network and Regional, Campaigns and Revenue) with segment slicers that work across all pages, and wrote the management report.

## What was tricky

- My first check for impossible ages (anything outside 0 to 120) found 23 of the 38 in the issue log. I found the other 15, adults recorded as age 0 or 1, by comparing each age with the date of birth.
- The overall churn figure (18.5%) cannot be compared with a monthly target, so I worked out churn month by month from the churn dates.
- The data has no gross margin, so for customer lifetime value I assumed 40% and said so everywhere I use it.
- In Power BI I had to connect the tables properly and sync the slicers. Map visuals were switched off on my laptop, so I used a bar chart of dropped-call rate by state instead of a map.

## Things to keep in mind

- The 40% gross margin is my assumption. I use lifetime value to compare segments, not as a forecast.
- For customers who left, tenure stops on the day they left. Part of the pattern "short tenure, high churn" comes from that.
- The network data only covers January to March 2026, and most customers who left did so earlier. So I can say dropped calls and churn go together, not that poor network came first.
- The retention campaign data has no group of similar customers who were not contacted, so I cannot say whether the campaigns worked.
- The "top at-risk customers" list is a simple rule I made (Monthly plan, two or more unresolved complaints, worst-quarter dropped calls, Mass segment). It is not a prediction model.
- A few things in the data need checking with the business: 251 customers marked as churned still have an active subscription, 52 active subscriptions start after 31 March 2026, and 2,947 contracts are past their end date but still show as Active or Pending.

## Running it yourself

1. Put the project's data files in Google Drive, in `MyDrive/NexaTel/data/`.
2. Open the notebooks in Google Colab and run them in order: Phase 1, Phase 2, Phase 3, then Phase 4 data prep.
3. Open the `.pbix` file in Power BI Desktop (Windows). The data is saved inside it.

Tools I used: Python (pandas, matplotlib), Google Colab, Power BI Desktop and GitHub.

## About me

Swetha, Bengaluru.
[LinkedIn](https://www.linkedin.com/in/swetharajv) | [GitHub](https://github.com/swetharajv)
