combine results from multiple queries
```sql
use sql_store;
select order_id,order_date,"Active" as "status"
from orders
where order_date >= "2019-01-01"
union
select order_id,order_date,"archived" as "status"
from orders
where order_date < "2019-01-01"
```
single test expression: IF(expression, first, second)
```sql
use sql_store;
select 
	order_id,
    order_date,
    if(
     year(order_date) = year(now()),
     "active",
     "archived") as category
from  orders 
```
multiple test expression: CASE
```sql
use sql_store;
select
	order_id,
    case 
        when year(order_date) = year(now()) then "archive"
        when year(order_date) = year(now()) - 1 then "last year"
        when year(order_date) < year(now()) - 1 then "archived"
        else "future"
	end as category
from  orders
```
