## Initial Queries
```sql
-- Check the raw data
SELECT *
FROM pizza_sales
LIMIT 10;

SELECT COUNT(pizza_id)
FROM pizza_sales;

-- Check data type of order_date column
SELECT order_date, pg_typeof(order_date) AS data_type
FROM pizza_sales;

-- Change data type of order_date from text to Date
ALTER TABLE pizza_sales
ADD COLUMN order_date_f DATE;

UPDATE pizza_sales
SET order_date_f = TO_DATE(order_date, 'DD-MM-YYYY');

SELECT order_date_f, pg_typeof(order_date_f) AS data_type
FROM pizza_sales;

ALTER TABLE pizza_sales
DROP COLUMN order_date;
```

## Total Revenue
```sql
SELECT ROUND(SUM(total_price), 2) AS Total_Revenue 
FROM pizza_sales;
```
picture

## Average order Values
```sql
SELECT ROUND(SUM(total_price) / COUNT(DISTINCT order_id), 2) AS Avg_Order_Value 
FROM pizza_sales;
```
picture

## Total Pizza Sold
```sql
SELECT SUM(quantity) AS pizza_sold
FROM pizza_sales;
```
picture

## Total Orders
```sql
SELECT COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales;
```
picture

## Average Pizzas Per Order
```sql
SELECT ROUND(CAST(SUM(quantity) AS DECIMAL) / COUNT(DISTINCT order_id) , 2) AS Avg_Pizza_Per_Order
FROM pizza_sales;
```
picture
