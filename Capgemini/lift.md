## Q. Final list of passengers allowed to enter the lift based on the maximum capacity of the lift.

```sql
Create table lifts(
 id int,
 capacity_kg   int
);

insert into lifts values (1, 300);
insert into lifts values (2, 350);

create table lift_passengers(  
    passenger_name varchar(50),
    weight_kg int,
    lift_id	 int
);


insert into lift_passengers values ('Rahul', 85, 1);
insert into lift_passengers values ('Adarsh', 73, 1);
insert into lift_passengers values ('Riti', 95, 1);
insert into lift_passengers values ('Dheeraj', 80, 1);
insert into lift_passengers values ('Vimal', 83, 2);
insert into lift_passengers values ('Neha', 77, 2);
insert into lift_passengers values ('Priti', 73, 2);
insert into lift_passengers values ('Himanshi', 85, 2);
```
<h4>SQL</h4>

```sql
with cte as (select l.PASSENGER_NAME, l.WEIGHT_KG, sum(WEIGHT_KG) 
over(partition by l.lift_id  ORDER BY l.PASSENGER_NAME rows between unbounded preceding and current row)
as cur_wt_on_lift, l2.id, l2.CAPACITY_KG
    from lift_passengers l join lifts l2 on l.LIFT_ID = l2.id),
cte2 as(select id, PASSENGER_NAME from cte where CAPACITY_KG >= CUR_WT_ON_LIFT)
select id, listagg(PASSENGER_NAME, ',') as PASSENGER_NAME from cte2 group by id
```
