## Zadanie 1
```sql
insert into course.customers(
customer_id,
customer_name,
email,
country,
signup_date,
acquisition_channel)

values(
123,
'Jan Pietrzak',
'jan.pietrzak@example.com',
'PL',
'2026-09-26',
'linkedin');
```
dodałem klienta
```sql
insert into course.orders(
order_id,
customer_id,
order_date,
status,
total_amount)

values(
1014,
123,
'2026-09-27',
'paid',
414);
```
dodałem zamówienie
```sql
insert into course.order_items (
order_item_id,
order_id,
product_id,
quantity,
unit_price)

values(
20,
1014,
108,
2,
310);
```
dodałem pozycje zamowienia
## Zadanie 2
```sql
select
c.customer_name,
o.order_id,
oi.product_id,
oi.quantity,
oi.unit_price
from course.customers c 
join course.orders o
on c.customer_id = o.customer_id 
join course.order_items oi
on o.order_id = oi.order_id
where o.order_id = 1014;
```
tak działa wszystko
## Zadanie 3
```sql
begin;
```
```sql
update course.orders 
set status = 'cancelled'
where order_id = 1014;
```
```sql
select *
from course.orders 
where order_id = 1014;
```
```sql
rollback;
```
## Zadanie 4
```sql
update course.orders 
set status = 'paid'
where order_id = 1014
returning *;
```
## Zadanie 5
```sql
insert into course.products(
product_id,
product_name,
category,
base_price)

values(
345,
'Pandas Tutorial',
'course',
39.99
)
returning *;
```
## Zadanie 6
```sql
insert into course.products(
product_id,
product_name,
category,
base_price)

values(
345,
'PySpark Tutorial',
'mentoring',
400
)
on conflict(product_id) do update set
product_name = excluded.product_name,
category = excluded.category,
base_price = excluded.base_price;
```
## Zadanie 7
```sql
delete from course.products 
where product_id = 345
returning *;
```
## Zadanie 8
```sql
delete from course.customers
where customer_id = 2;
```
SQL Error [23503]: BŁĄD: update or delete on table "customers" violates foreign key constraint "fk_orders_customers" on table "orders"
  Detail: Key (customer_id)=(2) is still referenced from table "orders".
Customer id jest wciąż przypisany do tabeli order.
## Zadanie 9
```sql
select * from course.order_items 
where order_item_id = 20;
```
kontrolny select
```sql
delete from course.order_items 
where order_item_id = 20
returning *;
```
```sql
select * 
from course.orders 
where order_id = 1014;
```
kontrolny select
```sql
delete from course.orders 
where order_id = 1014
returning *;
```
```sql
select * from course.customers
where customer_id = 123;
```
kontrolny select
```sql
delete from course.customers 
where customer_id = 123
returning *;
```
## Zadanie 10
```sql
insert into course.products (
product_id,
product_name,
category,
base_price)

values (
433,
'Polars Ebook',
'ebook',
49.99
)
on conflict (product_id) do update set
base_price = excluded.base_price;
```
## Zadanie 11
```sql
select 
product_id,
product_name,
category,
base_price,
round((base_price * 1.05),2) as new_price
from course.products 
where category = 'ebook'

insert into course.products (
product_id,
product_name,
category,
base_price)

values(
160,
'Databricks Notebook',
'ebook',
59.99
)
on conflict(product_id) do update set
base_price = excluded.base_price
where course.products.base_price is distinct from excluded.base_price;
```
## Zadanie 12
Przy DML należy napisać kontrolnego selecta z tym samym where którego użyję w zmianie. Przy wykonywaniu zmiany należy pamiętać o otworzeniu transakcji. Sprawdzam wynik poprzez porównanie wartości przed i po zmianie. Transakcji używam przy DML, kiedy zmiana modyfikuje dane, a szczególnie wtedy, kiedy obejmuje wiele rekordów.
