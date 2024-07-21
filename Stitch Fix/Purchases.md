## Repeat Purchases on Multiple Days

```sql
create table purchases(
	user_id integer,
	product_id integer,
	quantity integer,
	purchase_date timestamp
);

INSERT INTO purchases VALUES (536, 3223, 6, TO_TIMESTAMP('2022-01-11 12:33:44', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO purchases VALUES (827, 3585, 35, TO_TIMESTAMP('2022-01-20 14:05:26', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO purchases VALUES (536, 3223, 5, TO_TIMESTAMP('2022-03-02 09:33:28', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO purchases VALUES (536, 1435, 10, TO_TIMESTAMP('2022-03-02 08:40:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO purchases VALUES (827, 2452, 45, TO_TIMESTAMP('2022-04-09 00:00:00', 'YYYY-MM-DD HH24:MI:SS'));
```

<h4>SQL</h4>

```sql
with cte as (
select USER_ID,PRODUCT_ID, count(*) over(partition by TRUNC(purchase_date)) as cnt from purchases
)
select DISTINCT USER_ID from cte where cnt > 1;
```
