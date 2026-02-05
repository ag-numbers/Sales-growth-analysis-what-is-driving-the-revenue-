# Sales growth analysis - what is driving the revenue
## Goal

Understand whether revenue is growing and what is driving that growth.
The goal of this analysis was to answer three core questions:
- Is revenue growing over time?
- Which categories and products contribute most to revenue and growth?
- Is revenue growth driven by higher sales volume or higher prices?

These questions guided both the data model and the dashboard structure.

## Data preparation and modeling

1) Loaded sales and product data into Power BI
2) Performed data profiling and cleaned the data in Power Query (data types, NULLs)
3) Created a Date table
4) Built a star schema to connect the tables
<img width="768" height="468" alt="Screenshot 2026-02-05 at 10 17 17" src="https://github.com/user-attachments/assets/1065e167-2e0e-422a-b65e-77aa31240bc2" />


## I created the following measures for complete analysis (DAX)

- Revenue = SUM(Sales[Revenue])
- Units = SUM(Sales[Units])
- Previous year measures
- Revenue PY = CALCULATE([Revenue], SAMEPERIODLASTYEAR(Date[Date]))
- Revenue Growth % = DIVIDE([Revenue] - [Revenue PY], [Revenue PY])
- Units PY = CALCULATE([Units], SAMEPERIODLASTYEAR(Date[Date]))
- Units Growth % = DIVIDE([Units] - [Units PY], [Units PY])
- Avg Price = DIVIDE([Revenue], [Units])
- Avg Price PY = DIVIDE([Revenue PY], [Units PY])

# Dashboard and insights
## Page 1 — Sales overview

Question: Is revenue growing?
Revenue shows consistent year-over-year growth
Category view highlights where most revenue comes from

### Insight:
Revenue is increasing steadily over time.
<img width="895" height="502" alt="Screenshot 2026-02-04 at 10 11 13" src="https://github.com/user-attachments/assets/c90ebd8c-aa2f-4863-8edc-5a5a7e5e5748" />



## Page 2 — Where is revenue coming from? (Categories and Products)

Question: Which categories and products drive revenue?
Revenue is concentrated in specific category and product combinations
A small number of segments contribute most to total revenue and growth

### Insight:
A few categories and products are the main revenue drivers.
<img width="1943" height="1101" alt="Screenshot 2026-02-04 at 10 20 24" src="https://github.com/user-attachments/assets/14fd6df9-2fb4-4dd2-b7eb-d88f55d2961d" />


## Page 3 — What’s driving revenue growth? (Units vs Price)
Question: Is growth driven by volume or price?
Unit sales are increasing
Average prices remain relatively stable

### Insight:
<img width="973" height="548" alt="Screenshot 2026-02-04 at 10 34 36" src="https://github.com/user-attachments/assets/85bb313e-c5ce-4d17-8029-b776301dae74" />


# Final conclusion
Revenue is growing consistently. Growth is concentrated in specific product categories and is driven mainly by increased unit sales rather than price increases.
