# Delivery & Seller Performance Analytics (Olist)

A Power BI dashboard that analyses delivery performance for an online marketplace.

## About the project

This project uses the public **Olist Brazilian e-commerce** dataset. It looks at **96,470 delivered orders** and answers three questions:

- How often are orders delivered on time, and where and when do delays happen?
- Is the delay caused by the **seller** (slow hand-over) or by the **carrier** (slow transit)?
- Which states, sellers and product categories need attention?

**Main result:** the carrier is the main cause of late orders. Late orders spend **25.2 days** in transit versus **7.4** for on-time ones, and they get a much lower review score (**2.57** versus **4.29**).

The main KPI is **OTD** (on-time delivery): an order is late when it arrives after the estimated delivery date.

Author: **Mohammed Aref Sultan** ([GitHub](https://github.com/mohdaref12345-hash))

## Links

| What | Link |
|---|---|
| Portfolio page (dashboards explained) | https://mohdaref12345-hash.github.io/olist-delivery-seller-analytics/ |
| Power BI report file | [Olist_Delivery_Dashboard.pbix](Olist_Delivery_Dashboard.pbix) |
| Report as PDF | [Olist_Dashboard.pdf](Olist_Dashboard.pdf) |
| Source data (9 Excel files) | [data/](data/) |
| Power BI project source | [powerbi/](powerbi/) |
| All 45 DAX measures | [docs/measures.dax](docs/measures.dax) |
| Verification results | [docs/reconciliation.csv](docs/reconciliation.csv) |

## Dashboards

The report has four pages. All of them share the same three filters (Year, State, Category).

### 1. Executive Overview

<a href="images/01_Executive_Overview.png"><img src="images/01_Executive_Overview.png" alt="Executive Overview" width="100%"></a>

The big picture: how reliable delivery is and where the delay comes from.

- **On-time delivery: 91.9%** (8.1% late)
- **Average delivery: 12.1 days** from purchase to door
- **Average delay: 8.9 days** on late orders
- **Average review: 4.16 / 5** (late orders 2.57, on-time orders 4.29)
- **Revenue: 13.2M** from 96,470 delivered orders
- Late orders spend **25.2 days** with the carrier versus 7.4 for on-time ones. Seller handling is 5.4 versus 2.5 days.
- Highest late rate by state: Maranhão 19.7%, Ceará 15.3%, Bahia 14.0%. São Paulo is 5.9%.

### 2. Delivery by Region

<a href="images/02_Delivery_by_Region.png"><img src="images/02_Delivery_by_Region.png" alt="Delivery by Region" width="100%"></a>

Which states are late or slow, and where freight costs a lot.

- **Delivered orders: 96,470** and **freight is 16.6% of revenue**
- Slowest average delivery: Roraima 29.0 days, Amapá 26.7 days, Amazonas 26.0 days
- A bubble map shows the late rate by state
- Highest freight share by category: christmas_supplies 36.5%, signaling_and_security 30.4%

### 3. Seller & Carrier Performance

<a href="images/03_Seller_and_Carrier.png"><img src="images/03_Seller_and_Carrier.png" alt="Seller and Carrier" width="100%"></a>

Who hands orders over late, and whether the problem is the seller or the carrier.

- **Late hand-off: 9.32%**, seller handling **2.7 days**, carrier transit **8.9 days**
- The 10 best sellers (30+ orders) hand over on time **100%** of the time
- The 10 worst sellers range from **17.6% to 52.2%**. One seller has 246 orders at 49.7%.
- Review score: **2.57** for late orders versus **4.29** for on-time orders

### 4. Demand & Forecast

<a href="images/04_Demand_and_Forecast.png"><img src="images/04_Demand_and_Forecast.png" alt="Demand and Forecast" width="100%"></a>

How demand moves, which categories earn the most, and how much buffer stock is needed.

- Monthly orders with a **3-month forecast** (95% confidence band)
- Top categories by revenue: health_beauty and watches_gifts about **1.2M** each
- Busiest day: Monday (**15.7K** orders). Quietest: Saturday (**10.6K**).
- Delivery time averages **12.1 days** and varies by **9.6 days**, so plan about **15.8 extra days** of safety stock for a 95% service level

## Tools

- **Power BI Desktop**: report design and data model
- **Power Query**: data preparation
- **DAX**: 45 measures and calculated columns
- **Excel**: data source files
- **Python**: independent check of the numbers
- **Git and GitHub**: version control and hosting

## Repository

```
README.md
index.html                       portfolio page
Olist_Delivery_Dashboard.pbix    Power BI report (data included)
Olist_Dashboard.pdf              report as PDF
images/                          the four dashboard pages (4K)
data/                            the nine source Excel files
powerbi/                         Power BI project source (.pbip)
docs/
  measures.dax                   all DAX measures
  verification_queries.dax       queries used to check the numbers
  reconciliation.csv             verification results
  MODEL_NOTES.md                 model notes
  Olist_Theme.json               colour theme
```

## How to open the report in Power BI (from GitHub)

You need **Power BI Desktop** (free, Windows).

1. Open [`Olist_Delivery_Dashboard.pbix`](Olist_Delivery_Dashboard.pbix) on GitHub.
2. Click the **download** icon (Download raw file) at the top right of the file view. The file is about 52 MB.
3. Double-click the downloaded file, or open Power BI Desktop and choose **File, then Open report**.

The data is stored inside the `.pbix`, so the report opens and works right away. You do not need the Excel files to view it.

**To refresh the data or edit the queries**, download the repository (**Code, then Download ZIP**) and point Power BI to your copy of the data:

1. In Power BI Desktop choose **Transform data, then Data source settings**.
2. Change each file path to the matching file in the `data/` folder. The file names in `data/` are shorter than the ones the report was built with (for example `olist_orders.xlsx` is `olist_orders_dataset.xlsx` in the report).
3. Click **Refresh**.

To open the project source instead, enable the **Power BI Project (.pbip)** preview feature in Power BI Desktop, then open `powerbi/Olist_Delivery_Dashboard.pbip`.
