## Урок 6. SQL – Транзакции. Временные таблицы, управляющие конструкции, циклы

### 1. Создайте процедуру, которая принимает кол-во сек и формат их в кол-во дней часов. Пример: 123456 ->'1 days 10 hours 17 minutes 36 seconds '

    DELIMITER //
    CREATE PROCEDURE getTime(seconds INT)
    BEGIN
        DECLARE days INT default 0;
        DECLARE hours INT default 0;
        DECLARE minutes INT default 0;
    
        WHILE seconds >= 86400 DO
        SET days = floor(seconds / 86400);
        SET seconds = seconds % 86400;
        END WHILE;
    
        WHILE seconds >= 3600 DO
        SET hours = floor(seconds / 3600);
        SET seconds = seconds % 3600;
        END WHILE;
    
        WHILE seconds >= 60 DO
        SET minutes = floor(seconds / 60);
        SET seconds = seconds % 60;
        END WHILE;
    
    SELECT days, hours, minutes, seconds;
    END //
    DELIMITER ;
    
    CALL getTime(564667);

### 2.  Создайте функцию, которая выводит только четные числа от 1 до 10. Пример: 2,4,6,8,10

    DELIMITER //
    CREATE PROCEDURE getEvenNumbers()
    BEGIN
        DECLARE x INT default 0;
        DROP TABLE IF EXISTS numbers;
        CREATE TABLE numbers (x INT);
    
        WHILE x < 10 DO
        SET x = x + 2;
        INSERT INTO numbers VALUES(x);
        END WHILE;
    
    SELECT * FROM numbers;
    END //
    DELIMITER ;
    
    CALL getEvenNumbers();
