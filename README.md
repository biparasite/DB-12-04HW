# Домашнее задание к занятию " `SQL. Часть 2` " - `Сулименков Алексей`

---

## Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию:

фамилия и имя сотрудника из этого магазина;
город нахождения магазина;
количество пользователей, закреплённых в этом магазине..

### Ответ

---

## Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

### Ответ

```SQL
SELECT COUNT(*) FROM sakila.film f WHERE f.`length` < (SELECT AVG(f.`length` ) FROM sakila.film f) ;
```

<details>  
  <summary>Скриншот к заданию 2</summary>    
  <div class="image-container">    
    <a href="https://github.com">    
      <span style="content:url('biparasite/DB-12-04HW/blob/main/task2.png')"></span>
    </a>
  </div>

[![task2](biparasite/DB-12-04HW/blob/main/task2.png "task2")](github.com)

</details>

---

## Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

### Ответ

```SQL

```

---
