# Patika.Dev-PostgreSQL
[ÖDEV 1](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-1)<br/>
[ÖDEV 2](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-2)<br/>
[ÖDEV 3](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-3)<br/>
[ÖDEV 4](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-4)<br/>
[ÖDEV 5](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-5)<br/>
[ÖDEV 6](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-6)<br/>
[ÖDEV 7](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-7)<br/>
[ÖDEV 8](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-8)<br/>
[ÖDEV 9](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-9)<br/>
[ÖDEV 10](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-10)<br/>
[ÖDEV 11](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#odev-11)<br/>
[ÖDEV 12](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#%C3%B6dev-12)<br/>
[GENEL TEKRAR](https://github.com/EmineOzbek/Patika.Dev-PostgreSQL/blob/main/README.md#genel-tekrar)<br/>
<br/>
## ÖDEV 1 
#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```sql
SELECT title, description FROM film;
```
#### Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
```sql
SELECT * FROM film
WHERE length > 60 AND length <75;
```
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız. 
```sql
SELECT * FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost =28.99;
```
#### Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir? 
```sql
SELECT last_name FROM customer 
WHERE first_name = 'Mary';
``` 
#### Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız. 
```sql
SELECT * FROM film
WHERE NOT length >50 AND NOT (rental_rate = 2.99 Or rental_rate = 4.99);
```
## ÖDEV 2 
#### Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız. (BETWEEN - AND yapısını kullanınız.) 
```sql
SELECT *FROM film 
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```
#### Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. (IN operatörünü kullanınız.)
```sql
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. (IN operatörünü kullanınız.) 
```sql
SELECT * FROM film
WHERE rental_rate IN (0.99,2.99,4.99) AND replacement_cost IN (12.99,15.99,28.99);
```
## ÖDEV 3 
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız. 
```sql
SELECT country FROM country
WHERE country LIKE 'A%a';
```
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```sql
SELECT country FROM country
WHERE length(country)>=6 AND country ~~'%n';
```
#### Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```sql
SELECT title FROM film 
WHERE title ILIKE '%t%t%t%t%';
```
#### Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız. 
```sql
SELECT * FROM film
WHERE title LIKE 'C%' AND length>90 AND rental_rate = 2.99;
```
## ÖDEV 4 
#### Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız. 
```sql
SELECT DISTINCT replacement_cost FROM film;
```
#### Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```sql
SELECT COUNT(DISTINCT replacement_cost) FROM film;
``` 
#### Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```
#### Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```sql
SELECT COUNT(*) FROM country
WHERE length(country)=5;
```
#### City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter? 
```sql
SELECT COUNT(*) FROM city 
WHERE city ILIKE '%r';
```
## ÖDEV 5
#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```sql
SELECT * FROM film 
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```
#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
```sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
```
#### Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```sql
SELECT * FROM customer
WHERE store_id =1
ORDER BY last_name DESC
LIMIT 4;
````
## ÖDEV 6
#### Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```sql
SELECT ROUND(AVG(rental_rate),3) FROM film;
```
#### Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
```sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
```
#### Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```sql
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```
#### Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```sql
SELECT COUNT (DISTINCT replacement_cost) FROM film
WHERE length>150;
```
## ÖDEV 7
#### Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```sql
SELECT rating FROM film
GROUP BY rating;
```
#### Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
````sql
SELECT replacement_cost,COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*)>50;
````
#### Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
````sql
SELECT store_id, COUNT(*) FROM customer 
GROUP BY store_id;
````
#### City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
````sql
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
````
## ÖDEV 8
#### Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
````sql
CREATE TABLE employee(
	id INTEGER,
	name VARCHAR(50) NOT NULL,
	birthday DATE NOT NULL,
	email VARCHAR(100)
);
````
#### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
````sql
insert into employee (id, name, birthday, email) values (1, 'Cherida Erie', '2020-12-26', 'cerie0@netvibes.com');
insert into employee (id, name, birthday, email) values (2, 'Ramona Rouff', '2020-08-05', 'rrouff1@github.io');
insert into employee (id, name, birthday, email) values (3, 'Heath Villa', '2020-07-29', 'hvilla2@rediff.com');
insert into employee (id, name, birthday, email) values (4, 'Sacha Matkin', '2021-06-29', 'smatkin3@cafepress.com');
insert into employee (id, name, birthday, email) values (5, 'Corrine Blowfelde', '2020-09-05', 'cblowfelde4@addthis.com');
insert into employee (id, name, birthday, email) values (6, 'Franzen Dunbabin', '2021-06-24', null);
insert into employee (id, name, birthday, email) values (7, 'Giffard Caroline', '2020-10-15', 'gcaroline6@smh.com.au');
insert into employee (id, name, birthday, email) values (8, 'Jeannine Jex', '2020-08-23', 'jjex7@wired.com');
insert into employee (id, name, birthday, email) values (9, 'Tiphani Insley', '2020-11-19', 'tinsley8@ocn.ne.jp');
insert into employee (id, name, birthday, email) values (10, 'Dacia Stapleton', '2021-06-21', 'dstapleton9@cdbaby.com');
insert into employee (id, name, birthday, email) values (11, 'Kalle Trumble', '2021-06-24', 'ktrumblea@reverbnation.com');
insert into employee (id, name, birthday, email) values (12, 'Gawain Tether', '2021-06-24', null);
insert into employee (id, name, birthday, email) values (13, 'Valli Blamire', '2020-09-09', 'vblamirec@jugem.jp');
insert into employee (id, name, birthday, email) values (14, 'Bastian Spragg', '2021-03-25', null);
insert into employee (id, name, birthday, email) values (15, 'Alexandrina Sousa', '2020-11-18', null);
insert into employee (id, name, birthday, email) values (16, 'Gallagher Thebeaud', '2021-04-09', 'gthebeaudf@squarespace.com');
insert into employee (id, name, birthday, email) values (17, 'Artair Beament', '2021-05-08', 'abeamentg@tuttocitta.it');
insert into employee (id, name, birthday, email) values (18, 'Olga Hellin', '2021-01-02', 'ohellinh@friendfeed.com');
insert into employee (id, name, birthday, email) values (19, 'Natassia Pasquale', '2021-01-06', 'npasqualei@mapy.cz');
insert into employee (id, name, birthday, email) values (20, 'Micheil Dreakin', '2021-06-10', 'mdreakinj@google.co.jp');
insert into employee (id, name, birthday, email) values (21, 'Mannie Worrell', '2020-07-16', 'mworrellk@dot.gov');
insert into employee (id, name, birthday, email) values (22, 'Doris Brouncker', '2021-05-20', 'dbrounckerl@ihg.com');
insert into employee (id, name, birthday, email) values (23, 'Berk Inglese', '2020-10-12', 'binglesem@shop-pro.jp');
insert into employee (id, name, birthday, email) values (24, 'Tamas Beyne', '2021-02-20', 'tbeynen@zimbio.com');
insert into employee (id, name, birthday, email) values (25, 'Benji Rens', '2021-06-19', 'brenso@nhs.uk');
insert into employee (id, name, birthday, email) values (26, 'Evan Haines', '2021-03-10', 'ehainesp@wikimedia.org');
insert into employee (id, name, birthday, email) values (27, 'Perceval Habbeshaw', '2020-08-16', 'phabbeshawq@fotki.com');
insert into employee (id, name, birthday, email) values (28, 'Nevin Vertigan', '2021-04-11', 'nvertiganr@soundcloud.com');
insert into employee (id, name, birthday, email) values (29, 'Ardine Marten', '2020-11-27', 'amartens@github.com');
insert into employee (id, name, birthday, email) values (30, 'Bevvy Ludford', '2021-01-18', 'bludfordt@springer.com');
insert into employee (id, name, birthday, email) values (31, 'Gerik Corington', '2021-01-31', 'gcoringtonu@boston.com');
insert into employee (id, name, birthday, email) values (32, 'Mischa Rupel', '2021-05-06', 'mrupelv@ameblo.jp');
insert into employee (id, name, birthday, email) values (33, 'Briney Franck', '2021-05-29', 'bfranckw@amazon.co.jp');
insert into employee (id, name, birthday, email) values (34, 'Muffin Bagby', '2020-10-04', 'mbagbyx@gmpg.org');
insert into employee (id, name, birthday, email) values (35, 'Othella Counsell', '2021-03-21', 'ocounselly@virginia.edu');
insert into employee (id, name, birthday, email) values (36, 'Mildrid Lowless', '2021-06-27', 'mlowlessz@tripod.com');
insert into employee (id, name, birthday, email) values (37, 'Kaja Lucock', '2021-01-04', 'klucock10@symantec.com');
insert into employee (id, name, birthday, email) values (38, 'Rosita Maddick', '2021-07-01', 'rmaddick11@instagram.com');
insert into employee (id, name, birthday, email) values (39, 'Melony Fadell', '2020-07-28', 'mfadell12@nytimes.com');
insert into employee (id, name, birthday, email) values (40, 'Madelina Boggers', '2021-05-04', 'mboggers13@seesaa.net');
insert into employee (id, name, birthday, email) values (41, 'Niel Georges', '2021-05-08', 'ngeorges14@technorati.com');
insert into employee (id, name, birthday, email) values (42, 'Cordy Manna', '2020-11-30', 'cmanna15@csmonitor.com');
insert into employee (id, name, birthday, email) values (43, 'Constancia Calderonello', '2021-05-12', null);
insert into employee (id, name, birthday, email) values (44, 'Sophi Rentelll', '2021-04-14', null);
insert into employee (id, name, birthday, email) values (45, 'Iseabal Preon', '2021-02-19', 'ipreon18@youtube.com');
insert into employee (id, name, birthday, email) values (46, 'Olivie Spittles', '2021-02-28', 'ospittles19@digg.com');
insert into employee (id, name, birthday, email) values (47, 'Lorrin Mac Geaney', '2021-06-18', 'lmac1a@storify.com');
insert into employee (id, name, birthday, email) values (48, 'Zelda Overil', '2020-10-27', 'zoveril1b@i2i.jp');
insert into employee (id, name, birthday, email) values (49, 'Kath Thirlwell', '2020-08-17', 'kthirlwell1c@sohu.com');
insert into employee (id, name, birthday, email) values (50, 'Abigale Lapwood', '2020-11-10', 'alapwood1d@360.cn');
````
#### Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
````sql
UPDATE employee
SET name = 'Emine Özbek',
 	birthday = '2020-05-08',
	email = 'emine@ozbek.com'
WHERE id =1;

UPDATE employee
SET id= 29,
	birthday = '1995-08-31',
	email = 'kalle@trumble.com'
WHERE name = 'Kalle Trumble';

UPDATE employee
SET id = 17,
	name = 'Nurullah Uğur',
	email = 'nurullah@ugur.com'
WHERE birthday = '2021-04-14';
````
#### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
````sql
DELETE FROM employee
WHERE id =1;

DELETE FROM employee
WHERE name = 'Sevda Sever';

DELETE FROM employee
WHERE birthday = '2021-02-28';

DELETE FROM employee
WHERE email = 'vblamirec@jugem.jp';
````

## ÖDEV 9
#### City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
````sql
SELECT city, country FROM city
INNER JOIN country ON city.country_id = country.country_id;
````
#### Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
````sql
SELECT payment_id, first_name, last_name FROM customer
INNER JOIN payment ON payment.customer_id = customer.customer_id;
````
#### Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
````sql
SELECT rental_id, first_name, last_name FROM customer
INNER JOIN rental ON rental.customer_id = customer.customer_id;
````

## ÖDEV 10
#### City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
````sql
SELECT city, country FROM city
LEFT JOIN country ON city.city_id = country.country_id;
````
#### Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
````sql
SELECT payment_id, first_name, last_name FROM customer
RIGHT JOIN payment ON payment.customer_id = customer.customer_id;
````
#### Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
````sql
SELECT rental_id, first_name, last_name FROM customer
FULL JOIN rental ON rental.customer_id = customer.customer_id;
````

## ODEV 11
#### Actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
````sql
(SELECT first_name FROM actor)
UNION 
(SELECT first_name FROM customer);
````
#### Actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
````sql
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
````
#### Actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
````sql
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);
````
#### İlk 3 sorguyu tekrar eden veriler için de yapalım.
````sql
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);
````
````sql
(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);
````
````sql
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
````

## ÖDEV 12
#### Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
````sql
SELECT COUNT(*) FROM film
WHERE length >
(
	SELECT AVG(length) FROM film
);
````
#### Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
````sql 
SELECT COUNT(*) FROM film
WHERE rental_rate =
(
	SELECT MAX(rental_rate) FROM film
);
````
#### Film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.
````sql
SELECT title FROM film
WHERE film_id = ANY
(
	SELECT film_id FROM film
	WHERE rental_rate= 
	(SELECT MIN (rental_rate) FROM film)
	AND  replacement_cost= 
	(SELECT MIN (replacement_cost) FROM film)
);
````
#### Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
````sql
SELECT first_name, last_name,
(
	SELECT COUNT(customer_id) 
	FROM payment 
	GROUP BY customer_id
	ORDER BY COUNT(customer_id) DESC
	LIMIT 1
)
FROM customer;
````

## GENEL TEKRAR
#### Film tablosunda isminde en az 4 adet 'e' veya 'E' karakteri bulunan kç tane film vardır?
````sql
SELECT COUNT(*) FROM film
WHERE title ILIKE '%e%e%e%e%';
````
#### Film tablosundan 'K' karakteri ile başlayan en uzun ve replacenet_cost u en düşük 4 filmi sıralayınız.
````sql
SELECT title, length, replacement_cost FROM film
WHERE title LIKE 'K%' 
ORDER BY length DESC, replacement_cost ASC
LIMIT 3;
````
#### Film tablosunda içerisinden en fazla sayıda film bulunduran rating kategorisi hangisidir?
````sql
SELECT rating, COUNT(rating) FROM film
GROUP BY rating
ORDER BY COUNT(*) DESC
LIMIT 1;
````
#### Customer tablosunda en çok alışveriş yapan müşterinin adı nedir?
````sql
SELECT first_name, last_name, SUM(amount) FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id, first_name, last_name
ORDER BY SUM(amount) DESC
LIMIT 1;
````
#### Category tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.
````sql
SELECT name, COUNT(*) FROM category
INNER JOIN film_category ON film_category.category_id = category.category_id
INNER JOIN film ON film_category.film_id = film.film_id
GROUP BY name;
````
