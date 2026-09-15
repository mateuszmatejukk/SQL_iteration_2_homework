## Zadanie 1
```sql
select *
from course.order_items
where order_item_id = 14;
```
## Zadanie 2
```sql
delete from course.order_items
where order_item_id = 14;
```
## Zadanie 3
```sql
select *
from course.order_items
where order_item_id = 14;
```
tak usunelo sie
## Zadanie 4
```sql
insert into course.products 
(
product_id,
product_name,
category,
base_price
)

values(
222,
'Databricks Ebook',
'ebook',
49.95
);
```
## Zadanie 5
```sql
select * from course.products 
where product_id = 222;
```
dziala 
## Zadanie 6
```sql
delete from course.products 
where product_id = 222;
```
## Zadanie 7
```sql
select * from course.products 
where product_id = 222;
```
usunelo sie
## Zadanie 8
```sql
select * from course.orders 
where customer_id = 1;
testowy select
SQL Error [23503]: BŁĄD: modyfikacja lub usunięcie na tabeli "orders" narusza klucz obcy "fk_order_items_orders" tabeli "order_items"
  Detail: Klucz (order_id)=(1001) ma wciąż odwołanie w tabeli "order_items".
```
inna tabela wciaz odnosi sie do tego customer id 
## Zadanie 9
```sql
select * from course.order_items
where product_id = 108;
testowy select
SQL Error [23503]: BŁĄD: modyfikacja lub usunięcie na tabeli "products" narusza klucz obcy "fk_order_items_products" tabeli "order_items"
  Detail: Klucz (product_id)=(108) ma wciąż odwołanie w tabeli "order_items".
```
tak jak wyzej
## Zadanie 10
```sql
select 
oi.order_id, 
o.status,
oi.order_item_id
from course.orders o  
join course.order_items oi
on o.order_id = oi.order_id 
where o.status = 'cancelled';

delete from course.order_items oi
using course.orders o
where oi.order_id = o.order_id 
and o.status = 'cancelled';
```
## Zadanie 11
```sql
select 
oi.order_item_id,
oi.product_id,
p.category
from course.order_items oi
join course.products p
on oi.product_id = p.product_id 
where p.category = 'ebook';

delete from course.order_items oi
using course.products p
where oi.product_id = p.product_id 
and p.category = 'ebook';
```
## Zadanie 12
delete table usuwa wiersze, ale tabela fizycznie zostaje, natomiast drop table usuwa tabele jako obiekt
## Zadanie 13
w takim przypadku wszystkie wiersze tabeli mogłyby zostac usuniete
