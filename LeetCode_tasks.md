## 175. Combine Two Tables

```sql
SELECT firstName, lastName, city, state FROM Person
LEFT JOIN Address ON Person.personID = Address.personID
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/21ec2e44-2c48-415d-9bc2-ff2b278a7c39)
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/bb8b69ba-76e2-4d03-834f-3eff6bdd9098)


## 176. Second Highest Salary

```sql
SELECT MAX(salary) as "SecondHighestSalary" FROM Employee
WHERE salary < (SELECT MAX(salary) FROM Employee)
LIMIT 1
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/ed62cd09-c747-4d59-97ab-1a77d2229b85)
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/876ffe09-44ed-48bb-b8b0-a5fc2112b330)
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
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/07a4356c-e564-4880-8116-dee54056e1ef)
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/2b65012a-2d5a-4e14-8b0c-9f3faac641a4)
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/58218627-b8ee-4310-be76-621b57c5aa8d)


## 178. Rank Scores

```sql
SELECT score, DENSE_RANK() OVER(ORDER BY score DESC) as rank FROM Scores
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/53f8de5f-a94a-4392-8e21-df58f274b48b)
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/6da5ed7a-d972-4edd-b38a-fbae5c402c24)
