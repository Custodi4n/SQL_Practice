## 570. Managers with at Least 5 Direct Reports

```sql
SELECT name FROM (
    SELECT e2.id, e2.name, COUNT(e2.id) AS pod FROM employee e1
    JOIN employee e2 ON e1.managerId = e2.id
    GROUP BY e2.id, e2.name
)
WHERE pod >= 5
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/f433fe5e-6561-447e-b753-df50a044b879)


## 1934. Confirmation Rate

```sql
SELECT s.user_id, ROUND(COUNT(action = "confirmed"), 2) AS confirmation_rate FROM signups s
LEFT JOIN confirmations c ON s.user_id = c.user_id
GROUP BY s.user_id
