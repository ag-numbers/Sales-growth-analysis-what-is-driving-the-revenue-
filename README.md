# Sales growth analysis - what is driving the revenue
## Business context

The company sells products across multiple categories and segments. Management wants to understand what is driving revenue growth in order to prioritize product strategy and marketing investments.

Key business questions:
- Is the growth coming from more units sold or higher prices?
- Which product categories and segments contribute the most to revenue?
- Which products are driving the largest share of growth?
  
Understand whether revenue is growing and what is driving that growth.

## Business recommendations

Based on the analysis:

• Focus on the Urban category which contributes the largest share of revenue.
• Expand products similar to Maximus UC-76, which shows the strongest growth contribution.
• Since growth is primarily driven by unit sales rather than price increases, marketing and distribution strategies should prioritize volume expansion.
• Monitor price stability to ensure margins remain sustainable while volume grows.

## Data preparation

1) Loaded sales and product data into Power BI
2) Performed data profiling and cleaned the data in Power Query (data types, NULLs)
3) Created a Date table

## Data model

The dataset was structured using a snowflake schema.
Fact table:
- Sales (Revenue, Units)
Dimension tables:
- Date
- Product
- Manufacturer
- Geography

The model allows flexible analysis across time, product categories, segments and regions.
<img width="768" height="468" alt="Screenshot 2026-02-05 at 10 17 17" src="https://github.com/user-attachments/assets/1065e167-2e0e-422a-b65e-77aa31240bc2" />

## I created the following measures for complete analysis (DAX)

- Revenue = SUM(Sales[Revenue])
- Units = SUM(Sales[Units])
- Revenue PY = PY Revenue = CALCULATE (SUM (Sales[Revenue]), SAMEPERIODLASTYEAR ( 'Date'[Date]))
- Revenue Growth % = DIVIDE([Revenue] - [Revenue PY], [Revenue PY])
- Units PY = CALCULATE(sum(Sales[Units]), SAMEPERIODLASTYEAR('Date'[Date]))
- Units Growth % = DIVIDE(sum(Sales[Units]) - [Units PY], [Units PY])
- Avg Price = DIVIDE(SUM([Revenue]), sum(Sales[Units]))
- Avg Price PY = CALCULATE([Avg Price], SAMEPERIODLASTYEAR('Date'[Date]))

# Dashboard and insights
## Page 1 — Sales overview

Question: Is revenue growing?

### Insight:
Yes, revenue is increasing steadily over time.
<img width="895" height="502" alt="Screenshot 2026-02-04 at 10 11 13" src="https://github.com/user-attachments/assets/c90ebd8c-aa2f-4863-8edc-5a5a7e5e5748" />

## Page 2 — Where is revenue coming from? (Categories and Products)

Question: Which categories and products drive revenue?

### Insight:
Urban category in convenience segment is the main revenue driver. Maximus UC-76 product drives the most growth.
<img width="1943" height="1101" alt="Screenshot 2026-02-04 at 10 20 24" src="https://github.com/user-attachments/assets/14fd6df9-2fb4-4dd2-b7eb-d88f55d2961d" />


## Page 3 — What’s driving revenue growth? (Units vs Price)
Question: Is growth driven by volume or price?

### Insight: Unit sales are increasing & average prices remain relatively stable
<img width="973" height="548" alt="Screenshot 2026-02-04 at 10 34 36" src="https://github.com/user-attachments/assets/85bb313e-c5ce-4d17-8029-b776301dae74" />


# Final conclusion
Revenue is growing consistently. Growth is in urban product category and is driven mainly by increased unit sales rather than price increases.

