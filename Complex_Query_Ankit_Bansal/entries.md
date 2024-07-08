## Scenario based Interviews Question for Product companies

```sql
create table entries ( 
name varchar(20),
address varchar(20),
email varchar(20),
floor int,
resources varchar(10));

INSERT INTO entries VALUES ('A', 'Bangalore', 'A@gmail.com', 1, 'CPU');
INSERT INTO entries VALUES ('A', 'Bangalore', 'A1@gmail.com', 1, 'CPU');
INSERT INTO entries VALUES ('A', 'Bangalore', 'A2@gmail.com', 2, 'DESKTOP');
INSERT INTO entries VALUES ('B', 'Bangalore', 'B@gmail.com', 2, 'DESKTOP');
INSERT INTO entries VALUES ('B', 'Bangalore', 'B1@gmail.com', 2, 'DESKTOP');
INSERT INTO entries VALUES ('B', 'Bangalore', 'B2@gmail.com', 1, 'MONITOR');
```

<h4>SQL</h4>

```sql
with cte as(
SELECT NAME, count(name) as total_visits, listagg(distinct RESOURCES, ',') as resources_used 
FROM entries group by name),
cte2 as (
SELECT NAME, FLOOR, count(FLOOR) as no_of_visits, rank() over(partition by NAME order by count(1) desc) as rnk
FROM entries group by name, FLOOR
)
select c1.NAME, total_visits, c2.FLOOR as most_visited_floor, resources_used
FROM cte c1 join cte2 c2 on c1.NAME = c2.NAME where rnk =1;
```
