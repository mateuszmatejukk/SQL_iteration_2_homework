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
