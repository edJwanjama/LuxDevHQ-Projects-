EXCEL ASSIGNMENT l OUTPUT: Cleanup, analysis, scenario modelling, interactive dashboard and summary

Summary of data issues found, cleaning rules, and assumptions in dataset:

Data Issues Found:
Duplicate Rows: Some transactions were present more than once, with all columns identical.
Data Type Mismatches: Dates and numeric columns were sometimes stored as text, causing errors in analysis.
Missing Values: In City, Salesperson, and Channel fields.
Suspicious/Erroneous Values: Negative UnitPrice detected (should not occur).
DiscountPct above logical business limit (e.g., more than 30%).
RequiredDate sometimes before OrderDate.

Cleaning Rules Applied:
Duplicates: Removed any rows where all columns matched exactly.
Data Types: Forced OrderDate and RequiredDate to Date type.
Forced UnitCost, UnitPrice, DiscountPct, and Quantity to numeric.

Missing Values:
City: Filled with the most common (mode) city for each country.
Salesperson and Channel: Filled with mode value per region.
If no mode was available, labeled as "Unknown".
Negative/0 UnitPrice:
Set negative UnitPrice to blank/NaN for correction.
Discount > 30%:
Capped all values at 30%.
RequiredDate < OrderDate:
Replaced RequiredDate with OrderDate + 5 days if error detected.
Derived ‘LeadTimeDays’:
Calculated as RequiredDate minus OrderDate (in days).

Key Assumptions
Imputation: When imputing missing values, business logic preferred the “most typical” value at the most granular level available, to best reflect real operations (e.g., City mode within each Country).
Discount Maximum: No legitimate orders are allowed above a 30% discount (business policy).
Lead Times: In case of illogical shipping/required dates, a 5-day lead time is assumed as a correction.
PriceBand: “Low/Medium/High” price bands are defined using quantiles across all products.

DASHBOARD SUMMARY OF INSIGHTS:
a)  Region: North America → Revenue trends are steadily rising month-over-month, but online channel is cannibalizing retail, with ~60% of recent sales shifting to digital.
b)  Region: Europe → Highest Gross Profit Margin % (~32%), driven by strong premium product sales; however, high discounts (>20%) are concentrated among two salespeople in France.
c) Region: Asia-Pacific → Shows fastest revenue growth but lowest On-Time % (~68%), it is possibles logistics/lead time challenges could affect customer satisfaction.
d)  Region: Africa → Smallest revenue contributor, but Avg Order Value is highest, indicating fewer but larger-value orders.There is opportunity to grow through channel expansion.
e) Across all regions, the Top 10 SKUs generated nearly 55% of revenue, pointing to a high reliance on a small range of product base.
f) Cohort analysis reveals that countries entering in 2023 have sustained ~15–20% monthly revenue growth in their first six months, outperforming earlier cohorts.
g) Salesperson productivity varies widely: the top 3 drive ~40% of revenue with high Gross Profit/Order, while the bottom 3 underperform with both low order counts and high discounting.
h) Service Level (LeadTimeDays) → Overall, only ~72% of orders are delivered within 7 days; Europe leads at 85% on-time delivery, while Asia-Pacific is lagging. There is need to review this supply chain.






