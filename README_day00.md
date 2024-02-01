## Task 2

```sql
SELECT (name,age)
FROM person WHERE address = 'Tomsk';
```
![image](https://github.com/Custodi4n/SQL_Practice/assets/113520737/8ef66c09-5869-4af1-8ffa-046aecd15596)

## Task 3

```sql
SELECT name, age, gender
FROM person WHERE gender= 'female' AND address= 'Kazan'
ORDER BY name DESC
```
![Task3](https://github.com/Custodi4n/SQL_Practice/assets/113520737/df52b3c1-fab5-42ba-bfb7-28461794cd60)

## Task 4

```sql
SELECT name,rating FROM pizzeria
WHERE rating BETWEEN 3.5 AND 5
ORDER BY rating DESC
```

![Task4](https://github.com/Custodi4n/SQL_Practice/assets/113520737/182e04b9-6311-4b32-93a0-56a6253dc632)

## Task 5

```sql
SELECT DISTINCT person_id FROM person_visits
WHERE person_visits.visit_date BETWEEN '2022-01-01' AND '2022-01-04'
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/095e626b-6b55-40a1-a9f8-97115bfd7de0)

## Task 6

```sql
SELECT name FROM person
WHERE id IN(SELECT person_id FROM person_order 
		   WHERE menu_id= 7)
```

![Task6](https://github.com/Custodi4n/SQL_Practice/assets/113520737/08ff1be5-da9e-4fea-9538-01b015b3eb55)

## Task 7

```sql
SELECT EXISTS(SELECT name FROM person WHERE name= 'Peter' )
```

![Task7](https://github.com/Custodi4n/SQL_Practice/assets/113520737/be721384-2542-47a7-b408-59f3ed9ee9f2)


     
