## Урок 3. SQL – выборка данных, сортировка, агрегатные функции

### Вывести всю таблицу staff

    SELECT * 
    FROM staff;

### 1. Отсортируйте данные по полю заработная плата (salary) в порядке: убывания; возрастания

    SELECT * 
    FROM staff
    ORDER BY salary DESC;
    
    SELECT * 
    FROM staff
    ORDER BY salary;

### 2. Выведите 5 максимальных заработных плат (salary)  

    SELECT * 
    FROM staff 
    ORDER BY salary DESC 
    LIMIT 5 ;

### 3. Посчитайте суммарную зарплату (salary) по каждой специальности (роst)  

    SELECT post, SUM(salary)
    FROM staff
    GROUP BY post;
### 4. Найдите кол-во сотрудников с специальностью (post) «Рабочий» в возрасте от 24 до 49 лет включительно.  

    SELECT COUNT(id) AS 'кол-во сотрудников  на должности рабочий'
    FROM staff
    WHERE age >= 24 AND age <= 49 AND post = 'рабочий';

### 5. Найдите количество специальностей  

    SELECT COUNT(DISTINCT post)  AS 'Кол- во специальностей'
    FROM staff;

### 6. Выведите специальности, у которых средний возраст сотрудников меньше 30 лет (включительно)

    SELECT post, AVG(age) 
    FROM staff
    GROUP BY post 
    HAVING AVG(age) <= 30 ;
