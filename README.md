# Додаткові вбудовані функції SQL
### 1. Напишіть SQL-запит, який для таблиці orders з атрибута date витягує рік, місяць і число. Виведіть на екран їх у три окремі атрибути поряд з атрибутом id та оригінальним атрибутом date (всього вийде 5 атрибутів).
```
SELECT 
    id,
    date,
    EXTRACT(YEAR FROM date) AS year,
    EXTRACT(MONTH FROM date) AS month,
    EXTRACT(DAY FROM date) AS day
FROM 
    orders;
```
<img width="1010" alt="HW7_p1" src="https://github.com/user-attachments/assets/b9bbb4fe-6525-4354-ba46-486b3c9a282b">

### 2. Напишіть SQL-запит, який для таблиці orders до атрибута date додає один день. На екран виведіть атрибут id, оригінальний атрибут date та результат додавання.
```
SELECT 
    id,
    date,
    DATE_ADD(date, INTERVAL 1 DAY) AS date_plus_one
FROM 
    orders;
```
<img width="1009" alt="HW7_p2" src="https://github.com/user-attachments/assets/2c4a3121-d1a2-4960-a642-070ac7135378">

### 3. Напишіть SQL-запит, який для таблиці orders для атрибута date відображає кількість секунд з початку відліку (показує його значення timestamp). Для цього потрібно знайти та застосувати необхідну функцію. На екран виведіть атрибут id, оригінальний атрибут date та результат роботи функції.
```
SELECT 
    id,
    date,
    UNIX_TIMESTAMP(date) AS timestamp
FROM 
    orders;
```
<img width="1010" alt="HW7_p3" src="https://github.com/user-attachments/assets/7e8deb7e-80ac-4d8c-a254-d80ed1bf85ee">

### 4. Напишіть SQL-запит, який рахує, скільки таблиця orders містить рядків з атрибутом date у межах між 1996-07-10 00:00:00 та 1996-10-08 00:00:00.
```
SELECT 
    COUNT(*) AS row_count
FROM 
    orders
WHERE 
    date BETWEEN '1996-07-10 00:00:00' AND '1996-10-08 00:00:00';
```
<img width="583" alt="HW7_p4" src="https://github.com/user-attachments/assets/4c2ac193-07e0-4fd5-8668-a8a9fc18e7c4">

### 5. Напишіть SQL-запит, який для таблиці orders виводить на екран атрибут id, атрибут date та JSON-об’єкт {"id": <атрибут id рядка>, "date": <атрибут date рядка>}. Для створення JSON-об’єкта використайте функцію.
```
SELECT 
    id,
    date,
    JSON_OBJECT('id', id, 'date', date) AS json_object
FROM 
    orders;
```
<img width="1014" alt="HW7_p5" src="https://github.com/user-attachments/assets/600cb530-a5ff-4e1e-9de0-ed65a634b704">
