可以类比为 内层函数-外层函数
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
