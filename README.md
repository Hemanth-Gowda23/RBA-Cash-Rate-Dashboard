# RBA Cash Rate Dashboard — Power BI

> Interactive Power BI dashboard analysing Australia's official cash rate trends from **1990 to present**, built using DAX time intelligence functions and financial KPIs sourced directly from the Reserve Bank of Australia.

---

## Overview

The Reserve Bank of Australia (RBA) adjusts the official cash rate to manage inflation and economic growth. This dashboard makes 35+ years of monetary policy decisions explorable and visual — turning raw RBA data into actionable financial insight.

**Key questions this dashboard answers:**
- How has Australia's cash rate changed since 1990?
- What were the biggest rate movements and when did they occur?
- How does the current rate cycle compare to historical periods (GFC 2008, COVID 2020, inflation surge 2022–23)?
- What is the year-on-year and period-on-period rate of change?

---

## Dashboard Features

| Feature | Detail |
|---|---|
| Time range | 1990 – Present (RBA f01hist dataset) |
| Interactivity | Year slicers, period filters, drill-through by RBA decision date |
| KPIs | Current rate, YoY change, all-time high/low, average by decade |
| Visuals | Line trend chart, rate change bar chart, KPI cards, period comparison |
| DAX | Time intelligence: YoY %, period-over-period change, running average |

---

## DAX Measures

```dax
-- Year-over-Year Rate Change
YoY Change % =
DIVIDE(
    [Current Cash Rate] - CALCULATE([Current Cash Rate], DATEADD('Date'[Date], -1, YEAR)),
    CALCULATE([Current Cash Rate], DATEADD('Date'[Date], -1, YEAR))
) * 100

-- Running Average Cash Rate
Running Avg Rate =
AVERAGEX(
    FILTER(ALL('RBA Data'), 'RBA Data'[Date] <= MAX('RBA Data'[Date])),
    'RBA Data'[Cash Rate]
)

-- Change from Previous Decision
Change from Previous =
[Current Cash Rate] - CALCULATE([Current Cash Rate], PREVIOUSMONTH('Date'[Date]))
```

---

## Key Insights from the Data

- Australia's cash rate peaked at **17.5% in January 1990** during the recession-inducing tightening cycle
- The rate hit a historic low of **0.1% in November 2020** during COVID-19 monetary stimulus
- The 2022–2023 hiking cycle was the fastest rate increase in 30 years — from 0.1% to 4.35% in 18 months

---

## Data Source

- **Source:** Reserve Bank of Australia — [Statistical Table F1](https://www.rba.gov.au/statistics/tables/)
- **File:** `f01hist.xlsx` (included in this repo)

---

## Tools Used

- Power BI Desktop
- DAX (time intelligence, calculated measures)
- Excel / Power Query (data cleaning)

---

## How to Open

1. Clone or download this repo
2. Open `RBA_Cash_Rate_Dashboard.pbix` in Power BI Desktop (free from Microsoft)
3. Data is embedded — no additional setup needed

---

## Author

**Hemanth R**
- LinkedIn: [linkedin.com/in/hemanth-gowda-78b972222](https://www.linkedin.com/in/hemanth-gowda-78b972222/)
- GitHub: [github.com/Hemanth-Gowda23](https://github.com/Hemanth-Gowda23)

Master of Data Science — RMIT University, Melbourne
Bachelor of Engineering (Information Science) — VTU, Bangalore

---

## License

CC0 1.0 — free to use, share, and adapt.
