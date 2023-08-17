可以类比为 内层函数-外层函数
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
Find the products that have never been ordered
```sql
use sql_store;
select *
from products
where product_id not in (
    select distinct product_id
    from order_items
 )
```
