## Zadanie 1
```sql
insert into course.customers (
customer_id,
customer_name,
email,
country,
signup_date,
acquisition_channel
)
values (
9,
'Jan Kowalski',
'jan.kowalski@example.com',
'PL',
'2026-08-01',
'organic'
);
```
## Zadanie 2
```sql
select *
from course.customers c
where c.customer_id = 9
```
## Zadanie 3
```sql
insert into course.customers (
customer_id,
customer_name,
email,
country,
signup_date,
acquisition_channel
)
values(
10,
'customer without email',
null,
'CZ',
'2026-09-13',
'google');
```
## Zadanie 4
```sql
select *
from course.customers
where customer_id = 10;
```
## Zadanie 5
```sql
insert into course.products(
product_id,
product_name,
category,
base_price)

values 
(201,'SQL Pack Practice','course',99.00),
(202,'Data PDF Notes', 'ebook', 29.00);
```
## Zadanie 6
```sql
select *
from course.products
where product_id = 201 or product_id = 202
```
## Zadanie 7
```sql
insert into course.orders(
order_id,
customer_id,
order_date,
status,
total_amount)

values(
1013,
10,
'2026-09-13',
'paid',
120.00);
```
## Zadanie 8
```sql
insert into course.order_items (
order_item_id,
order_id,
product_id,
quantity,
unit_price)

values(
15,
1013,
108,
2,
190);
```

## Zadanie 9
```sql
insert into course.order_items (
order_item_id,
order_id,
product_id,
quantity,
unit_price)

values(
16,
1013,
106,
2,
170);
```
## Zadanie 10
```sql
select 
oi.order_item_id,
o.order_id,
oi.product_id,
oi.quantity,
oi.unit_price
from course.order_items oi 
join course.orders o
on oi.order_id = o.order_id
where oi.order_id = 1013;
```
## Zadanie 11
```sql
insert into course.customers(
customer_id,
customer_name,
email,
country,
signup_date,
acquisition_channel)

values(
2,
'Random',
'random@example.com',
'PL',
'2026-09-16',
'linkedin'); 
SQL Error [23505]: BŁĄD: podwójna wartość klucza narusza ograniczenie unikalności "customers_pkey"
  Detail: Klucz (customer_id)=(2) już istnieje.
```
## Zadanie 12
```sql
insert into course.orders(
order_id,
customer_id,
order_date,
status,
total_amount)

values(
123,
24150913,
'2026-09-16',
'pending',
245);
SQL Error [23503]: BŁĄD: wstawianie lub modyfikacja na tabeli "orders" narusza klucz obcy "fk_orders_customers"
  Detail: Klucz (customer_id)=(24150913) nie występuje w tabeli "customers".
```
## Zadanie 13
```sql
insert into course.products(
product_id,
product_name,
category,
base_price)

values(
140,
null,
'ebook',
414)
SQL Error [23502]: BŁĄD: null value in column "product_name" of relation "products" violates not-null constraint
  Detail: Niepoprawne ograniczenia wiersza (140, null, ebook, 414.00).
```
