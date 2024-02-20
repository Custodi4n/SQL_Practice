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

## Task 5

```sql
SELECT DISTINCT
	pizzeria.name
FROM
	pizzeria
JOIN 
	person_visits ON pizzeria.id = person_visits.pizzeria_id
JOIN 
	person_order ON person_visits.person_id = person_order.person_id
JOIN 
	person ON person_visits.person_id = person.id
WHERE 
	person.name = 'Andrey' AND visit_date != order_date
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/569f0206-6a8a-4aaf-9282-82ec576e9754)

## Task 6

```sql
WITH pizza_s AS (
 SELECT m1.pizza_name, m1.pizzeria_id as pi_1, m2.pizzeria_id as pi_2, m1.price
 FROM menu m1
 JOIN menu m2 ON m1.pizza_name = m2.pizza_name AND m1.price = m2.price AND m1.pizzeria_id > m2.pizzeria_id
)

SELECT pizza_name, pi1.name, pi2.name, price
FROM pizza_s
JOIN pizzeria pi1 ON pi_1 = pi1.id
JOIN pizzeria pi2 ON pi_2 = pi2.id
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/ffa40e8c-d6b7-41ec-949f-e9eca637b91f)

## Task 7

```sql
INSERT INTO menu
VALUES (19, 2, 'Greek Pizza', 800);
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/7cd89b3f-008b-42ef-b2e2-eea76e117a54)

## Task 8

```sql
INSERT INTO menu 
VALUES(
	(SELECT MAX(id) 
 	 FROM menu) +1, 
	(SELECT id 
	 FROM pizzeria
	WHERE name = 'Dominos'), 'Sicilian Pizza', 900
)
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/a85af64b-ce32-4fe2-b979-8bac0524fdeb)

## Task 9

```sql
INSERT INTO person_visits VALUES(
 (SELECT MAX(id) FROM person_visits) +1,
 (SELECT id FROM person
 WHERE name = 'Denis'),
 (SELECT id FROM pizzeria
 WHERE name = 'Dominos'), 
 '2022-02-24'),
 ((SELECT MAX(id) FROM person_visits) +2, 
 (SELECT id FROM person
 WHERE name = 'Irina'),
 (SELECT id FROM pizzeria
 WHERE name = 'Dominos'), 
 '2022-02-24')
```

![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/a43b8e42-7652-4bdd-a293-511ee2a3c36e)

## Task 10
