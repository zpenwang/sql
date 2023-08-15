### Left/Right join
Return all customers whether they have any orders or not
```sql
use sql_store;
SELECT *
FROM customers c
LEFT JOIN orders o 
 ON c.customer_id = o.customer_id
-- USING (customer_id)
```







composite keys
```sql
use sql_store;
SELECT *
from order_items oi
join order_item_notes oin
    on oi.order_id = oin.order_id and oin.product_id = oin.product_id
--  USING (product_id, order_id)
```
