### 2 exchangeable statements:
subquery returns a single value
```sql
use sql_invoicing;
select *
from invoices 
where invoice_total > (
	select max(invoice_total)
	from invoices
	where client_id = 3  -- this statmetn returns a value
)
```

subquery returns a list of value
```sql
use sql_invoicing;
select *
from invoices 
where invoice_total > all(
	select invoice_total
	from invoices
	where client_id = 3   
)
```

how ALL statement works?:
  - For each row, it will compare the invoice_total value with the values in the subquery statement (one returning list of value), \
    if invoice_total greater than ALL these values, that row will be returned in the final result set. 
