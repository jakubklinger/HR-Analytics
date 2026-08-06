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
SELECT e.name,
       d.department name,
       s.wage
FROM employees e
JOIN department d
    ON e.Employee_ID = d.Employee_ID
JOIN salary s
    ON e.Employee_ID = s.Employee_ID
ON e.Employee_ID = s.Employee_ID
WHERE s.Wage > AVG(s.Wage) OVER (
    PARTITION BY d.Department_Name
)
ORDER BY d.Department_Name, s.Wage DESC;
```
