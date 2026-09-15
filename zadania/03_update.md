## Zadanie 1
```sql
select *
from course.customers c
where customer_id = 6;
```
## Zadanie 2
```sql
update course.customers 
set email = 'claire.new@example.com'
where customer_id = 6;
```
## Zadanie 3
```sql
select customer_id, email
from course.customers c
where customer_id = 6
```
## Zadanie 4
```sql
update course.customers 
set acquisition_channel = 'linkedin'
where customer_id = 6;
```
## Zadanie 5
```sql
select customer_id, acquisition_channel
from course.customers c
where customer_id = 6
```
## Zadanie 6
```sql
update course.products
set base_price = base_price * 1.10
where category = 'course';
```
## Zadanie 7
```sql
select * 
from course.products;
```
## Zadanie 8
```sql
update course.orders
set status = 'paid'
where status = 'pending'
and total_amount < 100;
```
## Zadanie 9
```sql
select * 
from course.orders
where status = 'paid'
and total_amount < 100;
```
## Zadanie 10
```sql
select *
from course.customers
where country = 'FR';

update course.customers 
set country = 'PL'
where country = 'FR';
```
## Zadanie 11
```sql
update course.order_items
set unit_price = 130.00
where order_item_id = 1;
```
## Zadanie 12
```sql
select *
from course.order_items
where product_id = 103

update course.order_items 
set quantity = 2
where product_id = 103
```
## Zadanie 13
zostałaby zaktualizowana cała kolumna zamiast poszczególnych rekordów co wprowadziłoby zamieszanie w tabeli

## Zadanie 14
```sql
select
o.order_id,
o.total_amount,
oi.items_value
from course.orders o
join(
select 
order_id,
sum(quantity * unit_price) as items_value
from course.order_items oi 
group by order_id
)oi
on o.order_id = oi.order_id;
```
## Zadanie 15
```sql
update course.orders o
set total_amount = oi.items_value
from(
select
order_id,
sum(quantity * unit_price) as items_value
from course.order_items
group by order_id
)oi
where o.order_id = oi.order_id;	
```
