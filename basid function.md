truncate(5.7432, 2)
ceiling(5.7)
floor(5.2)
abs(5.2)
rand()
https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html
length("sky")
upper("sky")
lower("sky")
ltrim("      sky")
rtrip("sky       ")
trim("  sky     ")
left ("kingdergarden", 4)
right("kingdergarden", 6)
substring("kindergarden", 3, 5)     nderg
locate(n, "kindergaren")      3
locate(garden, "kindergaren")      7
replace("kindergarten", "garten", "garden")      kindergarden
concat("first", "last")
```sql
use sql_store;
select concat(first_name, " ", last_name) as full_name
from customers
```
https://dev.mysql.com/doc/refman/8.0/en/string-functions.html
now()
curdate()
curtime()
year(now()), month(now()), minute(now()), dayname(now()), monthname(now()),
extract(day from now())   extract(year from now())

date_format(now(),"%m %d %y")
time_format(now(), "%h:%i %p") 12小时制
time_format(now(), "%H:%i %p") 24小时制
https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html


date_add（now(), interval 1 day）
date_sub（now(), interval 1 day）
datediff("2019-01-05", "2019-01-01")  前面的时间剪去后面的时间
time_to_sec("09:00") - time_to_sec("09:02")
