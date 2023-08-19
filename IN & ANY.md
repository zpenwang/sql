select clients with at least 2 invoices
```sql
select * 
from invoices
where client_id in (
	select client_id
	from invoices
    group by client_id
    having count(*) >= 2
)
```
```sql
select * 
from invoices
where client_id = any (
	select client_id
	from invoices
    group by client_id
    having count(*) >= 2
)
```
