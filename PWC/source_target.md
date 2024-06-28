## Q. Find the new source and target?
```sql
create table source(id int, name varchar(5))
create table target(id int, name varchar(5))
insert into source values(1,'A'),(2,'B'),(3,'C'),(4,'D')
insert into target values(1,'A'),(2,'B'),(4,'X'),(5,'F');
```

<h4>Source</h4>

id | 1 | 2 | 3 | 4
--- | --- | --- | --- | --- 
name | A | B | C | D

<h4>Target</h4>

id | 1 | 2 | 4 | 5
--- | --- | --- | --- | --- 
name | A | B | X | F


```sql
select coalesce(s.id,t.id) as id,case
    when s.id is null then 'New in Source'
    when t.id is null then 'New in Target'
    else 'Mismatch' end as "Comment"
from target t full outer join source s on t.id = s.id
where s.name <> t.name or s.name is null or t.name is null
```
<h4>OUTPUT TABLE</h4>

id  | 3           | 4      | 5
--- | --- | --- | --- | 
comment|  New in Target | Mismatch | New in Source

