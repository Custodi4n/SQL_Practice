## Task 1

```sql
SELECT pizza_name, price, name, visit_date FROM menu, pizzeria, person_visits
WHERE person_id = '3' AND price BETWEEN 800 AND 1000
ORDER BY pizza_name, price DESC, name
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/08ade57e-c547-4fb9-87be-7f6b101943dc)

## Task 2

```sql
SELECT menu.id FROM menu
WHERE menu.id NOT IN (SELECT DISTINCT menu_id FROM person_order)
ORDER BY menu.id
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/a32c411c-4d5d-4920-9d7e-07c5699de39f)

## Task 3

```sql
SELECT menu.id, pizza_name, price, pizzeria.name AS pizzeria_name FROM menu, pizzeria
WHERE menu.id NOT IN (SELECT DISTINCT menu_id FROM person_order)
ORDER BY pizza_name, price
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/3d34e374-e8f2-4c1a-a917-c66fa4828423)

## Task 4

```sql
WITH female AS (
	SELECT pi.name FROM pizzeria pi
	JOIN person_visits pv ON pv.pizzeria_id = pi.id
	JOIN person p ON pv.person_id = p.id
	WHERE p.gender = 'female'
), male AS (
	SELECT pi.name FROM pizzeria pi
	JOIN person_visits pv ON pv.pizzeria_id = pi.id
	JOIN person p ON pv.person_id = p.id
	WHERE p.gender = 'male'
)


(
	SELECT * FROM female
	EXCEPT ALL
	SELECT * FROM male
)
UNION
(
	SELECT * FROM male
	EXCEPT ALL
	SELECT * FROM female
)
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/68375337-af8f-4482-ace2-3567d0682b84)

## To be continued ;)
