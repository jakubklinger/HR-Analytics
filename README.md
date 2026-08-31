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
employees_new	Stores 
salary_new Contains 
department_new	Includes 

## 🛠️ Stack
<ul>
<li>PostgreSQL 18.3</li>
<li>pgAdmin 4</li>
<li>DBeaver 26.1.0</li>
<li>Microsoft Excel</li>
</ul>

## </> Example Queries

📊**Average Salary by Department**

## 🎯Business Question



## 🔍 Approach


## 💻 SQL Query
```sql
SELECT employees_new."Department Name",
       ROUND(AVG(salary_new.Wage), 2) AS avg_wage
FROM employees_new
JOIN salary_new
  ON salary_new."Employee ID" = employees_new."Employee ID"
GROUP BY employees_new."Department Name";
```
