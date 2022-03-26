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