### Left/Right join
Return all customers whether they have any orders or not
```sql
use sql_store;
SELECT *
FROM customers c
LEFT JOIN orders o 
 ON c.customer_id = o.customer_id
```
