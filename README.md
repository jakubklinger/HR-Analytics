 <h1> 📊 HR Analytics Project </h1>

## 📌 Project Overview

This project demonstrates SQL-based HR analytics using a fictional employee dataset.
The goal is to evaluate salary distribution, hiring trends, department performance and retirement plan participation.
The analysis transforms raw HR data into insights supporting decisions in compensation strategy, workforce planning and benefits optimization.

## 🎯 Objectives

<ul>
<li>Analyze the salary across different departments</li>
<li>Identify hiring trends over time</li>
<li>Evaluate the participation in a retirement plan </li>
<li>Apply intermediate SQL techniques including:
    <li>Aggregations</li>
    <li>Multi-table JOINs</li>
    <li>Common Table Expressions (CTEs)</li>
    <li> CASE WHEN - defining the results based on the condition </li>
    <li>Window functions (ROW_NUMBER, ranking logic)</li>
</ul>

## 📋 Files
- department_new.sql
- employees_new.sql
- salary_new.sql
- queries.sql

## 🗄️ Tables
Table	Description
employees_new Stores employee details including name, department, and hire date
salary_new 	Contains wage, compensation rate, and retirement plan participation
department_new	Includes department IDs and department names

## 🛠️ Stack
<ul>
<li>PostgreSQL 18.3</li>
<li>pgAdmin 4</li>
<li>DBeaver 26.1.0</li>
<li>Microsoft Excel</li>
</ul>

## </> Example Queries

<h2>📊 Average Salary by Department</h2>

## 🎯 Business Question

What is the average salary in each department? This infomation can influence further wage strategies to ensure satisfaction of the employees while keeping the business costs in mind.

## 🔍 Approach

1. Join employee and salary data 
2. Calculate and round the average value of salary
3. Group results by department name 

## 💻 SQL Query
```sql
SELECT en."Department Name",
       ROUND(AVG(salary_new.Wage), 2) AS avg_wage
FROM employees_new en
JOIN salary_new sn
  ON sn."Employee ID" = en."Employee ID"
GROUP BY en."Department Name";
```
<img width="251" height="146" alt="image" src="https://github.com/user-attachments/assets/4e223b5c-a99c-4288-be77-a47e6f9a52c8" />

<h2> 📊Number of employees hired each year </h2>

## 🎯Business Question
How many employees were hired each year, and what does this reveal about workforce expansion or contraction? Answering that can influence company change their employment strategy.


## 🔍 Approach
The analysis was performed in two steps:
1. Use SUBSTR operator to extract the hire year
2. Count employees hired per year
3. Group results chronologically

## 💻 SQL Query
```sql
SELECT
    substr("Date hired", 1, 4) AS hire_year,
    COUNT(*) AS employees_hired
FROM employees_new
GROUP BY hire_year
ORDER BY hire_year;
```
<img width="239" height="195" alt="image" src="https://github.com/user-attachments/assets/301c2cb1-e9e5-4e2b-920f-e947cb12f8dc" />

<h2> 📊 Retirement plan participation </h2>

## 🎯Business Question
What is the level of participation to the retirement plan? This information can help in evaluating benefits strategy. 


## 🔍 Approach

1. Use CASE WHEN logic for summing the employees that participate in the retirement plan
2. CASE WHEN logic was reapplied to calculate how many employees aren't enrolled in the plan
3. Group results by department 

## 💻 SQL Query
```sql
SELECT
    en."Department Name",
    SUM(CASE WHEN sn."Retirement Plan Voluntary" = 'Yes' THEN 1 ELSE 0 END) AS enrolled_in_retirement_plan ,
    SUM(CASE WHEN sn."Retirement Plan Voluntary" = 'No'  THEN 1 ELSE 0 END) AS not_enrolled_in_retirement_plan
FROM employees_new en
JOIN salary_new sn ON en."Employee ID" = sn."Employee ID"
GROUP BY en."Department Name"
ORDER BY en."Department Name";
```
<img width="574" height="149" alt="image" src="https://github.com/user-attachments/assets/37a1a7b5-0d4f-41fd-9706-aa5db6a9158d" />

<h2> 📊 Average wage by hire year </h2>

## 🎯Business Question

How wages differ for employees hired each year? This information might help in determining if the salary adjustments are necessary.

## 🔍 Approach

The analysis was performed in three steps:
1. Used SUBSTR function to track the hire year
2. Rounded average of wages was calculated
3. Results were grouped by a hire year and shown in an ascending order (2015,2016,2017...)

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

<h2> 📊 Top earning employee in each department </h2>

## 🎯Business Question
Who is the highest-earning employee in each department? This calculation can help in evaluating the wages across all departments.

## 🔍 Approach

1. CTE was used to create temporary values for reference
2. Rank the employees within each department by their wages using the window function
3. Showing the highest record (rank num = 1) for each department (employee with the highest salary)

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
📈 Overview of Findings 

📌 Business Impact: 
💡 Key Insight

Evaluation of salaries across all departments is an important step in 

✉ ---Contact me--- For any questions, please contact me at jakub.klinger1996@gmail.com.
