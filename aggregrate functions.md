```sql
use sql_invoicing;
select 
    max(invoice_total) as highest,
    min(invoice_total) as lowest,
    avg(invoice_total) as average,
    sum(invoice_total * 1.1) as total,
    count(*) as total_records,  -- count the number of all records, with duplicate
    count(DISTINCT client_id) as total_records  -- count without duplicate
from invoices
where invoice_date > "2019-07-01"
```
