# 📊 E-Commerce Sales Analytics (SQL + Power BI)

## 🔹 Project Overview
Built an **end-to-end data analytics project** analyzing e-commerce sales using **SQL for data modeling** and **Power BI for visualization**.  
The project delivers **20+ KPIs** on revenue, profit margins, customer behavior, and product performance, enabling data-driven decision-making.

---
## 📌 Project Story 

Problem :

The business lacked clear visibility into sales performance, customer retention, and profitability drivers across regions, products, and customer segments.
Decision-makers relied on raw spreadsheets without consolidated insights.

Action:

-Cleaned and modeled a dataset of ~10,000+ e-commerce transactions using SQL Server.

-Designed 20+ advanced SQL queries to calculate KPIs, including:

-Revenue & Profit Margin %

-Average Order Value (AOV) & Customer Lifetime Value (CLV)

-Repeat Purchase Rate & Customer Retention Rate (YoY)

-Top Products by Sales & Most Profitable Sub-Categories

-Discount Impact on Profit & Net Revenue per Customer

-Developed an interactive Power BI dashboard with filters, drill-downs, and KPI visuals across customers, regions, and products.

Result :

-Delivered a single source of truth dashboard with 95%+ accuracy.

-Identified that 10 products contributed ~40% of sales.

-Highlighted that discounted orders reduced profit margin by ~12%, guiding promotional strategy.

-Found that the South region delivered 15% higher profit margins compared to others.

-Improved visibility into customer repeat purchases (30% retention), supporting strategic growth decisions.

💡 Business Impact

This project demonstrates how analytics can:

 -Identify profitable customers and products

 -Optimize marketing ROI by analyzing discount impacts

 -Highlight regional trends for better sales strategy

 -Guide management in customer retention planning

---

## 🛠️ Tools & Technologies
- **SQL (MS SQL Server)** → Data cleaning, KPI calculations, advanced queries  
- **Power BI** → Dashboard development & interactive reporting  
- **Excel/CSV** → Input dataset

---

## 📈 Key KPIs & Metrics
- **Revenue & Profitability:** Total Revenue, Profit Margin %, Sales per Order  
- **Customer Insights:** Average Order Value (AOV), Repeat Purchase Rate, Retention Rate, Customer Lifetime Value (CLV)  
- **Product & Category Metrics:** Top 10 Products by Sales, Most Profitable Sub-Categories  
- **Operational Metrics:** Avg Delivery Days, Basket Size (Avg Quantity per Order)  
- **Financial/Marketing:** Discount Impact on Profit, Net Revenue per Customer  

---

## 🗄️ SQL Queries
Some example queries used in the project:

```sql
-- Total Revenue & Profit
SELECT SUM(Sales) AS TotalRevenue,
       SUM(Profit) AS TotalProfit
FROM SalesData;

-- Profit Margin %
SELECT (SUM(Profit) * 100.0 / SUM(Sales)) AS ProfitMarginPercent
FROM SalesData;


