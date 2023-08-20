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
IF(expression, first, second)
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
