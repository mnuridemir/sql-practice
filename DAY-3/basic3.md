# SQL practice
## CREATE TABLE - UPDATE TABLE - DELETE TABLE 
- ### test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
 ```sql
CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50),
	birthdat DATE,
	email VARCHAR(100)
);
```
- ### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim. (örnek olarak 5 tane)
 ```sql
insert into employee (id, name, birthday, email) values (1, 'Chucho Klaes', '1940-04-22', 'cklaes0@linkedin.com');
insert into employee (id, name, birthday, email) values (2, 'Marie-jeanne Rotham', '1913-02-23', 'mrotham1@ucsd.edu');
insert into employee (id, name, birthday, email) values (3, 'Griswold Wrathall', '1929-12-20', 'gwrathall2@twitter.com');
insert into employee (id, name, birthday, email) values (4, 'Hugibert Baldrick', '1956-05-20', 'hbaldrick3@cdc.gov');
insert into employee (id, name, birthday, email) values (5, 'Arabele Larking', '1946-02-02', 'alarking4@w3.org');
insert into employee (id, name, birthday, email) values (6, 'Dieter Arpe', '1976-09-28', 'darpe5@com.com');
```
- ### Sütunların her birine göre diğer sütunları güncelleyecek UPDATE işlemi yapalım.
```sql
UPDATE employee
SET
	name = 'Mehmet Demir',
	birthday = '1999-12-11',
	email = 'md@gmail.com'
WHERE id =1;
```
- ### Sütunların her birine göre ilgili satırı silecek DELETE işlemi yapalım.
```sql
DELETE FROM employee WHERE id<35;
```
## JOIN 
- ### city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT city,country FROM city INNER JOIN country ON city.country_id = country.country_id;
```
- ### customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT payment_id,first_name,last_name FROM customer INNER JOIN payment ON payment.customer_id = customer.customer_id;
```
- ### customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT rental_id,first_name,last_name FROM customer INNER JOIN rental ON rental.customer_id = customer.customer_id;
```
- ### city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```sql
SELECT city,country FROM city LEFT JOIN country ON city.country_id = country.country_id;
```
- ### customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```sql
SELECT payment_id,first_name,last_name FROM customer RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
```
- ### customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```sql
SELECT rental_id,first_name,last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
```
## UNION - INTERSECT - EXCEPT 
- ### actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
```sql
(SELECT first_name FROM actor) UNION (SELECT first_name FROM customer);
```
- ### actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
```sql
(SELECT first_name FROM actor) INTERSECT (SELECT first_name FROM customer);
```
- ### actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```sql
(SELECT first_name FROM actor) EXCEPT (SELECT first_name FROM customer);
```
## SUB QUERY
- ### film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```sql
SELECT COUNT(title) FROM film WHERE length > (SELECT AVG(length) FROM film);
```
- ### film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```sql
SELECT COUNT(title) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);
```
- ### film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
```sql
SELECT * FROM film WHERE (rental_rate = (SELECT MIN(rental_rate) FROM film)) AND (replacement_cost = (SELECT MIN(replacement_cost) FROM film));
```
- ### payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```sql
SELECT customer.first_name,customer.last_name,customer.customer_id,COUNT(customer.customer_id) 
FROM customer LEFT JOIN payment ON payment.customer_id = customer.customer_id
GROUP BY customer.first_name,customer.last_name,customer.customer_id
ORDER BY COUNT(customer.customer_id) DESC;
```