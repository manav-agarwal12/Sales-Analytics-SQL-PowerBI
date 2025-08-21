📊 Sales & Profitability KPIs

## Total Revenue & Profit :

```sql
SELECT SUM(Sales) AS TotalRevenue,
```

SUM(Profit) AS TotalProfit

FROM SalesData.csv;

## Profit Margin % :

```sql
SELECT (SUM(Profit) * 100.0 / SUM(Sales)) AS ProfitMarginPercent FROM SalesData.csv;
```

## Profit Per Growth:

```sql
SELECT SUM(Profit) * 1.0 / COUNT(DISTINCT Order_ID) AS ProfitPerOrder FROM [SalesData.csv];
```

## Revenue per Region :

```sql
SELECT Region, SUM(Sales) AS Revenue FROM SalesData GROUP BY Region;
```

## Revenue per Segment :

```sql
SELECT Segment, SUM(Sales) AS Revenue FROM SalesData GROUP BY Segment;
```

## Sales per Order :

```sql
SELECT SUM(Sales) * 1.0 / COUNT(DISTINCT Order_ID) AS SalesPerOrder FROM SalesData;
```

👥 Customer Metrics

## Average Order Value (AOV) :

```sql
SELECT SUM(Sales) * 1.0 / COUNT(DISTINCT Order_ID) AS AvgOrderValue FROM [SalesData.csv];
```

## Repeat Purchase Rate :

```sql
SELECT * FROM SalesData
```

```sql
WITH CustomerOrders AS (SELECT Customer_ID, COUNT(DISTINCT Order_ID) AS OrderCount
```

FROM SalesData

GROUP BY Customer_ID)

```sql
SELECT COUNT(CASE WHEN OrderCount > 1 THEN 1 END) * 100.0 / COUNT(*) AS RepeatPurchaseRate
```

FROM CustomerOrders

## Customer Retention Rate (YoY) :

```sql
WITH CustomersByYear AS (
```

```sql
SELECT DISTINCT Customer_ID, YEAR(Order_Date) AS OrderYear
```

FROM SalesData

)

```sql
SELECT cy1.OrderYear,
```

COUNT(DISTINCT cy1.Customer_ID) AS CustomersThisYear,

COUNT(DISTINCT cy2.Customer_ID) AS CustomersLastYear,

(COUNT(DISTINCT cy1.Customer_ID) * 100.0 / NULLIF(COUNT(DISTINCT cy2.Customer_ID), 0)) AS RetentionRate

FROM CustomersByYear cy1

LEFT JOIN CustomersByYear cy2 ON cy1.Customer_ID = cy2.Customer_ID

AND cy1.OrderYear = cy2.OrderYear + 1

GROUP BY cy1.OrderYear;

## CLV(Customer Lifetime Value) Estimate :

```sql
WITH CustomerStats AS (
```

```sql
SELECT Customer_ID,
```

COUNT(DISTINCT Order_ID) AS Orders,

SUM(Sales) AS Revenue,

SUM(Profit) AS Profit

FROM SalesData GROUP BY Customer_ID

)

```sql
SELECT AVG(Revenue / Orders) AS AvgOrderValue,
```

AVG(Orders) AS AvgOrders,

AVG(Profit * 1.0 / Revenue) AS AvgMargin,

(AVG(Revenue / Orders) * AVG(Orders) * AVG(Profit * 1.0 / Revenue)) AS CLV_Estimate

FROM CustomerStats;

📦 Product & Category Metrics

## Top 10 Products by Sales :

```sql
SELECT TOP 10 Product_Name, SUM(Sales) AS TotalSales
```

FROM SalesData GROUP BY Product_Name ORDER BY TotalSales DESC;

## Most Profitable Sub-Categories :

```sql
SELECT Sub_Category, SUM(Profit) AS TotalProfit
```

FROM SalesData GROUP BY Sub_Category ORDER BY TotalProfit DESC;

🚚 Order & Shipping

## Avg Delivery Days :

```sql
SELECT AVG(DATEDIFF(DAY, Order_Date, Ship_Date)) AS AvgDeliveryDays FROM SalesData;
```

## Basket Size (Avg Quantity per Order) :

```sql
SELECT SUM(Quantity) * 1.0 / COUNT(DISTINCT OrderID) AS AvgBasketSize FROM SalesData;
```

💰 Financial / Marketing

## Net Revenue per Customer :

```sql
SELECT Customer_ID, SUM(Sales) AS TotalRevenue
```

FROM SalesData GROUP BY Customer_ID;

## Discount Impact on Profit :

```sql
SELECT CASE WHEN Discount = 0 THEN 'No Discount' ELSE 'Discount Applied' END AS DiscountFlag,
```

SUM(Sales) AS Revenue,

SUM(Profit) AS Profit,

(SUM(Profit) * 100.0 / SUM(Sales)) AS ProfitMargin

FROM SalesData

GROUP BY CASE WHEN Discount = 0 THEN 'No Discount' ELSE 'Discount Applied' END;

“Built an end-to-end SQL Server project analyzing e-commerce sales with 20+ KPIs, including Revenue, Profit Margin, AOV, CLV, CAC, Conversion Rate, Repeat Purchase Rate, Sales Growth, Customer Retention/Churn, Basket Size, and Discount Impact. Designed complex queries, views, and stored procedures to deliver insights into customer profitability, product performance, and regional sales trends, supporting data-driven decision-making.”