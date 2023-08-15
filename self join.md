### self join
```sql
use sql_hr;
select
    e.employee_id,
    e.first_name,
    m.first_name AS manager
from employees e
join employees m
    ON e.reports_to = m.employee_id
```

### self outer join
self join won't return the record of the manager, while self outer join
```sql
use sql_hr;
select
    e.employee_id,
    e.first_name,
    m.first_name AS manager
from employees e
left join employees m
    ON e.reports_to = m.employee_id
```
