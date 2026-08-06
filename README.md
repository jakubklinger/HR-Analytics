HR Company report.

📌 Project Overview



🎯 Objectives


Apply intermediate SQL techniques including:
Aggregations
Multi-table JOINs
Common Table Expressions (CTEs)
Window functions (ROW_NUMBER, ranking logic)

📋 Files
database.sql
queries.sql

🗄️ Tables
Table	Description
shop_customers	Stores 
shop_orders	Contains 
shop_items	Includes 

🛠️ Stack
PostgreSQL 18.3
pgAdmin 4
DBeaver 26.1.0
Microsoft Excel

</> Example Queries
📊 Employees salary compared to the departments avergae

🎯Business Question



🔍 Approach


💻 SQL Query
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
