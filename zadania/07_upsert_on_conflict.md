## Zadanie 1
SQL Error [23505]: BŁĄD: duplicate key value violates unique constraint "customers_pkey"
  Detail: Key (customer_id)=(1) already exists.
Baza nie pozwoliła dodać drugiego klienta z tym samym identyfikatorem.
## Zadanie 2
```sql
insert into course.customers(
customer_id,
customer_name,
email,
country,
signup_date,
acquisition_channel)

values(
1,
'Random Customer',
'random.customer@example.com',
'PL',
'2026-09-27',
'linkedin'
)
ON CONFLICT (customer_id) DO nothing;
```
## Zadanie 3
```sql
select *
from course.customers 
where customer_id = 1;
```
nie nie zmieniły sie
## Zadanie 4
```sql
update course.customers 
set 
email = 'new_mail@example.com',
acquisition_channel = 'organic'
where customer_id = 1
ON CONFLICT (customer_id) DO update;
```
## Zadania 5
```sql
select * 
from course.customers 
where customer_id = 1;
```
## Zadanie 6
```sql
insert into course.products(
product_id,
product_name,
category,
base_price)

values(
107,
'Airflow Mentoring',
'mentoring',
150.00
)

on conflict (product_id) do update set
product_name = excluded.product_name,
category = excluded.category,
base_price = excluded.base_price;
```
## Zadanie 7
```sql
insert into course.products(
product_id,
product_name,
category,
base_price)

values(
333,
'Polars Ebook',
'ebook',
49.99
)

on conflict (product_id) do update set
product_name = excluded.product_name,
category = excluded.category,
base_price = excluded.base_price;
```
## Zadanie 8
```sql
select * from course.products 
where product_id = 333;
```
nie
## Zadanie 9
```sql
insert into course.orders(
order_id,
customer_id,
order_date,
status,
total_amount)

values(
1012,
1,
'2026-09-26',
'paid',
190)

on conflict(order_id) do update set
customer_id = excluded.customer_id,
order_date = excluded.order_date,
status = excluded.status,
total_amount = excluded.total_amount;
```
## Zadanie 10
```sql
insert into course.order_items(
order_item_id,
order_id,
product_id,
quantity,
unit_price)

values(
16,
1004,
104,
2,
329)

on conflict (order_item_id) do update set
order_id = excluded.order_id,
product_id = excluded.product_id,
quantity = excluded.quantity,
unit_price = excluded.unit_price;
```
## Zadanie 11
Do nothing najlepiej użyć kiedy jesteśmy pewni, że chcemy zignorować duplikat.
## Zadanie 12
Lepiej użyć do update kiedy chcemy zaktualizować jakiś rekord.
## Zadanie 13
Dzięki upsertowi pipeline nadal będzie działał mimo takiego samego inputu
