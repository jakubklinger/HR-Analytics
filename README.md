📊 **Computer Shop SQL Sales Analysis**

## 📌 Project Overview

This project demonstrates SQL-based HR analytics using a fictional employee dataset.
The goal is to evaluate salary distribution, hiring trends, department performance and retirement plan participation.
The analysis transforms raw HR data into insights supporting decisions in compensation strategy, workforce planning and benefits optimization.

## 🎯 Objectives


<li>Analyze the salary across different departmenys</li>
<li>Evaluate the particaption in a retirement plan </li>
<li>Apply intermediate SQL techniques including:
    <li>Aggregations</li>
    <li>Multi-table JOINs</li>
    <li>Common Table Expressions (CTEs)</li>
    <li> CASE WHEN - to define the results based on the condition </li>
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

What is the average salary in each department? This infomation can influence further wage strategies to ensure satisfaction of the employees while keeping the business costs in mind.

## 🔍 Approach

The analysis was performed in two steps:
1. Round the average value of salary
2. Group the results by the department name 

## 💻 SQL Query
```sql
SELECT en."Department Name",
       ROUND(AVG(salary_new.Wage), 2) AS avg_wage
FROM employees_new en
JOIN salary_new sn
  ON sn."Employee ID" = en."Employee ID"
GROUP BY en."Department Name";
```

📊**Number of employees hired each year**

## 🎯Business Question
What is the hiring trend in recent years? Answering that can influence company change their employment strategy.


## 🔍 Approach
The analysis was performed in two steps:
1. Use SUBSTR function to track the hire year
2. Group the results by the department name

## 💻 SQL Query
```sql
SELECT
    substr("Date hired", 1, 4) AS hire_year,
    COUNT(*) AS employees_hired
FROM employees_new
GROUP BY hire_year
ORDER BY hire_year;
```

📊**Retirement plan participation**

## 🎯Business Question



## 🔍 Approach


## 💻 SQL Query
```sql
SELECT
    en."Department Name",
    SUM(CASE WHEN sn."Retirement Plan Voluntary" = 'Yes' THEN 1 ELSE 0 END) AS enroled_in_retirement_plan ,
    SUM(CASE WHEN sn."Retirement Plan Voluntary" = 'No'  THEN 1 ELSE 0 END) AS not_enroled_in_retirement_plan
FROM employees_new en
JOIN salary_new sn ON en."Employee ID" = sn."Employee ID"
GROUP BY en."Department Name"
ORDER BY en."Department Name";
```

📊**Average wage by hire year**

## 🎯Business Question

How the wages are shapping for the employees hired each year? This infomation might help in determining if the wages of long time employees should be raised.


## 🔍 Approach


## 💻 SQL Query
```sql
SELECT
    substr(en."Date hired", 1, 4) AS hire_year,
    ROUND(AVG(sn.Wage), 2) AS avg_salary
FROM employees_new en
JOIN salary_new sn
    ON sn."Employee ID" = en."Employee ID"
GROUP BY hire_year
ORDER BY hire_year ASC;
```

📊**Top earning employee in each department**

## 🎯Business Question



## 🔍 Approach


## 💻 SQL Query
```sql
WITH employee_wages AS (
    SELECT
en.Name, 
en."Employee ID", 
en."Department Name", 
sn.Wage

    FROM employees_new en
    JOIN salary_new sn
        ON en."Employee ID" = sn."Employee ID"
  
),
ranked_employees AS (
    SELECT
        Name,
        "Department Name",
Wage,
        ROW_NUMBER() OVER (
            PARTITION BY "Department Name"
            ORDER BY Wage DESC
        ) AS rank_num
    FROM employee_wages
)SELECT
Name,
"Department Name",
Wage
   FROM ranked_employees
WHERE rank_num = 1;
```
