# Model notes (added after review)
- state_geo: hidden calculated table, 27 rows, approximate state-capital lat/lng, used only to place bubbles on page 2. No relationship; measures Map Lat / Map Lng look up by customers[customer_state]. Coordinates were typed from general knowledge, then checked against IBGE capital-seat coordinates (gist by kguidonimartins, sf data): all 27 within about 0.1 degree. Still capital cities, not state centroids.
- Map is a scatter ("bubble map") because Power BI's built-in map visuals depend on Bing Maps, which is being retired.
- sellers[Seller Short] = LEFT(seller_id, 8), unique across all 3,095 sellers; page 3 tables show it instead of the 32-char id. Seller Rank (Top/Bottom) rank over this column.
- 500+ orders threshold: 17 of 27 states, 20 of 23 months, 26 of 74 categories qualify.
- raw_order_reviews: no bad rows. 99,224 raw rows -> 95,824 clean = 2,849 orders not delivered + 551 repeat reviews averaged per order.
- Page 2: the Revenue-vs-freight column chart was replaced by the bubble map.
