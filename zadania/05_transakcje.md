## Zadanie 1
```sql
begin;
```
## Zadanie 2
```sql
update course.orders 
set status = 'cancelled'
where order_id = 1003;
```
## Zadanie 3
```sql
select status 
from course.orders 
where order_id = 1003;
```
tak zmienil sie jest cancelled
## Zadanie 4
```sql
rollback;
```
## Zadanie 5
```sql
select status 
from course.orders 
where order_id = 1003;
```
tak status wrocil do pending
## Zadanie 6
```sql
begin
```
## Zadanie 7
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
3241,
'Krystian Żak',
'krystianzak@example.com',
'PL',
'2026-09-23',
'referral'
);
```
## Zadanie 8
```sql
insert into course.orders(
order_id,
customer_id,
order_date,
status,
total_amount
);

values (
3133,
3241,
'2026-09.23',
'paid',
250);
```
## Zadanie 9
```sql
insert into course.order_items(
order_item_id,
order_id,
product_id,
quantity,
unit_price)

values(
4141,
3133,
103,
2,
49.99);
```
## Zadanie 10
```sql
select 
c.customer_id,
c.customer_name,
c.email,
c.country, 
c.signup_date,
c.acquisition_channel
from course.customers c
join course.orders o
on c.customer_id = o.customer_id;

select 
o.order_id, 
o.customer_id,
o.order_date,
o.status,
o.total_amount
from course.orders o
join course.order_items oi
on o.order_id = oi.order_id;
```
## Zadanie 11
```sql
commit;
```
## Zadanie 12
tak
## Zadanie 13
```sql
update course.products 
set base_price = base_price * 1.2
where product_id = 101;

select product_id, base_price
from course.products
where product_id = 101;

rollback;
```
## Zadanie 14
commit zatwierdza zmiany a rollback je odrzuca
