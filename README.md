# Sales growth analysis - what is driving the revenue
Goal

Understand whether revenue is growing and what is driving that growth.
The goal of this analysis was to answer three core questions:
- Is revenue growing over time?
- Which categories and products contribute most to revenue and growth?
- Is revenue growth driven by higher sales volume or higher prices?

These questions guided both the data model and the dashboard structure.

## Data preparation and modeling ##

1) Loaded sales and product data into Power BI
2) Performed data profiling and cleaned the data in Power Query (data types, NULLs)
3) Created a Date table
4) Built a star schema to connect the tables
<img width="512" height="217" alt="model star schema" src="https://github.com/user-attachments/assets/a5ee5fa3-7e11-46af-8df7-1bd5d29896c8" />

## Then I created the following measures (DAX)##

- Revenue = SUM(Sales[Revenue])
- Units = SUM(Sales[Units])
- Previous year measures
- Revenue PY = CALCULATE([Revenue], SAMEPERIODLASTYEAR(Date[Date]))
- Revenue Growth % = DIVIDE([Revenue] - [Revenue PY], [Revenue PY])
- Units PY = CALCULATE([Units], SAMEPERIODLASTYEAR(Date[Date]))
- Units Growth % = DIVIDE([Units] - [Units PY], [Units PY])
- Avg Price = DIVIDE([Revenue], [Units])
- Avg Price PY = DIVIDE([Revenue PY], [Units PY])

## Dashboard and insights ##
# Page 1 — Sales overview

Question: Is revenue growing?
Revenue shows consistent year-over-year growth
Category view highlights where most revenue comes from

# Insight:
Revenue is increasing steadily over time.
<img width="512" height="286" alt="sales overview p1" src="https://github.com/user-attachments/assets/e20dbacc-a31f-40e7-971a-1f24c1474965" />


# Page 2 — Where is revenue coming from? (Categories and Products)

Question: Which categories and products drive revenue?
Revenue is concentrated in specific category and product combinations
A small number of segments contribute most to total revenue and growth

# Insight:
A few categories and products are the main revenue drivers.
<img width="512" height="289" alt="p2" src="https://github.com/user-attachments/assets/8ad30cb2-98e3-4304-aedb-66114ec85765" />

# Page 3 — What’s driving revenue growth? (Units vs Price)
Question: Is growth driven by volume or price?
Unit sales are increasing
Average prices remain relatively stable

# Insight:
Revenue growth is demand-driven, not price-driven.
<img width="512" height="282" alt="p3" src="https://github.com/user-attachments/assets/e088e7ec-f042-4062-a92d-093c14666145" />

# Final conclusion
Revenue is growing consistently. Growth is concentrated in specific product categories and is driven mainly by increased unit sales rather than price increases.
