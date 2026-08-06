HR Company report.

## 📌 Project Overview



## 🎯 Objectives


<li>Analyze </li>
<li>Identify </li>
<li>Evaluate </li>
<li>Apply intermediate SQL techniques including:
    <li>Aggregations</li>
    <li>Multi-table JOINs</li>
    <li>Common Table Expressions (CTEs)</li>
    <li>Window functions (ROW_NUMBER, ranking logic)</li>
</ul>

## 📋 Files
- database.sql
- queries.sql

## 🗄️ Tables
Table	Description
shop_customers	Stores 
shop_orders	Contains 
shop_items	Includes 

## 🛠️ Stack
<ul>
<li>PostgreSQL 18.3</li>
<li>pgAdmin 4</li>
<li>DBeaver 26.1.0</li>
<li>Microsoft Excel</li>
</ul>

## </> Example Queries

📊**Employees salary compared to the department's average**

## 🎯Business Question



## 🔍 Approach


## 💻 SQL Query
```sql
SELECT *
FROM (
    SELECT
        e."Name",
        d."Department Name",
        s.wage,
         ROUND(AVG(s.wage) OVER (PARTITION BY d."Department Name"), 2) AS avg_wage
    FROM employees e
    JOIN department d ON e."Employee ID" = d."Employee ID"
    JOIN salary s ON e."Employee ID" = s."Employee ID"
) q
WHERE q.wage > q.avg_wage
ORDER BY q."Department Name", q.wage DESC;

;
```
