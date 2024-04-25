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
SELECT s.user_id, ROUND(COUNT(action) FILTER(WHERE action = 'confirmed')::numeric / COUNT(s.user_id), 2) AS confirmation_rate 
FROM signups s
LEFT JOIN confirmations c ON s.user_id = c.user_id
GROUP BY s.user_id
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/637678f2-75ef-44ca-985a-ec39bb01c88b)


## 1193. Monthly Transactions I

```sql
SELECT 
    TO_CHAR(trans_date, 'YYYY-MM') AS month, 
    country, 
    COUNT(TO_CHAR(trans_date, 'YYYY-MM')) AS trans_count, 
    COUNT(state) FILTER(WHERE state = 'approved') AS approved_count, 
    SUM(amount) AS trans_total_amount, 
    SUM(CASE WHEN state = 'approved' THEN amount else 0 end) AS approved_total_amount
FROM transactions
GROUP BY TO_CHAR(trans_date, 'YYYY-MM'), country
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/cf2bb20d-18c4-4e1f-b87a-4d9d56dd6479)


## 1174. Immediate Food Delivery II

```sql
SELECT ROUND((SUM(CASE WHEN order_date = customer_pref_delivery_date THEN 1.0 ELSE 0.0 END)::NUMERIC / COUNT(customer_id)) * 100, 2) AS immediate_percentage
FROM delivery
WHERE (customer_id, order_date) IN (
        SELECT customer_id, min(order_date)
        FROM delivery
        GROUP BY customer_id
    )
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/5c7214df-e54b-4ad5-bef0-f1362acd67b7)


## 
