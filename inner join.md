single key, single join condition
```sql
SELECT *
FROM customers c
JOIN orders o 
 ON c.customer_id = o.customer_id
-- USING (customer_id)
```

composite keys, compound join conditions
```sql
```sql
use sql_store;
SELECT *
from order_items oi
join order_item_notes oin
    on oi.order_id = oin.order_id and oin.product_id = oin.product_id
--  USING (product_id, order_id)
```

joining across multiple databases
```sql
use sql_store;
select *
from order_items oi
join sql_inventory.products p
    on oi.product_id = p.product_id
```
