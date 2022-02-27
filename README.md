# PostgreSQL_PATİKA

## dvdrental


ÖDEV 1 

SELECT-WHERE-FROM

1-)Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.



```SQL
SELECT title , description
FROM film
```
2-) Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.


```SQL
SELECT *
FROM film
WHERE (length < 75 AND length > 60 );
```

3-) Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

```SQL

SELECT *
FROM film
WHERE (rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99) );

```
4-) Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```SQL
SELECT last_name
FROM customer
WHERE first_name='Mary';
```
Dataoutput ; Smith 



5-) Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```SQL

SELECT *
FROM film
WHERE ((NOT length>50)AND(rental_rate=2.99 OR  NOT rental_rate=4.99 ) );

```
ÖDEV 2 

BETWEEN-IN 

1-) Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

```SQL

SELECT *  FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.98 ;

```
2-) Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```SQL

SELECT first_name,last_name
FROM actor 
WHERE first_name IN ('Penelope' , 'Nick' , 'Ed');

```

3-) Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

```SQL

SELECT *
FROM film 
WHERE  rental_rate IN (0.99 , 2.99 , 4.99) AND replacement_cost IN (12.99 , 15.99 , 28.99  );

```

ÖDEV 3 

LIKE - ILIKE

1-) Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```SQL
SELECT *
FROM country
WHERE country LIKE 'A%a' ;

```
2-)Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```SQL
SELECT *
FROM country
WHERE country LIKE '_____n' ;

```
3-) Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```SQL

SELECT *
FROM film
WHERE title ILIKE '%t%t%t%t' ;

```

4-) Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```SQL

SELECT *
FROM film
WHERE title ILIKE 'C%' AND 	length >90 AND rental_rate=2.99;


```


ÖDEV 4 

DISTINCT-COUNT

1-) Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.


```SQL

SELECT  DISTINCT replacement_cost
FROM film ;



```

2-) Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?


```SQL

SELECT  COUNT (DISTINCT replacement_cost)
FROM film ;


```

3-) Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```SQL

SELECT  COUNT (title)
FROM film 
WHERE title LIKE 'T%' AND rating = 'G' ;


``` 

4-) Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?


```SQL

SELECT COUNT (country)
FROM country 
WHERE country LIKE '_____';


``` 


5-) City tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?


```SQL

SELECT COUNT (city)
FROM city 
WHERE city ILIKE '%R';

```


ÖDEV 5 

ORDER BY - LIMIT - OFFSET 

1-) Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

```SQL

SELECT * 
FROM film 
WHERE title LIKE '%n'
ORDER BY length DESC 
LIMIT  5 ;

```

2-) Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

```SQL

SELECT * 
FROM film 
WHERE title LIKE '%n' 
ORDER BY length 
OFFSET 5
LIMIT  5;

```



3-) Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```SQL

SELECT last_name
FROM customer
WHERE store_id = 1 
ORDER BY  last_name DESC
LIMIT  4;

```


ÖDEV 6

AGGREGATE FONKSİYONLAR


1-)Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?


```SQL

SELECT AVG(rental_rate)
FROM film ;

```

2-)Film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

```SQL

SELECT count(title)
FROM film
WHERE title LIKE 'C%' ; 


```

3-)Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```SQL

SELECT MAX(length) 
FROM film 
WHERE rental_rate=0.99 ;

```

4-)Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```SQL

SELECT  COUNT (DISTINCT replacement_cost)
FROM film 
WHERE length>150 ;

```


ÖDEV 7
HAVING - GROUP BY



1-) Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

```SQL

SELECT rating
FROM film
GROUP BY rating ; 



```




2-) Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

```SQL

SELECT replacement_cost,COUNT(*)
FROM film
GROUP BY replacement_cost 
HAVING COUNT(*) > 50;




```



3-) Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?


```SQL

SELECT store_id , COUNT(customer_id)
FROM  customer
GROUP BY store_id 



```



4-) City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

```SQL

SELECT country_id, COUNT (city)
FROM city
GROUP BY country_id
ORDER BY COUNT(city) DESC
LIMIT 1;




```

ÖDEV 8

VERİLERİ GÜNCELLEŞTİRME - SİLME
TABLO OLUŞTURMA - SİLME



1-) Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```SQL

CREATE TABLE employee (
  	id integer,
	name VARCHAR(50),
	birthday DATE,
    email VARCHAR(100) 
);

```

2-) Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.


