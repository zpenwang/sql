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
```sql
use sql_invoicing;
SELECT p.date, 
       p.payment_method,
       sum(amount) AS payment_total
       -- amount AS payment_total 会报错，是因为启用了only_full_group_by模式，参数会使得GROUP BY的检查更加严格:
       -- 1. SELECT列表中的任何非聚合列,必须在GROUP BY子句中出现。
       -- 2. 如果SELECT列表中的非聚合列不在GROUP BY从句中出现,那么GROUP BY子句中的列能够唯一确定这个未出现的非聚合列的值
       -- 3. 不允许在GROUP BY列上面没有的SELECT列上进行查询。
FROM payments p 
JOIN payment_methods pm ON p.payment_method = pm.payment_method_id
LEFT JOIN invoices i ON p.date = i.payment_date
GROUP BY p.date, p.payment_method
ORDER BY p.date
```
