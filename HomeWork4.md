
## Урок 4. SQL – работа с несколькими таблицами

### 1.Вывести всех котиков по магазинам по id (условие соединения shops.id = cats.shops_id)  

    SELECT cats.name, shops.shopname
    FROM cats
    LEFT JOIN shops ON shops.id = cats.shops_id;

### 2.Вывести магазин, в котором продается кот “Мурзик” (попробуйте выполнить 2 способами) 

    SELECT shops.shopname
    FROM shops
    INNER JOIN cats ON  shops.id = cats.shops_id
    WHERE cats.name = 'Murzik';
    
    SELECT shops.shopname
    FROM shops 
    WHERE id = (SELECT shops_id FROM cats WHERE name = 'Murzik');

 
### 3.Вывести магазины, в которых НЕ продаются коты “Мурзик” и “Zuza”

    SELECT shops.shopname
    FROM shops
    -- LEFT JOIN cats ON  shops.id = cats.shops_id AND (cats.name = 'Murzik' OR cats.name = 'Zuza')
    LEFT JOIN cats ON  shops.id = cats.shops_id AND cats.name IN ('Murzik', 'Zuza')
    WHERE cats.name IS NULL;

### 4.Вывести название и цену для всех анализов, которые продавались 5 февраля 2020 и всю следующую неделю.

    SELECT an_name, an_price
    FROM analysis
    RIGHT JOIN orders ON analysis.an_id = orders.ord_an
    WHERE ord_datetime BETWEEN '2020-02-05' AND '2020-02-12';
    
    SELECT an_name, an_price, gr_name
    FROM Analysis
    RIGHT JOIN Orders ON Analysis.an_id = Orders.ord_an
    LEFT JOIN groupsan ON Analysis.an_group = groupsan.gr_id
    WHERE ord_datetime BETWEEN '2020-02-05' AND '2020-02-12';

