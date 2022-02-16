--- SQL-1_PATİKA
--- dvdrental


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



