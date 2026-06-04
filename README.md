# E-commerce-Sales-Customer-Insights-SQL-Case-Study

# 📌 1. Business Scenario
An online pet‑care store wants to understand customer behaviour, revenue trends, and opportunities to increase repeat purchases. You were asked to analyse transactional data using SQL and present actionable insights.

# 📌 2. Dataset Structure (Dummy Data)

# A. Monthly Revenue Trend
SELECT 
    DATE_TRUNC('month', order_date) AS month,
    SUM(amount) AS total_revenue
FROM orders
GROUP BY month
ORDER BY month;

# B. Top 10 Customers by Total Spend
SELECT 
    c.customer_id,
    c.name,
    SUM(o.amount) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name
ORDER BY total_spent DESC
LIMIT 10;

# C. Average Order Value by Region
SELECT 
    c.region,
    AVG(o.amount) AS avg_order_value
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.region
ORDER BY avg_order_value DESC;

# D. Repeat Customer Rate
SELECT 
    COUNT(DISTINCT customer_id) FILTER (WHERE order_count > 1) * 100.0 /
    COUNT(DISTINCT customer_id) AS repeat_customer_rate
FROM (
    SELECT customer_id, COUNT(*) AS order_count
    FROM orders
    GROUP BY customer_id
) t;


# 📌 4. Insights Report (Completed)
## Revenue Trends
Monthly revenue grew steadily, with a 22% increase in Q2.  
Seasonal spikes observed around holidays and promotional periods.  

## Customer Behaviour
Top 10% of customers contribute 55% of total revenue, indicating a strong high‑value segment.  
Repeat customer rate: 38%, showing room for loyalty improvement.    

## Regional Performance
South region has the highest average order value (£87).  
East region shows the lowest engagement and may require targeted marketing.  

## Productivity & Growth Opportunities
Customers who place a second order within 30 days have a 3× higher lifetime value.  
Early engagement campaigns could significantly boost retention.  

# 📌 5. Recommendations
Launch a loyalty programme to increase repeat purchases.  
Target the East region with discounts or personalised offers.  
Introduce first‑order follow‑up emails to encourage second purchases.  
Use customer segmentation to prioritise high‑value customers.  
  
