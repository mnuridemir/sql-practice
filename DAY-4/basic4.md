# SQL practice
## SUB QUERY
- ### film tablosundan 'K' karakteri ile başlayan en uzun ve replacenet_cost u en düşük 4 filmi sıralayınız.
 ```sql
select title from film where title ilike '%e%e%e%e%'
```
- ### film tablosunda içerisinden en fazla sayıda film bulunduran rating kategorisi hangisidir?
 ```sql
select count(*),category.name from category
join film_category on category.category_id=film_category.category_id
join film on film.film_id=film_category.film_id
group by category.name;
```
- ### cutomer tablosunda en çok alışveriş yapan müşterinin adı nedir?
 ```sql
select count(*),rating from film group by rating order by count(*) desc limit 1;
```
- ### category tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.
 ```sql
select title, length, replacement_cost from film
where title like 'K%'
order by length desc, replacement_cost
limit 3;
```
- ### film tablosunda isminde en az 4 adet 'e' veya 'E' karakteri bulunan kç tane film vardır?
 ```sql
select customer.first_name, customer.last_name, sum(amount) from payment
join customer on customer.customer_id= payment.customer_id
group by payment.customer_id,customer.first_name, customer.last_name
order by sum(amount) desc;
```
