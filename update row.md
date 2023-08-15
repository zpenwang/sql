update single row
```sql
use sql_invoicing;
update invoices
set payment_total = 10, payment_date = "2019-01-01"
where invoice_id = 1
```
update muliple rows
```sql
use sql_invoicing;
update invoices
set payment_total = invoice_total * 0.5, payment_date = due_date
where client_id in (3,4) -- optional
```
