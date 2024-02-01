## Task 1

```sql
SELECT pizza_name, id FROM menu
UNION ALL
SELECT name, id FROM person
ORDER BY ID
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/76f94a4e-42d9-4706-9154-649372b5c00c)

## Task 2

```sql
SELECT DISTINCT person.name, menu.pizza_name
FROM person
JOIN menu ON person.id = menu.pizzeria_id
ORDER BY person.name, menu.pizza_name;
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/604f8c9b-f5d8-4d45-947c-1fb3ab9bacdb)

## Task 3

```sql
SELECT order_date AS action_date, person_id FROM person_order
UNION ALL
SELECT visit_date AS action_date, person_id FROM person_visits
ORDER BY action_date ASC, person_id DESC
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/814f85b9-72d3-4e1a-acbe-26a63470fa0f)

## Task 4

```sql
SELECT person_id
FROM person_order
WHERE order_date = '2022-01-07'
EXCEPT
SELECT person_id
FROM person_visits
WHERE visit_date = '2022-01-07';
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/89452439-1a53-4879-919e-2cdaf326e266)
