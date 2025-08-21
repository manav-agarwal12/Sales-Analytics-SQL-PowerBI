# Sales-Analytics-SQL-PowerBI

# 📊 E-Commerce Sales Analytics (SQL + Power BI)

## 🔹 Project Overview
Built an **end-to-end data analytics project** analyzing e-commerce sales using **SQL for data modeling** and **Power BI for visualization**.  
The project delivers **20+ KPIs** on revenue, profit margins, customer behavior, and product performance, enabling data-driven decision-making.

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
