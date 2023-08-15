insert single row
```sql
use sql_store;
insert into customers
values(
    DEFAULT,
    "John",
    "Smith",
    "1990-01-01",
    DEFAULT,
    "address",
    "city",
    "CA",
    DEFAULT)
```

```sql
use sql_store;
insert into customers(
    first_name,
    last_name,
    birth_date,
    address,
    city,
    state)
values(
	"John",
    "Smith",
    "1990-01-01",
    "address",
    "city",
    "CA")
```
action output 会显示 xx row(s) affected, 最后的变动呈现要从原表点开查看

insert multiple rows
```sql
use sql_store;
insert into products(name,quantity_in_stock,unit_price)
values ("product 1", 10, 1.95),
       ("product 2", 11, 1.95),
       ("product 3", 12, 1.95)
```
