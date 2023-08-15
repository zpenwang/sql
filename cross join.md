```sql
use sql_store;
select c.first_name as customer,
       p.name as product
-- explicit syntax
from customers c
cross join products p
-- implicit syntax
-- from customers c, products p 
order by c.first_name
```
