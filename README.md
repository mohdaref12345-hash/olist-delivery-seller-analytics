# Delivery & Seller Performance Analytics (Olist) – Power BI

A four-page Power BI dashboard on the public **Olist Brazilian e-commerce** dataset. It measures how reliably **96,470 delivered orders** reached customers, where and why they were late, which sellers drive the problem, and what demand looks like.

**Headline finding:** carrier transit, not seller handling, drives late orders – 25.2 days in transit for late orders versus 7.4 for on-time ones. Late orders also score 2.57 in reviews versus 4.29.

| KPI | Value |
|---|---|
| On-time delivery (OTD) | 91.9% (8.1% late) |
| Average delivery (purchase to door) | 12.1 days |
| Average delay on late orders | 8.9 days |
| Average review | 4.16 / 5 |
| Revenue | 13.2M |

> KPI is **OTD** (on-time delivery), not OTIF: the dataset has no in-full information.

## Dashboards

### 1. Executive Overview
![Executive Overview](images/01_Executive_Overview.png)

### 2. Delivery by Region
![Delivery by Region](images/02_Delivery_by_Region.png)

### 3. Seller & Carrier Performance
![Seller & Carrier](images/03_Seller_and_Carrier.png)

### 4. Demand & Forecast
![Demand & Forecast](images/04_Demand_and_Forecast.png)

A full walkthrough with explanations is in [`index.html`](index.html) (open it locally, or via GitHub Pages if enabled). A PDF copy is in [`Olist_Dashboard.pdf`](Olist_Dashboard.pdf), and the ready-to-open report is [`Olist_Delivery_Dashboard.pbix`](Olist_Delivery_Dashboard.pbix) (52 MB, data included).

## What's inside

```
README.md
index.html              portfolio page with all four dashboards explained
Olist_Dashboard.pdf     the report as a PDF
Olist_Delivery_Dashboard.pbix   the report file, data included (open in Power BI Desktop)
images/                 the four pages in 4K
data/                   the nine Olist source Excel files
powerbi/                Power BI project (PBIP, readable text files)
docs/
  measures.dax          all 45 DAX measures
  verification_queries.dax, reconciliation.csv
  MODEL_NOTES.md, Olist_Theme.json
```

## Method

- Nine Olist tables are loaded as raw tables and never edited; all logic is in DAX measures and calculated columns.
- Only delivered orders are analysed. A state, month or category needs 500+ orders to be ranked; sellers need 30+ orders.
- Headline numbers were verified three ways (report model, independent DAX on the raw tables, Python on the original CSVs). All match – see [`docs/reconciliation.csv`](docs/reconciliation.csv).
- The map is a scatter-plot bubble map using approximate state-capital coordinates, because the built-in map visuals depend on Bing Maps, which is being retired.

## Open the report

**Quickest:** download `Olist_Delivery_Dashboard.pbix` and open it in Power BI Desktop. The data is already inside the file.

**Or open the project source:**

1. In Power BI Desktop, enable the **Power BI Project (.pbip)** preview feature.
2. Open `powerbi/Olist_Delivery_Dashboard.pbip`.
3. Point the data sources to your local copy of `data/` (Transform data → Data source settings; the project's original paths are `C:\Users\isc\OneDrive\Attachments\`).
4. Refresh.

## Data

Olist Brazilian E-Commerce Public Dataset (Kaggle). Excel copies of the nine tables are in `data/`.
