## 175. Combine Two Tables

```sql
SELECT firstName, lastName, city, state FROM Person
LEFT JOIN Address ON Person.personID = Address.personID
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/bb8b69ba-76e2-4d03-834f-3eff6bdd9098)


## 176. Second Highest Salary

```sql
SELECT MAX(salary) as "SecondHighestSalary" FROM Employee
WHERE salary < (SELECT MAX(salary) FROM Employee)
LIMIT 1
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/792b350e-1650-4937-addd-81d468da669a)


## 177. Nth Highest Salary

```sql
CREATE OR REPLACE FUNCTION NthHighestSalary(N INT) RETURNS TABLE (Salary INT) AS $$
BEGIN
  RETURN QUERY (
    -- Write your PostgreSQL query statement below.
    SELECT  DISTINCT tab.salary FROM (
    SELECT Employee.salary, DENSE_RANK() OVER(ORDER BY Employee.salary DESC) AS rank FROM Employee
    ) AS tab
    WHERE rank = N
  );
END;
$$ LANGUAGE plpgsql;
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/58218627-b8ee-4310-be76-621b57c5aa8d)


## 178. Rank Scores

```sql
SELECT score, DENSE_RANK() OVER(ORDER BY score DESC) as rank FROM Scores
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/6da5ed7a-d972-4edd-b38a-fbae5c402c24)


## 181. Employees Earning More Than Their Managers

```sql
SELECT e1.name AS "Employee" FROM employee e1 
JOIN employee e2 ON e1.managerid = e2.id
WHERE e1.managerid = e2.id AND e1.salary > e2.salary
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/4c29a73b-5d52-4ace-9943-adef5bd6adae)


## 182. Duplicate Emails

```sql
SELECT tab.email FROM (
SELECT email AS "Email", COUNT(*) AS n FROM person
GROUP BY email
HAVING COUNT(*) > 1
) AS tab
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/f89537d9-3230-4e51-92c2-62c10bd454b0)


## 183. Customers Who Never Order

```sql
SELECT cust.name AS "Customers" FROM Customers cust
LEFT JOIN Orders ord ON cust.id = ord.customerId
WHERE NOT ord.customerId <=> cust.id
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/30af6b7c-7ee7-4ee5-9a34-ef0abe2d11d5)


## 511. Game Play Analysis I

```sql
SELECT player_id, MIN(event_date) AS first_login FROM Activity
GROUP BY player_id
ORDER BY player_id
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/fca118da-90ec-4b0d-bb74-a2e673eada7b)


## 184. Department Highest Salary

```sql
SELECT department.name AS "Department", employee.name AS "Employee", employee.salary AS "Salary" 
FROM department, employee
WHERE employee.departmentId = department.id AND (employee.departmentId, salary) IN
(SELECT departmentId, MAX(salary) FROM Employee
GROUP BY departmentId)
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/806079ba-16c2-429e-a220-96bc7c0713f9)


## 196. Delete Duplicate Emails

```sql
DELETE FROM Person
WHERE id NOT IN (SELECT MIN(id)
FROM Person
GROUP BY email)
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/3e1e96d5-dc66-4855-b6b5-556767d1367a)


## 197. Rising Temperature

```sql
SELECT w1.id
FROM weather w1
CROSS JOIN weather w2
WHERE w1.recordDate - w2.recordDate = 1 AND w1.temperature - w2.temperature > 0
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/be312231-765c-4d42-935b-993eef074852)
