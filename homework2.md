# Урок 2. SQL – создание объектов, простые запросы выборки

## 1. Используя операторы языка SQL, создайте табличку “sales”. Заполните ее данными

    CREATE SCHEMA `homework2` ;
    
    CREATE TABLE `homework2`.`sales` (
      `id` INT NOT NULL AUTO_INCREMENT,
      `order_date` VARCHAR(45) NOT NULL,
      `count_product` INT NOT NULL,
      PRIMARY KEY (`id`));
    
    
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-11', '155');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-21', '20');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-31', '132');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-02', '354');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-03', '28');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-04', '127');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-05', '371');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-06', '57');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-06', '289');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-07', '700');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-08', '98');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-09', '165');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-10', '224');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-11', '643');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-13', '73');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-14', '236');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-15', '923');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-16', '63');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-17', '299');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-18', '621');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-19', '56');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-20', '182');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-21', '837');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-22', '29');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-23', '232');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-24', '534');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-25', '75');
    INSERT INTO `homework2`.`sales` (`order_date`, `count_product`) VALUES ('2023-05-26', '133');

## 2. Сгруппируйте значений количества в 3 сегмента — меньше 100, 100-300 и больше 300 (функция IF).

    SELECT 
    id AS 'id заказа',
    order_date AS 'Дата заказа',
    IF (count_product < 100, 'Малый заказ', 	
    	IF (count_product  between 100 AND 300, 'Средний заказ', 'Большой заказ')) AS 'Тип'
    FROM homework2.sales;

## 3. Создайте таблицу “orders”, заполните ее значениями. Покажите “полный” статус заказа, используя оператор CASE

    CREATE TABLE `homework2`.`orders` (
      `id` INT NOT NULL AUTO_INCREMENT,
      `employee_id` VARCHAR(45) NOT NULL,
      `amount` VARCHAR(45) NOT NULL,
      `order_status` VARCHAR(45) NOT NULL,
      PRIMARY KEY (`id`));ALTER TABLE `homework2`.`orders` 
    ADD UNIQUE INDEX `id_UNIQUE` (`id` ASC) VISIBLE;
    
    INSERT INTO `homework2`.`orders` (`employee id`, `amount`, `order status`) VALUES ('e03', '15.00', 'OPEN');
    INSERT INTO `homework2`.`orders` (`employee id`, `amount`, `order status`) VALUES ('e01', '23.50', 'OPEN');
    INSERT INTO `homework2`.`orders` (`employee id`, `amount`, `order status`) VALUES ('e05', '100.7', 'CLOSED');
    INSERT INTO `homework2`.`orders` (`employee id`, `amount`, `order status`) VALUES ('e02', '22.18', 'OPEN');
    INSERT INTO `homework2`.`orders` (`employee id`, `amount`, `order status`) VALUES ('e04', '9.50', 'CANCELLED');
    
    
    
    
    SELECT id, employee_id, amount,
    CASE
    WHEN order_status = 'OPEN' THEN 'Order is in open state'
        WHEN order_status = 'CLOSED' THEN 'Order is closed'
        WHEN order_status = 'CANCELLED' THEN 'Order is cancelled'
        ELSE 'UNKNOW'
    END AS 'full_order_status'
    FROM homework2.orders;

## 4. Чем NULL отличается от 0?

NULL - это особое значение, которое указывает на отсутствие данных или неизвестное значение. Оно используется, когда значение не может быть определено или когда данные отсутствуют. NULL не является нулем и не имеет числового значения. Оно является отдельным типом данных в MySQL и используется для обозначения пустоты или отсутствия значения.

0, с другой стороны, является числовым значением и представляет ноль. Он используется для обозначения конкретного числового значения и отличается от NULL.

Разница между NULL и 0 проявляется в операциях и сравнениях. Например, сравнение NULL с любым числовым значением, включая 0, будет возвращать NULL, поскольку значение NULL неизвестно. С другой стороны, сравнение 0 с другими числовыми значениями будет производиться на основе числовых операций и возвращать соответствующие результаты.

Вот примеры, иллюстрирующие различие между NULL и 0:

SELECT NULL + 5; -- Вернет NULL, поскольку значение NULL неизвестно
SELECT 0 + 5; -- Вернет 5, поскольку 0 + 5 = 5

SELECT NULL = 0; -- Вернет NULL, поскольку значение NULL неизвестно
SELECT 0 = 0; -- Вернет 1, поскольку 0 равно 0