```SQL

insert into employee (id, name, email, birthday) values (1, 'Adrianne', 'aohaire0@goo.gl', '2013-02-04');
insert into employee (id, name, email, birthday) values (2, 'Sharity', 'scleverley1@smh.com.au', '2012-10-25');
insert into employee (id, name, email, birthday) values (3, 'Joshia', 'jblasiak2@admin.ch', '2018-05-10');
insert into employee (id, name, email, birthday) values (4, 'Leonelle', 'ladess3@livejournal.com', '2015-07-21');
insert into employee (id, name, email, birthday) values (5, 'Renaldo', 'rsokell4@macromedia.com', '2014-10-02');
insert into employee (id, name, email, birthday) values (6, 'Scot', 'sbeale5@smugmug.com', '2014-06-20');
insert into employee (id, name, email, birthday) values (7, 'Mamie', 'mmilleton6@flavors.me', '1999-12-23');
insert into employee (id, name, email, birthday) values (8, 'Caz', 'csnufflebottom7@zimbio.com', '1992-05-12');
insert into employee (id, name, email, birthday) values (9, 'Ardyth', 'afoote8@feedburner.com', '1990-07-25');
insert into employee (id, name, email, birthday) values (10, 'Shalne', 'sselland9@geocities.com', '2018-07-07');
insert into employee (id, name, email, birthday) values (11, 'Del', 'dosgerbya@loc.gov', '2014-08-24');
insert into employee (id, name, email, birthday) values (12, 'Abra', 'aclimieb@gmpg.org', '2014-11-20');
insert into employee (id, name, email, birthday) values (13, 'Stormie', 'saccumc@squidoo.com', '2022-02-04');
insert into employee (id, name, email, birthday) values (14, 'Garth', 'gcratered@godaddy.com', '2002-03-02');
insert into employee (id, name, email, birthday) values (15, 'Zacharie', 'zchestermane@engadget.com', '1990-05-31');
insert into employee (id, name, email, birthday) values (16, 'Weylin', 'wdavidofff@mlb.com', '2004-09-06');
insert into employee (id, name, email, birthday) values (17, 'Lanna', 'lferrigeg@shinystat.com', '2018-05-20');
insert into employee (id, name, email, birthday) values (18, 'Elysia', 'eaynoldh@prlog.org', '2013-06-22');
insert into employee (id, name, email, birthday) values (19, 'Idell', 'iscroggesi@hc360.com', '2015-07-08');
insert into employee (id, name, email, birthday) values (20, 'Harrison', 'hshoosmithj@thetimes.co.uk', '2020-08-22');
insert into employee (id, name, email, birthday) values (21, 'Goddard', 'galdredk@cloudflare.com', '2007-08-20');
insert into employee (id, name, email, birthday) values (22, 'Torrance', 'tcolsonl@europa.eu', '2007-01-08');
insert into employee (id, name, email, birthday) values (23, 'Lela', 'ldeperom@netscape.com', '1995-01-23');
insert into employee (id, name, email, birthday) values (24, 'Miguelita', 'mdrewittn@wikispaces.com', '2007-07-06');
insert into employee (id, name, email, birthday) values (25, 'Marylinda', 'melwillo@uol.com.br', '2004-03-17');
insert into employee (id, name, email, birthday) values (26, 'Tabitha', 'tdunfordp@ucoz.ru', '2013-10-18');
insert into employee (id, name, email, birthday) values (27, 'Rowen', 'rrumminq@multiply.com', '2017-07-02');
insert into employee (id, name, email, birthday) values (28, 'Britni', 'bpacker@alibaba.com', '1992-08-01');
insert into employee (id, name, email, birthday) values (29, 'Carter', 'cllorentes@jalbum.net', '2013-11-11');
insert into employee (id, name, email, birthday) values (30, 'Lari', 'lpearst@usda.gov', '2018-11-13');
insert into employee (id, name, email, birthday) values (31, 'Templeton', 'thazletonu@dedecms.com', '1999-09-01');
insert into employee (id, name, email, birthday) values (32, 'Marabel', 'mcourtoisv@techcrunch.com', '2017-11-28');
insert into employee (id, name, email, birthday) values (33, 'Sibyl', 'stomaszw@indiegogo.com', '2020-07-09');
insert into employee (id, name, email, birthday) values (34, 'Joanie', 'jchildrensx@twitter.com', '1990-11-19');
insert into employee (id, name, email, birthday) values (35, 'Keeley', 'kdonegany@si.edu', '2008-01-07');
insert into employee (id, name, email, birthday) values (36, 'Fredi', 'ffahyz@ocn.ne.jp', '1999-06-03');
insert into employee (id, name, email, birthday) values (37, 'Sue', 'sdicken10@tripadvisor.com', '2009-07-24');
insert into employee (id, name, email, birthday) values (38, 'Nicol', 'nheilds11@blogger.com', '2007-01-08');
insert into employee (id, name, email, birthday) values (39, 'Herschel', 'hcutmere12@techcrunch.com', '2013-05-04');
insert into employee (id, name, email, birthday) values (40, 'Aube', 'amoynihan13@slashdot.org', '2003-11-27');
insert into employee (id, name, email, birthday) values (41, 'Craggie', 'cpharro14@oakley.com', '1992-09-01');
insert into employee (id, name, email, birthday) values (42, 'Howey', 'hgingell15@360.cn', '2001-03-12');
insert into employee (id, name, email, birthday) values (43, 'Halli', 'htrowill16@cloudflare.com', '1994-09-24');
insert into employee (id, name, email, birthday) values (44, 'Rachele', 'rbridgement17@blogtalkradio.com', '1999-12-26');
insert into employee (id, name, email, birthday) values (45, 'Mirella', 'mdobell18@gravatar.com', '2020-07-02');
insert into employee (id, name, email, birthday) values (46, 'Miquela', 'mpossa19@mtv.com', '1991-02-13');
insert into employee (id, name, email, birthday) values (47, 'Tomaso', 'ttitchen1a@usatoday.com', '2017-04-24');
insert into employee (id, name, email, birthday) values (48, 'Even', 'edunkley1b@angelfire.com', '1993-08-27');
insert into employee (id, name, email, birthday) values (49, 'Austin', 'akeelan1c@taobao.com', '2019-03-07');
insert into employee (id, name, email, birthday) values (50, 'Brockie', 'breffe1d@squidoo.com', '2003-12-03');
insert into employee (id, name, email, birthday) values (51, 'Tremaine', 'tcookes1e@patch.com', '2008-01-01');
insert into employee (id, name, email, birthday) values (52, 'Nessie', 'nkincade1f@over-blog.com', '1994-09-17');
insert into employee (id, name, email, birthday) values (53, 'Merissa', 'mtejada1g@canalblog.com', '2011-01-11');
insert into employee (id, name, email, birthday) values (54, 'Lief', 'lthorp1h@t.co', '1993-06-11');
insert into employee (id, name, email, birthday) values (55, 'Penn', 'pknoles1i@baidu.com', '1994-10-10');
insert into employee (id, name, email, birthday) values (56, 'Kirsteni', 'ktomaskov1j@dion.ne.jp', '2021-04-09');
insert into employee (id, name, email, birthday) values (57, 'Bunnie', 'bbuntine1k@skyrock.com', '2018-02-18');
insert into employee (id, name, email, birthday) values (58, 'Janek', 'jaizikov1l@tripadvisor.com', '2009-11-26');
insert into employee (id, name, email, birthday) values (59, 'Ad', 'adumbare1m@elegantthemes.com', '2016-04-02');
insert into employee (id, name, email, birthday) values (60, 'Emilia', 'erickis1n@wufoo.com', '2002-05-20');
insert into employee (id, name, email, birthday) values (61, 'Lambert', 'lschaumaker1o@goo.ne.jp', '2005-04-07');
insert into employee (id, name, email, birthday) values (62, 'Winonah', 'wcapozzi1p@google.cn', '1994-11-09');
insert into employee (id, name, email, birthday) values (63, 'Fonz', 'fcourtois1q@dion.ne.jp', '1990-10-08');
insert into employee (id, name, email, birthday) values (64, 'Holly-anne', 'hpullan1r@jugem.jp', '2015-04-04');
insert into employee (id, name, email, birthday) values (65, 'Rikki', 'rlyte1s@bbc.co.uk', '2019-01-20');
insert into employee (id, name, email, birthday) values (66, 'Corry', 'cdelve1t@elpais.com', '2010-04-18');
insert into employee (id, name, email, birthday) values (67, 'Tyne', 'tiacovaccio1u@ning.com', '2013-01-03');
insert into employee (id, name, email, birthday) values (68, 'Ronnie', 'rrosnau1v@newsvine.com', '1993-11-22');
insert into employee (id, name, email, birthday) values (69, 'Vernor', 'vshearmer1w@google.ca', '2012-05-06');
insert into employee (id, name, email, birthday) values (70, 'Fidel', 'fwittke1x@stanford.edu', '2015-06-18');
insert into employee (id, name, email, birthday) values (71, 'Arabella', 'awildor1y@chronoengine.com', '2003-01-06');
insert into employee (id, name, email, birthday) values (72, 'Jaquith', 'jfellgatt1z@phoca.cz', '2018-10-01');
insert into employee (id, name, email, birthday) values (73, 'Ofilia', 'obounde20@ucla.edu', '2013-02-10');
insert into employee (id, name, email, birthday) values (74, 'Obadias', 'ospeariett21@alexa.com', '1990-04-29');
insert into employee (id, name, email, birthday) values (75, 'Glennis', 'gvigus22@ucla.edu', '2013-05-01');
insert into employee (id, name, email, birthday) values (76, 'Dorise', 'dredmond23@netscape.com', '2010-04-11');
insert into employee (id, name, email, birthday) values (77, 'Loni', 'lhann24@csmonitor.com', '1999-02-05');
insert into employee (id, name, email, birthday) values (78, 'Mandy', 'mprater25@amazon.com', '1994-10-30');
insert into employee (id, name, email, birthday) values (79, 'Allan', 'arozzier26@google.nl', '2009-08-27');
insert into employee (id, name, email, birthday) values (80, 'Sarine', 'sriehm27@mapquest.com', '2008-05-08');
insert into employee (id, name, email, birthday) values (81, 'Dori', 'dphebey28@harvard.edu', '1990-08-08');
insert into employee (id, name, email, birthday) values (82, 'Ferrel', 'framsdell29@yelp.com', '1998-07-24');
insert into employee (id, name, email, birthday) values (83, 'Jeanne', 'jnassi2a@php.net', '2013-11-06');
insert into employee (id, name, email, birthday) values (84, 'Annamarie', 'awilmut2b@squidoo.com', '2005-05-05');
insert into employee (id, name, email, birthday) values (85, 'Estell', 'ewillatt2c@pinterest.com', '1992-06-20');
insert into employee (id, name, email, birthday) values (86, 'Ashlie', 'asporton2d@vistaprint.com', '2011-06-15');
insert into employee (id, name, email, birthday) values (87, 'Philippe', 'ptraves2e@yandex.ru', '1994-11-24');
insert into employee (id, name, email, birthday) values (88, 'Barclay', 'bobradain2f@w3.org', '2001-03-13');
insert into employee (id, name, email, birthday) values (89, 'Morry', 'mmacgaughey2g@census.gov', '2011-06-03');
insert into employee (id, name, email, birthday) values (90, 'Ivy', 'imellon2h@si.edu', '1990-06-22');
insert into employee (id, name, email, birthday) values (91, 'Ranice', 'rmcleman2i@weibo.com', '1999-06-05');
insert into employee (id, name, email, birthday) values (92, 'Anabel', 'afussey2j@opensource.org', '2006-12-18');
insert into employee (id, name, email, birthday) values (93, 'Abigail', 'amellonby2k@ameblo.jp', '2017-06-13');
insert into employee (id, name, email, birthday) values (94, 'Amalle', 'aaugustus2l@weather.com', '1992-07-24');
insert into employee (id, name, email, birthday) values (95, 'Elana', 'eiannelli2m@gravatar.com', '1997-01-26');
insert into employee (id, name, email, birthday) values (96, 'Lothario', 'ljeynes2n@columbia.edu', '1994-03-27');
insert into employee (id, name, email, birthday) values (97, 'Molly', 'mduckerin2o@prweb.com', '2011-08-24');
insert into employee (id, name, email, birthday) values (98, 'Meggi', 'mwhorlton2p@bloglines.com', '2020-10-01');
insert into employee (id, name, email, birthday) values (99, 'Leese', 'lcottell2q@chicagotribune.com', '2005-10-27');
insert into employee (id, name, email, birthday) values (100, 'Paul', 'pannies2r@microsoft.com', '2019-11-16');

```


