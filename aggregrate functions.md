```sql
use sql_invoicing;
select 
    max(invoice_total) as highest,
    min(invoice_total) as lowest,
    avg(invoice_total) as average,
    sum(invoice_total * 1.1) as total, -- 函数括号内可以用expression
    count(*) as total_records,  -- count the number of all records, with duplicate
    count(DISTINCT client_id) as total_records  -- count without duplicate
from invoices
where invoice_date > "2019-07-01"
```
```sql
use sql_invoicing;
select 
   "First half of 2019" as date_range, -- table中没有的column但是又需要加上去的
   sum(invoice_total) as total_sales,
   sum(payment_total) as total_payments,
   sum(invoice_total-payment_total) as what_we_expect
from invoices i
where i.invoice_date between "2019-01-01" and "2019-07-01"
union
select 
   "Second half of 2019" as date_range,
   sum(invoice_total) as total_sales,
   sum(payment_total) as total_payments,
   sum(invoice_total-payment_total) as what_we_expect
from invoices i
where i.invoice_date between "2019-07-01" and "2019-12-31"
union
select 
   "Total" as date_range,
   sum(invoice_total) as total_sales,
   sum(payment_total) as total_payments,
   sum(invoice_total-payment_total) as what_we_expect
from invoices i
where i.invoice_date between "2019-01-01" and "2019-12-31"

```
