# Sales growth analysis - what is driving the revenue
## Business context

The company sells products across multiple categories and segments. Management wants to understand what is driving revenue growth in order to prioritize product strategy and marketing investments.

1) What is driving revenue growth: higher sales volume or price increases?
2) Which categories and segments contribute the most to total revenue and growth?
3) Which products have the strongest impact on revenue performance?

## Key insights: 
1. Revenue grew 10.4% year-over-year. Growth was supported by both higher sales volume (+4.47%) and a moderate increase in average price (+5.69%), showing that demand and pricing both contributed to the increase.
2. The Urban category generates about 77% of total revenue, making it the main source of business performance with the potential dependancy risk. Other categories contribute much less, indicating strong reliance on one segment.
3. Key influencer analysis shows that several products from the Maximus product line are associated with higher revenue levels, suggesting that this type of product plays an important role in overall performance.

## Business recommendations

Based on the analysis:

1. Since the Urban segment generates the majority of revenue, prioritize product development, marketing, and distribution in this category.
2. Increase inventory and marketing activity before peak demand periods in Q2–Q3 to maximize sales.
3. Promote high-performing products: Products from the Maximus line are strongly associated with higher revenue and should be prioritized in promotions and sales strategies.
4. Revenue is concentrated in a few countries; exploring underperforming markets could unlock additional growth opportunities.

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
- PY Revenue = CALCULATE (SUM (Sales[Revenue]), SAMEPERIODLASTYEAR ( 'Date'[Date]))
- Revenue Growth % = DIVIDE([Revenue] - [PY Revenue], [PY Revenue])
- Units PY = CALCULATE(sum(Sales[Units]), SAMEPERIODLASTYEAR('Date'[Date]))
- Units Growth % = DIVIDE(sum(Sales[Units]) - [Units PY], [Units PY])
- Avg Price = DIVIDE(SUM([Revenue]), sum(Sales[Units]))
- Avg Price PY = CALCULATE([Avg Price], SAMEPERIODLASTYEAR('Date'[Date]))
- Avg Price Growth % = DIVIDE([Avg Price] - [Avg Price PY],[Avg Price PY])

# Dashboard
## Page 1 — Revenue trend - What's the general trend?
<img width="951" height="531" alt="trend final" src="https://github.com/user-attachments/assets/2ad31f08-2c58-4452-a777-acb2c5163cfd" />

## Page 2 — Revenue drivers - What’s driving revenue growth? (Units vs Price))
<img width="950" height="534" alt="drivers final " src="https://github.com/user-attachments/assets/4bf9db12-0e9b-4d38-b3e0-6f8f810ab21c" />


## Page 3 — Product drivers - Which product/segment drives revenue growth?
<img width="950" height="532" alt="growth final" src="https://github.com/user-attachments/assets/11b2db44-eafc-4bb9-85ac-0b569d87aacb" />

