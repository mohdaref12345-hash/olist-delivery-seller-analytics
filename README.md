# Delivery & Seller Performance Analytics (Olist) – Power BI

A four-page Power BI dashboard on the public **Olist Brazilian e-commerce** dataset. It measures how reliably **96,470 delivered orders** reached customers, where and why they were late, which sellers drive the problem, and what demand looks like.

**Author:** Mohammed Aref Sultan · [GitHub](https://github.com/mohdaref12345-hash)

## Links

| | |
|---|---|
| Portfolio page (all dashboards explained) | https://mohdaref12345-hash.github.io/olist-delivery-seller-analytics/ |
| Power BI report file | [`Olist_Delivery_Dashboard.pbix`](https://github.com/mohdaref12345-hash/olist-delivery-seller-analytics/blob/main/Olist_Delivery_Dashboard.pbix) (open in Power BI Desktop, data included) |
| PDF copy of the report | [`Olist_Dashboard.pdf`](Olist_Dashboard.pdf) |
| Repository | https://github.com/mohdaref12345-hash/olist-delivery-seller-analytics |

## Contents

[Links](#links) · [Headline finding](#headline-finding) · [Dashboards](#dashboards) · [Project scope](#project-scope) · [Data sources](#data-sources) · [Calculations used](#calculations-used) · [Tools and technologies](#tools-and-technologies) · [Project files](#project-files) · [Open the report](#open-the-report) · [Author](#author)

## Headline finding

Carrier transit, not seller handling, drives late orders: **25.2 days** in transit for late orders versus **7.4** for on-time ones. Late orders also score **2.57** in reviews versus **4.29**.

| KPI | Value |
|---|---|
| On-time delivery (OTD) | 91.9% (8.1% late) |
| Average delivery (purchase to door) | 12.1 days |
| Average delay on late orders | 8.9 days |
| Average review | 4.16 / 5 |
| Revenue | 13.2M |
| Freight as a share of revenue | 16.6% |

> The KPI is **OTD** (on-time delivery), not OTIF: the dataset has no in-full information.

## Dashboards

All four pages share the same left sidebar for navigation and three slicers (**Year, State, Category**) that filter every page. Click an image to open it full size.

### 1. Executive Overview

![Executive Overview](images/01_Executive_Overview.png)

**Purpose:** a one-page answer to "how are we doing, when did it go wrong, and at which stage is the delay?"

| Visual | What it shows |
|---|---|
| KPI cards | OTD 91.9% (8.1% late), average delivery 12.1 days, average delay 8.9 days on late orders, average review 4.16 / 5 (late 2.57 vs on-time 4.29), revenue 13.2M on 96,470 delivered orders |
| On-time delivery % by month | Monthly OTD from January 2017 to August 2018. The three lowest months are highlighted in orange |
| Late delivery % by customer state | Only states with 500+ delivered orders. The six worst are orange, the best three teal |
| Where the delay happens | Days per stage, seller handling vs carrier transit, split into late and on-time orders |
| Key findings | A text box written by a DAX measure, so it updates with the slicers |

**What it shows**
- Overall OTD is 91.9%, but monthly OTD dipped close to 80% in the weakest month.
- Maranhão has the highest late rate (19.7%), then Ceará (15.3%) and Bahia (14.0%). São Paulo is at 5.9%.
- The gap is in transit: **25.2 days** for late orders against **7.4** for on-time ones. Seller handling differs by only about three days (5.4 vs 2.5).

### 2. Delivery by Region

![Delivery by Region](images/02_Delivery_by_Region.png)

**Purpose:** find which states are slow or late, and where freight takes a large share of revenue.

| Visual | What it shows |
|---|---|
| KPI cards | Delivered orders, OTD, average delivery, revenue, freight as a share of revenue (16.6%) |
| Late delivery % by state | The 17 states with 500+ delivered orders, ranked |
| Average delivery days by state | Slowest states first |
| Bubble map | Late % by state, bubble size is the late rate (approximate state-capital coordinates) |
| Categories by freight % of revenue | Product categories ranked by freight cost relative to revenue |

**What it shows**
- The slowest deliveries are in the north: Roraima 29.0 days, Amapá 26.7, Amazonas 26.0. The south-east is far faster.
- Freight is 16.6% of revenue overall, but some categories are much heavier, such as christmas_supplies (36.5%) and signaling_and_security (30.4%).
- Late rate and delivery time do not rank the states identically, so both views are kept.

### 3. Seller & Carrier Performance

![Seller & Carrier](images/03_Seller_and_Carrier.png)

**Purpose:** see who hands orders to the carrier late, and whether the problem sits with sellers or with the carrier.

| Visual | What it shows |
|---|---|
| KPI cards | Delivered orders, late hand-off % (9.32%), average seller handling (2.7 days), average carrier transit (8.9 days), average review |
| Top 10 and Bottom 10 sellers | Ranked by on-time hand-off. Only sellers with 30+ orders are ranked, so small samples cannot top the table |
| Days per stage: seller vs carrier | Average handling and transit days, late vs on-time |
| Average review score by delivery status | Late 2.57 vs on-time 4.29 |

**What it shows**
- The ten best sellers all hand over on time (100%), including sellers with 150+ orders.
- The ten worst range from 17.6% to 52.2% on-time hand-off. One of them handles 246 orders at 49.7%, a high-volume problem worth acting on.
- Late orders score far lower in reviews, so lateness has a clear customer cost.

Sellers are shown by the first 8 characters of their ID (unique across all 3,095 sellers). Ranking ties are broken by order volume.

### 4. Demand & Forecast

![Demand & Forecast](images/04_Demand_and_Forecast.png)

**Purpose:** understand demand trends, which categories earn the revenue, and how much buffer variable delivery time requires.

| Visual | What it shows |
|---|---|
| Monthly delivered orders | Orders per month with a 3-month forecast and a 95% confidence band |
| Top 10 categories by revenue | Revenue by product category |
| Orders by weekday | Orders for each day of the week |
| Orders by month of year | Orders for each calendar month |
| Safety stock note | A DAX-written text based on the spread of delivery times |

**What it shows**
- Monthly orders grew steadily through 2017 and flattened in 2018. The forecast band is wide, so it is a rough guide only.
- health_beauty and watches_gifts lead revenue at about 1.2M each, followed by bed_bath_table and sports_leisure at about 1.0M.
- Mondays are the busiest day (15.7K orders) and Saturdays the quietest (10.6K).
- Delivery time averages 12.1 days with a standard deviation of 9.6. For a 95% service level, plan about **15.8 extra days** (1.65 × standard deviation).

Read the month-of-year chart with care: January to August include two years of orders, September to December only one, so the totals are not like-for-like.

## Project scope

**Business question:** where is delivery performance breaking down, and is the cause the seller or the carrier?

**In scope**
- Delivered orders only (status "delivered" with a customer delivery date): 96,470 orders.
- Four report pages with shared Year, State and Category slicers: Executive Overview, Delivery by Region, Seller & Carrier, Demand & Forecast.
- On-time delivery, delay by stage (seller handling vs carrier transit), regional and seller rankings, review impact, revenue and freight, demand trends and a 3-month forecast.
- Ranking rules to avoid small-sample noise: states, months and categories need **500+ delivered orders**; sellers need **30+ orders**.

**Out of scope / limitations**
- Static data: the report is built on Excel files and has no scheduled refresh.
- No OTIF, and no analysis of payments or geolocation (see data sources below).
- The map uses approximate state-capital coordinates, not state centroids. It is a scatter-plot bubble map because Power BI's built-in map visuals depend on Bing Maps, which is being retired.
- The forecast is Power BI's built-in line-chart forecast (3 months, 95% confidence band). It is a rough guide only.
- The month-of-year chart is not like-for-like: January to August cover two years, September to December only one.

## Data sources

Source: Olist Brazilian E-Commerce Public Dataset (Kaggle). The nine Excel files are in [`data/`](data/). The file names on GitHub are shortened; the Power BI project still points to the original names shown in the second column.

| File in `data/` | Original file name (used in the project) | What it contains | Used in the report |
|---|---|---|---|
| `olist_orders.xlsx` | `olist_orders_dataset.xlsx` | Order status and timestamps (purchase, carrier, delivery, estimate) | Yes: `orders` table (delivered only) |
| `olist_order_items.xlsx` | `olist_order_items_dataset.xlsx` | Items per order: seller, product, price, freight, shipping limit | Yes: `order_items` |
| `olist_customers.xlsx` | `olist_customers_dataset.xlsx` | Customer city and state | Yes: `customers` |
| `olist_sellers.xlsx` | `olist_sellers_dataset.xlsx` | Seller city and state | Yes: `sellers` |
| `olist_products.xlsx` | `olist_products_dataset.xlsx` | Product to category | Yes: `products` |
| `olist_categories.xlsx` | `product_category_name_translation.xlsx` | Category names in Portuguese and English | Yes: joined into `products` |
| `olist_reviews.xlsx` | `olist_order_reviews_dataset.xlsx` | Review score per order | Yes: `order_reviews` (average per order) |
| `olist_payments.xlsx` | `olist_order_payments_dataset.xlsx` | Payment type and value | No: defined as a query, not used by any visual |
| `olist_geolocation.xlsx` | `olist_geolocation_dataset - Copy - Copy.xlsx` | Zip-code coordinates | No: defined as a query, not used by any visual (map coordinates come from a small state table instead) |

## Calculations used

All logic is in Power Query, calculated columns and DAX measures. The raw tables are never edited. Full code: [`docs/measures.dax`](docs/measures.dax).

**Power Query (data preparation)**
- Keep only delivered orders with a customer delivery date, shared by the orders, items and reviews tables.
- Join product categories to their English names (fall back to the Portuguese name, then "Unknown").
- Average review score per order (551 repeat reviews are averaged): 99,224 raw rows become 95,824 clean rows.

**Calculated columns**

| Column | Logic |
|---|---|
| `Delivery Days` | delivered date − purchase date (whole days) |
| `Is Late` / `Delivery Status` | 1 / "Late" when delivered date is after the estimated date |
| `Delay Days` | days after the estimate, never below 0 |
| `Seller Handling Days` | carrier pick-up date − purchase date |
| `Carrier Transit Days` | customer delivery date − carrier pick-up date |
| `Seller Late Handoff Flag` | carrier pick-up after the seller's shipping limit date |
| `State Name` | state code to state name |
| `Seller Short` | first 8 characters of the seller ID (unique across all 3,095 sellers) |

**DAX measures (45), by group**
- **Delivery:** Delivered Orders, Late Delivery %, On-Time Delivery %, Avg Delivery Days, Avg Delay (Late Orders), Avg Seller Handling, Avg Carrier Transit.
- **Reviews:** Avg Review Score, Review Score (Late), Review Score (On-Time).
- **Revenue and freight:** Revenue, Revenue (M), Freight Cost, Freight % of Revenue.
- **Sellers:** Seller Orders, Late Handoff %, Seller On-Time Handoff %, Seller Rank Key, Seller Rank (Top / Bottom) with the 30-order rule.
- **500+ rules and rankings:** Late Rank (500+ States), Qualifying State Count, Show State (Top 6 + Bottom 3), Month In Window, Month OTD Rank (Lowest), Late % (States 500+), Late % (Highest 6 / Other States), OTD (Lowest 3 Months).
- **Map:** Map Lat, Map Lng (lookup in a small hidden table of 27 state coordinates).
- **Dynamic text and colours:** key-findings text, KPI sub-labels, chart titles, bar and marker colours, and a safety-stock note (1.65 × standard deviation of delivery days for a 95% service level).

**Model:** relationships from `orders` to `customers`, `order_items` to `orders`, `order_reviews` to `orders`, `order_items` to `sellers`, `order_items` to `products`, and `orders` to a calendar `Date` table (September 2016 to October 2018).

**Verification:** the headline numbers were checked three ways: the report model, independent DAX on the raw tables, and Python on the original CSV files. All match. See [`docs/reconciliation.csv`](docs/reconciliation.csv) and [`docs/verification_queries.dax`](docs/verification_queries.dax).

## Tools and technologies

- **Power BI Desktop**: report design, data model, PBIP project format (TMDL and PBIR text files)
- **Power Query (M)**: data preparation
- **DAX**: calculated columns and measures
- **Microsoft Excel files**: data sources
- **Python**: independent verification against the original CSV files
- **Git and GitHub**: version control, hosting
- **HTML and CSS with GitHub Pages**: portfolio page

## Project files

```
README.md
index.html                       portfolio page (also served by GitHub Pages)
Olist_Delivery_Dashboard.pbix    report file, data included
Olist_Dashboard.pdf              the report as a PDF
images/                          the four report pages in 4K
data/                            the nine Olist source Excel files
powerbi/                         Power BI project source (PBIP)
  Olist_Delivery_Dashboard.pbip
  Olist_Delivery_Dashboard.Report/          pages, visuals, theme
  Olist_Delivery_Dashboard.SemanticModel/   tables, relationships, measures (TMDL)
docs/
  measures.dax                   all 45 DAX measures
  verification_queries.dax       independent checks
  reconciliation.csv             A / B / C comparison results
  MODEL_NOTES.md                 model notes and known gaps
  Olist_Theme.json               report colour theme
```

## Open the report

**Quickest:** download `Olist_Delivery_Dashboard.pbix` and open it in Power BI Desktop. The data is already inside the file.

**Or open the project source:**
1. In Power BI Desktop, enable the **Power BI Project (.pbip)** preview feature.
2. Open `powerbi/Olist_Delivery_Dashboard.pbip`.
3. Point the data sources to your local copy of `data/` (Transform data, then Data source settings). The project's original paths are `C:\Users\isc\OneDrive\Attachments\`, with the original file names listed above.
4. Refresh.

## Author

**Mohammed Aref Sultan** – Power BI / data analytics. GitHub: [mohdaref12345-hash](https://github.com/mohdaref12345-hash)
