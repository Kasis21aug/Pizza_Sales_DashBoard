# Pizza Sales Analytics – Power BI Project

This repository contains an end‑to‑end analytics project that transforms raw point‑of‑sale data into interactive Power BI dashboards for tracking KPIs, understanding demand patterns, and identifying best/worst‑selling pizzas across categories and sizes.

### Key Deliverables
- KPI tiles for Total Revenue, Average Order Value, Total Pizzas Sold, Total Orders, and Average Pizzas per Order.
- Trend visuals for daily and monthly order volumes to surface seasonality and weekday effects.
- Composition charts showing percentage of sales by pizza category and by pizza size.
- Category funnel for total pizzas sold by category to compare performance at a glance.
- Best/Worst Seller report pages with Top 5 and Bottom 5 by Revenue, Quantity, and Total Orders, with callouts summarizing insights.

## Dataset

Fields used in the model:
- Pizza_id  
- order_id  
- pizza_name_id  
- Quantity  
- order_date  
- order_time  
- unit_price  
- total_price  
- Pizza_size  
- pizza_category  
- pizza_ingredients  
- pizza_name.[2]

Assumptions:
- order_date is in a Gregorian calendar year and combines with order_time for temporal analysis.  
- total_price equals Quantity × unit_price at the line level; if missing, it is recomputed during ETL.  
- pizza_name_id is a stable key mapping to pizza_name and attributes like category and size.[2]

## Business Questions

As outlined in the problem statements, the analysis focuses on:
- KPIs required for executive monitoring: Total Revenue, Average Order Value, Total Pizzas Sold, Total Orders, and Average Pizzas per Order.
- Trends to detect peaks and seasonality: daily trend for total orders and monthly trend for total orders.
- Mix analysis: percentage of sales by pizza category and by pizza size.
- Category performance: total pizzas sold by category (funnel).
- Product performance: Top 5 and Bottom 5 by Revenue, Quantity, and Total Orders.

## KPIs and Definitions

- Total Revenue: Sum of total_price across all order lines.
- Average Order Value (AOV): Total Revenue ÷ Total Orders.
- Total Pizzas Sold: Sum of Quantity across all order lines.
- Total Orders: Count of distinct order_id.
- Average Pizzas per Order: Total Pizzas Sold ÷ Total Orders.

## Dashboards

1) Home
- KPI tiles for overall performance.  
- Daily bar chart for total orders by weekday.  
- Monthly line chart for total orders by month.  
- Donut charts for percentage of sales by category and by size.  
- Category funnel showing total pizzas sold by category.

2) Best/Worst Seller
- Top 5 by Revenue, Quantity, Total Orders.  
- Bottom 5 by Revenue, Quantity, Total Orders.  
- Insight cards summarizing which pizzas contribute most/least by each metric.

## Insights Highlighted in the Report

- Peak demand occurs on weekends, especially Friday/Saturday evenings, informing staffing and inventory planning.
- July and January show the highest order volumes, indicating seasonal spikes for promotions and procurement.
- Classic category contributes the maximum share of sales and total orders, making it the anchor of the menu mix.
- Large size pizzas contribute the maximum sales share, suggesting upsell strategies around large-size bundles.
- Example winners and laggards are showcased in the Best/Worst page to guide menu optimization and marketing focus.

## Data Model and Transformations

Power Query steps (representative):
- Data type enforcement for dates, times, numeric fields.  
- Derive Year, Month, MonthName, Weekday, and Hour from order_date/order_time.  
- Recompute total_price as Quantity × unit_price if null, and validate nonnegative amounts.  
- Create dimension tables for Date, Pizza (from pizza_name_id), Category, and Size as needed.

## Use Cases

- Staffing and shift planning for peak weekend/evening demand.  
- Promotion timing around July and January spikes.  
- Menu engineering to emphasize Classic category and Large sizes.  
- Inventory forecasting by tracking top movers and pruning underperformers.[4][1]

