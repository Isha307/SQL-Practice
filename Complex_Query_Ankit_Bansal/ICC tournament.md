## Derive Points table for ICC tournament

```sql
create table icc_world_cup
(
Team_1 Varchar(20),
Team_2 Varchar(20),
Winner Varchar(20)
);
INSERT INTO icc_world_cup values('India','SL','India');
INSERT INTO icc_world_cup values('SL','Aus','Aus');
INSERT INTO icc_world_cup values('SA','Eng','Eng');
INSERT INTO icc_world_cup values('Eng','NZ','NZ');
INSERT INTO icc_world_cup values('Aus','India','India');

select * from icc_world_cup;
```

<h4>SQL</h4>

```sql
with cte as(
select TEAM_1, case when team_1=winner then 1 else 0 end as winner from icc_world_cup
union all
select TEAM_2, case when team_2=winner then 1 else 0 end as winner from icc_world_cup
)
select TEAM_1, count(TEAM_1) as match_played, sum(WINNER) as no_of_wins,
count(TEAM_1) - sum(WINNER) as no_of_lost
from cte group by TEAM_1
```
