## Урок 5. SQL – оконные функции

### 1. Создайте представление, в которое попадут автомобили стоимостью до 25 000 долларов  

    CREATE VIEW `cars_less_view` AS
    SELECT *
    FROM cars
    WHERE cost < 25000;
    
    SELECT * FROM cars_less_view;

### 2. Изменить в существующем представлении порог для стоимости: пусть цена будет до 30 000 долларов (используя оператор ALTER VIEW)  

    ALTER VIEW `cars_less_view` AS
    SELECT *
    FROM cars
    WHERE cost < 30000;
    
    SELECT * FROM cars_less_25000_view;

### 3. Создайте представление, в котором будут только автомобили марки “Шкода” и “Ауди”

    CREATE VIEW `cars_be_Skoda_Audi_view` AS
    SELECT *
    FROM cars
    WHERE name IN ('Skoda', 'Audi');
    
    SELECT * FROM cars_be_Skoda_Audi_view;
