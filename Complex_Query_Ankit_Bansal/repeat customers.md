## find new and repeat customers.

```sql
create table customer_orders (
  order_id integer,
  customer_id integer,
  order_date date,
  order_amount integer
);

INSERT INTO customer_orders VALUES (1, 100, TO_DATE('2022-01-01', 'YYYY-MM-DD'), 2000);
INSERT INTO customer_orders  VALUES (2, 200, TO_DATE('2022-01-01', 'YYYY-MM-DD'), 2500);
INSERT INTO customer_orders VALUES (3, 300, TO_DATE('2022-01-01', 'YYYY-MM-DD'), 2100);
INSERT INTO customer_orders VALUES (4, 100, TO_DATE('2022-01-02', 'YYYY-MM-DD'), 2000);
INSERT INTO customer_orders VALUES (5, 400, TO_DATE('2022-01-02', 'YYYY-MM-DD'), 2200);
INSERT INTO customer_orders VALUES (6, 500, TO_DATE('2022-01-02', 'YYYY-MM-DD'), 2700);
INSERT INTO customer_orders VALUES (7, 100, TO_DATE('2022-01-03', 'YYYY-MM-DD'), 3000);
INSERT INTO customer_orders VALUES (8, 400, TO_DATE('2022-01-03', 'YYYY-MM-DD'), 1000);
INSERT INTO customer_orders VALUES (9, 600, TO_DATE('2022-01-03', 'YYYY-MM-DD'), 3000);
```
<h4>SQL</h4>

```sql
with cte as
(select customer_orders.*, rank() over(partition by CUSTOMER_ID order by ORDER_DATE) as rnk from customer_orders),
cte1 as
(select ORDER_DATE, count(CUSTOMER_ID) as new_customer from cte where rnk = 1 group by ORDER_DATE ),
cte2 as
(select ORDER_DATE, count(CUSTOMER_ID) as repeat_customer from cte where rnk > 1 group by ORDER_DATE )
select c1.ORDER_DATE, coalesce(c1.new_customer,0) as new_customer, coalesce(c2.repeat_customer,0) as repeat_customer
from cte1 c1 full join cte2 c2 on c1.ORDER_DATE = c2.ORDER_DATE order by ORDER_DATE
```
