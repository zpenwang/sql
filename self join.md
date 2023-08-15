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
self join cannnot return the record of the manager, while self outer join can get every employee in the table whether they have a manager or not
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
