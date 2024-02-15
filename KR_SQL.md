## Task 1

```sql
SELECT last_name, first_name, COUNT(orders.customer_id) AS quantity
FROM orders
JOIN customers ON orders.customer_id = customers.customer_id
WHERE order_date >= '2024.02.01'
GROUP BY orders.customer_id, customers.last_name, customers.first_name
ORDER BY quantity DESC
LIMIT 1
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/2537a45d-bbe7-42bf-bdea-1db054f6a0ab)

## Task 3

```sql
UPDATE products
SET price = price - (price * 0.125)
WHERE category = 'Clothing';

UPDATE products
SET price = price - (price * 0.5)
WHERE category != 'Clothing'
```

## Task 4
С самой низкой средной ценой
```sql
SELECT category, AVG(price)
FROM products
GROUP BY category
ORDER BY avg
LIMIT 1
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/0e2e8294-59ec-49ed-898d-53c4d76c9c82)

С самой высокой средней ценой
```sql
SELECT category, AVG(price)
FROM products
GROUP BY category
ORDER BY avg DESC
LIMIT 1
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/a0170c5d-4ee3-493c-9e31-d1e92167f551)

## Task 5

```sql
DELETE 
FROM orders 
WHERE quantity < (SELECT AVG(quantity) FROM orders)
```
