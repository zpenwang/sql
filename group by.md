single table
```sql
use sql_invoicing;
select client_id,
	   sum(invoice_total) as total_sales
from invoices
where invoice_date > "2019-07-01"
group by client_id
order by total_sales desc
```
across multiple tables
```sql
select state,
       city,
       sum(invoice_total) as total_sales
from invoices
join clients using(client_id)
group by state, city
```
