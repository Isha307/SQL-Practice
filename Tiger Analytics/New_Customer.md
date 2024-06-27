## Q. Find the number of new customer each month?
```sql
CREATE TABLE sales 
(
    order_date date,
    customer VARCHAR(512),
    qty INT
);

INSERT INTO sales (order_date, customer, qty) VALUES ('2021-01-01', 'C1', '20');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-01-01', 'C2', '30');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-02-01', 'C1', '10');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-02-01', 'C3', '15');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-03-01', 'C5', '19');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-03-01', 'C4', '10');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-04-01', 'C3', '13');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-04-01', 'C5', '15');
INSERT INTO sales (order_date, customer, qty) VALUES ('2021-04-01', 'C6', '10');
```

<h4>Sales</h4>

customer | C1 | C2 | C1 | C3 | C5 | C4 | C3 | C5 | C5
--- | --- | --- | --- | --- | --- | --- | ---| --- | ---
order_date | 2021-01-01 | 2021-01-01 | 2021-02-01 | 2021-02-01 | 2021-03-01 | 2021-03-01 | 2021-04-01 | 2021-04-01 | 2021-04-01
customer | C1 | C2 | C1 | C3 | C5 | C4 | C3 | C5 | C5
qty | 20 | 30 | 10 | 15 | 19 | 10 | 13 | 15 | 10

```sql
with cte as(
    select extract(month from ORDER_DATE) as "MONTH", CUSTOMER, qty ,row_number() 
    over(partition by customer order by order_date) as rnk from sales
  )
select MONTH, count(*) as new_customer_cnt from cte where rnk =1 group by MONTH order by MONTH
```
