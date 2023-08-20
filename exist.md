select clients that have an invoice
```sql
use sql_invoicing;
select *
from clients c
where exists (
	 select client_id
	 from invoices
	 where client_id = c.client_id
)
```
execute the external query only if the inner query exists
exists 对外表用 loop 逐条查询，每次查询都会查看 exists 的条件语句。\
当 exists 里的条件语句能够返回记录行时（无论返回多少记录行，只要能返回），条件就为真，返回当前 loop 到的这条记录。\
IN用法的替代
