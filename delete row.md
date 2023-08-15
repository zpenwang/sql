```sql
use sql_invoicing;
delete from invoices
where client_id = (
select client_id
from clients
where name = "Myworks"
```
