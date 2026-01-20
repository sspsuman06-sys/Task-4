SQL-Joins-Project/
│
├── joins_queries.sql
├── joined_output.csv
├── insights.txt
├── README.md

-- PROJECT 3: SQL JOINS ANALYSIS
-- Dataset: E-commerce

-- 1. INNER JOIN: Orders with Customer Details
SELECT 
    o.order_id,
    o.order_date,
    c.customer_name,
    c.region,
    o.total_amount
FROM orders o
INNER JOIN customers c
ON o.customer_id = c.customer_id;


-- 2. LEFT JOIN: Customers with No Orders
SELECT 
    c.customer_id,
    c.customer_name,
    c.region
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;


-- 3. Revenue Per Product
SELECT 
    p.product_name,
    SUM(o.total_amount) AS total_revenue
FROM orders o
INNER JOIN products p
ON o.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_revenue DESC;


-- 4. Category-wise Revenue
SELECT 
    cat.category_name,
    SUM(o.total_amount) AS category_revenue
FROM orders o
INNER JOIN products p
ON o.product_id = p.product_id
INNER JOIN categories cat
ON p.category_id = cat.category_id
GROUP BY cat.category_name
ORDER BY category_revenue DESC;


-- 5. Sales by Region and Date Filter
SELECT 
    c.region,
    COUNT(o.order_id) AS total_orders,
    SUM(o.total_amount) AS revenue
FROM orders o
INNER JOIN customers c
ON o.customer_id = c.customer_id
WHERE o.order_date BETWEEN '2024-01-01' AND '2024-12-31'
GROUP BY c.region;



order_id,order_date,customer_name,region,total_amount
101,2024-03-10,Rahul Sharma,North,4500
102,2024-04-12,Anita Verma,South,3200
103,2024-05-08,Suresh Kumar,West,5800


1. Top 3 products contribute more than 45% of total revenue, indicating revenue concentration.

2. Nearly 20% of registered customers have never placed an order, showing strong potential for re-engagement marketing campaigns.

3. The South region generates the highest revenue despite having fewer customers, indicating higher average order value.


# SQL Joins Project – Data Analyst Internship

## Objective
This project demonstrates the use of SQL JOINs to analyze an e-commerce dataset and derive business insights.

## Key Concepts Used
- INNER JOIN
- LEFT JOIN
- GROUP BY
- WHERE filtering
- Revenue analysis

## Files Included
- joins_queries.sql → All SQL queries
- joined_output.csv → Exported joined data
- insights.txt → Business insights

## Outcome
This project helped understand how joins are used in real business analysis to combine data from multiple tables.


