## Q. Write a SQL query so that every team plays with another team, but no match should repeat.

```sql
create table team(
team_name varchar(20)
);

insert into team VALUES('Ind');
insert into team VALUES('AUS');
insert into team VALUES('PAK');
insert into team VALUES('SA');
insert into team VALUES('SL');
```

<h4>SQL</h4>

```sql
select t1.TEAM_NAME as team1, t2.TEAM_NAME as team2 from team t1 cross join team t2
where t1.TEAM_NAME < t2.TEAM_NAME
```
