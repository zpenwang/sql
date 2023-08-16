```sql
use sql_invoicing;
select client_id,
	   sum(invoice_total) as total_sales,
       count(*) as number_of_invoices
from invoices
-- where total_sales > 500 and number_of_invoices > 5
-- at this point we haven't grouped the data, so by then we don't know the total sales of each client
group by client_id
HAVING total_sales > 500 and number_of_invoices > 5
```
```sql
use sql_store;
select c.customer_id,
       c.first_name,
       c.last_name,
       sum(oi.quantity * oi.unit_price) as total_sales
from customers c
join orders o using(customer_id)
join order_items oi using(order_id)
where state = "VA" 
group by c.customer_id
having total_sales > 100
```
优先级： where > group by > having
### where clasue  vs  having clause
1. where clause: filter data before group \
having clause: filter data after group
2. HAVING中用到的column必须是select从句中的


