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

### self outer join
To get every employee in the table whether they have a manager or not
```sql
use sql_hr;
select
    e.employee_id,
    e.first_name,
    m.first_name AS manager
from employees e
left join employees m
    ON e.reports_to = m.employee_id
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
