HR Company report.

## 📌 Project Overview



## 🎯 Objectives


Apply intermediate SQL techniques including:
Aggregations
Multi-table JOINs
Common Table Expressions (CTEs)
Window functions (ROW_NUMBER, ranking logic)

## 📋 Files
database.sql
queries.sql

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
WHERE salary.Wage > (
    SELECT AVG(Wage)
    FROM employees e2
    WHERE e1.department_id = e2.department_id
);
```
