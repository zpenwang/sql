copy all data from one table to another
```sql
use sql_store;
create table orders_archived AS
select * from orders  -- subquery
```
copy part of data from one table to another
```sql
use sql_store;
insert into orders_archived

-- 下面的一串select语句作为subquery
select *
from orders
where order_date < "2019-01-01"
```
