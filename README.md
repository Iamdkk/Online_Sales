# Sales Trend Analysis Using Aggregations

This project performs a **sales trend analysis** on the **online_sales** dataset to track **monthly revenue** and **order volume**. The analysis aggregates the data based on the **order_date**, calculating the following metrics:

- **Monthly Revenue**: Total sales amount for each month.
- **Order Volume**: Number of distinct orders per month.

## SQL Script

The SQL script includes the following:

- Extraction of the month and year from the **order_date** column.
- Aggregation using **SUM()** for revenue and **COUNT(DISTINCT order_id)** for order volume.
- Results are grouped by year/month and sorted in descending order by month.
- The output is filtered for a specific time period.

```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM 
    orders
GROUP BY 
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY 
    year DESC, month DESC;
