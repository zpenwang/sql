insert single row \
action output 会显示 xx row(s) affected, 最后的变动呈现要从原表点开查看
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

insert multiple rows
```sql
use sql_store;
insert into products(name,quantity_in_stock,unit_price)
values ("product 1", 10, 1.95),
       ("product 2", 11, 1.95),
       ("product 3", 12, 1.95)
```
inserting hierarchy rows \
order 1 ------- product 1 \
order 1 ------- product 2 \
order 2 ------- product 5 \
order 2 ------- product 9 \
order 2 ------- product 12
 ```sql
use sql_store;
INSERT INTO orders (customer_id, order_date, status)
values(1, "2019-01-02", 1);

INSERT INTO order_items
VALUES
    (LAST_INSERT_ID(), 1, 1, 2.95),  -- LAST_INSERT_ID() returns the ID number when inserting a new row,这里返回的是新插入order的序号
    (LAST_INSERT_ID(), 2, 1, 3.95)
```
