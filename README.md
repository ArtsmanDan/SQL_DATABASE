## Базы данных и SQL (семинары)

### Урок 1. Установка СУБД, подключение к БД, просмотр и создание таблиц

1.  Создайте таблицу с мобильными телефонами, используя графический интерфейс. Заполните БД данными
    
2.  Выведите название, производителя и цену для товаров, количество которых превышает 2
    
3.  Выведите весь ассортимент товаров марки “Samsung”
    
    4.*** С помощью регулярных выражений найти:  
    4.1. Товары, в которых есть упоминание "Iphone"  
    4.2. "Samsung"  
    4.3. Товары, в которых есть ЦИФРА "8"



**Создание схемы(базы данных)**

    CREATE SCHEMA `mobilephone`;

**Выбор схемы(базы данных)**

    USE mobilephone;

**Создание  таблицы**

    CREATE TABLE `mobilephone`.`mobilephones` (
    
    `Id` INT NOT NULL AUTO_INCREMENT,
    
    `ProductName` VARCHAR(255) NOT NULL,
    
    `Manufacture` VARCHAR(255) NULL,
    
    `ProductCount` INT NOT NULL,
    
    `Price` INT NOT NULL,
    
    PRIMARY KEY (`Id`),
    
    UNIQUE INDEX `Id_UNIQUE` (`Id` ASC) VISIBLE);

**Добавление  данных**

    INSERT INTO `mobilephone`.`mobilephones` (`ProductName`, `Manufacture`, `ProductCount`, `Price`)
    
    VALUES
    
    ('IPhone 12', 'Apple', 10, 999),
    
    ('Galaxy S21', 'Samsung', 8, 899),
    
    ('Pixel 5', 'Google', 5, 699),
    
    ('OnePlus 9 Pro', 'OnePlus', 7, 899),
    
    ('Mi 11', 'Xiaomi', 12, 699),
    
    ('Xperia 1 III', 'Sony', 1, 1199),
    
    ('ROG Phone 5', 'Asus', 6, 1099),
    
    ('Mate 40 Pro', 'Huawei', 1, 1299),
    
    ('Nord 2', 'OnePlus', 9, 399),
    
    ('Redmi Note 10', 'Xiaomi', 15, 249),
    
    ('iPhone SE', 'Apple', 11, 399),
    
    ('Galaxy A52', 'samsung', 14, 349),
    
    ('Pixel 4a', 'Google', 8, 349),
    
    ('Xperia 5 II', 'Sony', 5, 899),
    
    ('ZenFone 8', 'Asus', 7, 599),
    
    ('P40 Pro', 'Huawei', 0, 999),
    
    ('Nokia 8.3', 'Nokia', 6, 599),
    
    ('Mi 10T Pro', 'Xiaomi', 9, 599),
    
    ('iPhone 11', 'Apple', 10, 699),
    
    ('Galaxy S20', 'Samsung', 8, 799);

**Выбор все полей и всех записей в таблице mobilephones**

    SELECT * FROM mobilephone.mobilephones;

**Выбор все полей в таблице mobilephones в записях, где количество продукта больше двух**

    SELECT * FROM mobilephone.mobilephones where ProductCount>2;

**Выведите весь ассортимент товаров марки “Samsung”**

    SELECT * FROM mobilephone.mobilephones
    WHERE LOWER(Manufacture)='Samsung';

**Выбор все полей в таблице mobilephones в записях, где в названии продукта присутствует «iPhone»**

    SELECT * FROM mobilephone.mobilephones
    where LOWER(ProductName) REGEXP 'iPhone';
    

    SELECT * FROM mobilephone.mobilephones
    where LOWER(ProductName) LIKE '%iPhone%';

**Выбор все полей в таблице mobilephones в записях, где в названии производителя присутствует «Samsung»**

    SELECT * FROM mobilephone.mobilephones
    where LOWER(Manufacture) REGEXP 'Samsung';
    
    SELECT * FROM mobilephone.mobilephones
    where LOWER(Manufacture) LIKE ‘%Samsung%';

**Выбор все полей в таблице mobilephones в записях, где в названии продукта присутствует цифра «8»**

    SELECT * FROM mobilephone.mobilephones
    where ProductName REGEXP '8';
    
    SELECT * FROM mobilephone.mobilephones
    where ProductName LIKE '%8%';

