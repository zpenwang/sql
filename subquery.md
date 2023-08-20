可以类比为 内层函数-外层函数
in where statement
### subquery returns a single value
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
### correlated subquery
get invoices that are larger than the client's average invoice amount
```sql
use sql_hr;
select *
from employees e
where salary > (
   select avg(salary)
   from employees e
   where office_id = e.office_id
)
```
correlated subquery的执行流程：
1. 从外层查询取一行记录 
2. 将记录字段值传入内层子查询进行计算 
3. 返回计算结果与外层查询进行比较 
4. 取外层查询下一行,重复步骤2-3 
    
non-correlated subquery的执行流程：
1. 首先执行子查询,计算平均价格 
2. 存储子查询的结果 
3. 对外层查询的每一行,读取子查询结果比较price字段 
4. 返回比较结果
   
综上， correlated/ non-correlated subquery 都是一种遍历的机制
https://www.cnblogs.com/heenhui2016/p/10574695.html

in select statement
