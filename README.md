# Домашнее задание к занятию " `SQL. Часть 2` " - `Сулименков Алексей`

---

## Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию:

фамилия и имя сотрудника из этого магазина;
город нахождения магазина;
количество пользователей, закреплённых в этом магазине..

### Ответ

```SQL
SELECT s.store_id,
       CONCAT(s2.first_name, ' ', s2.last_name) AS 'STAFF NAME',
       c2.city,
       COUNT(c.customer_id) AS 'COUNT CUSTOMER'
FROM sakila.store s
JOIN sakila.staff s2 ON s2.store_id = s.store_id
JOIN sakila.customer c ON c.store_id = s.store_id
JOIN sakila.address a ON a.address_id = s.address_id
JOIN sakila.city c2 ON c2.city_id = a.city_id
GROUP BY s.store_id, c2.city, s2.staff_id
HAVING (SELECT COUNT(*)
        FROM sakila.customer c
        WHERE c.store_id = s.store_id) > 300;
```

<details> <summary>Скриншот к заданию 1</summary>

![task1](https://github.com/biparasite/DB-12-04HW/blob/main/task1.png "task1")

</details>

---

## Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

### Ответ

```SQL
SELECT COUNT(*) FROM sakila.film f WHERE f.`length` < (SELECT AVG(f.`length` ) FROM sakila.film f) ;
```

<details> <summary>Скриншот к заданию 2</summary>

![task2](https://github.com/biparasite/DB-12-04HW/blob/main/task2.png "task2")

</details>

---

## Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

### Ответ

```SQL
SELECT
    MONTH(DATE(p.payment_date)) AS 'Month',
    SUM(p.amount) AS 'Total Amount',
    COUNT(p.rental_id) AS 'Rental Count'
FROM sakila.payment p
GROUP BY MONTH(DATE(p.payment_date))
ORDER BY SUM(p.amount) DESC
LIMIT 1;
```

<details> <summary>Скриншот к заданию 3</summary>

![task3](https://github.com/biparasite/DB-12-04HW/blob/main/task3.png "task3")

</details>

---