3-) Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

```SQL

UPDATE employee
 SET name='Enes',
     email='Enes_FLZ@protonmail.com'
  WHERE id  BETWEEN 1 AND 5; 

```





4-) Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.


```SQL

DELETE FROM employee
WHERE id > 45 
RETURNING *;

```



ÖDEV 9
INNER JOIN


1-) City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```SQL

SELECT city.city_id , country.country_id
FROM city
INNER JOIN country ON city.country_id = country.country_id ;

```


2-) Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```SQL

SELECT payment.payment_id ,customer.first_name , customer.last_name
FROM customer
INNER JOIN payment
ON customer.customer_id = payment.customer_id ; 

```


3-) Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```SQL

SELECT rental_id, first_name, last_name
FROM customer
INNER JOIN rental
ON customer.customer_id=rental.customer_id;

```


ÖDEV 10
LEFT JOIN - RIGHT JOIN - 	FULL JOIN


1-) City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

```SQL

SELECT city,country
FROM city
LEFT JOIN country
ON city.country_id=country.country_id;


```

2-) Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

```SQL

SELECT payment_id,first_name,last_name
FROM customer
RIGHT JOIN payment
ON customer.customer_id=payment.customer_id;

```


3-) Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

```SQL

SELECT rental_id,first_name,last_name
FROM customer
FULL JOIN rental
ON customer.customer_id=rental.customer_id;

```











