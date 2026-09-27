## Zadanie 1
```sql
insert into course.customers(
customer_id,
customer_name,
email,
country,
signup_date,
acquisition_channel
)

values(
22,
'Random Customer',
'random.customer@example.com',
'PL',
'2026-09-27',
'linkedin'
)
returning*;
```
## Zadanie 2
```sql
insert into course.products (
product_id,
product_name,
category,
base_price
)

values(
222,
'PySpark Notes',
'ebook',
49.99
)
returning product_id, product_name, base_price;
```
## Zadanie 3
```sql
update course.orders 
set status = 'cancelled'
where order_id = 1003
returning *;
```
## Zadanie 4
```sql
update course.customers 
set email = 'mariaschmidt@example.com'
where customer_id = 3
returning customer_id, customer_name, email;
```
## Zadanie 5
```sql
select * 
from course.order_items
where order_item_id = 14

delete from course.order_items 
where order_item_id = 14
returning *;
```
## Zadanie 6
```sql
select * 
from course.products p
left join course.order_items oi
on p.product_id = oi.product_id 
where oi.product_id is null;
```
identyfikuje anti joinem produkty bez zamowienia
```sql
delete from course.products p
where product_id = 109
returning product_id, product_name;
```
## Zadanie 7
```sql
begin;
```
```sql
select *
from course.customers 
where customer_id = 2;
```
```sql
update course.customers 
set country = 'DE', acquisition_channel = 'linkedin' 
where customer_id = 2 returning country, acquisition_channel;
```
```sql
rollback;
```
## Zadanie 8
```sql
begin;
```
```sql
select * 
from course.customers 
where customer_id = 22;
```
```sql
delete from course.customers 
where customer_id = 22
returning customer_id, customer_name, email, country, signup_date, acquisition_channel;
```
```sql
rollback;
```
## Zadanie 9
bo od razu pokazuje nowa wartosc
## Zadanie 10
bo pokazuje co zostało usuniete
