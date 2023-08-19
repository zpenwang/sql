可以类比为 内层函数-外层函数
遍历的意味
### subrequery returns a single value
找出比id = 3产品价格还要高的产品
```sql
use sql_store;
select *
from products
where unit_price > (
    select unit_price
    from products
    where product_id = 3
)
```
找出工资大于平均数的employee
```sql
use sql_hr;
select *
from employees 
where salary > (
    select avg(salary)
    from employees e
 )
```
### subrequery returns a list
Find products that have never been ordered
```sql
use sql_store;
select *
from products
where product_id not in (
    select distinct product_id
    from order_items
 )
```
Find customers who have ordered lettuce (id = 3)
```sql
select *
from customers c
where customer_id in (
    select o.customer_id
    from order_items oi
    join orders o using(order_id)
    where product_id = 3
)
```
```sql
use sql_store;
select distinct customer_id, first_name, last_name
from customers c
join orders o using(customer_id)
join order_items oi using(order_id)
where oi.product_id = 3
```
