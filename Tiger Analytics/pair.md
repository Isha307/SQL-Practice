## Q. Pair the adult and child together, last adult will go alone.

```sql
create table family (
person varchar(5),
type varchar(10),
age int
);

INSERT INTO family (person, type, age) VALUES ('A1', 'Adult', 54);
INSERT INTO family (person, type, age) VALUES ('A2', 'Adult', 53);
INSERT INTO family (person, type, age) VALUES ('A3', 'Adult', 52);
INSERT INTO family (person, type, age) VALUES ('A4', 'Adult', 58);
INSERT INTO family (person, type, age) VALUES ('A5', 'Adult', 54);
INSERT INTO family (person, type, age) VALUES ('C1', 'Child', 20);
INSERT INTO family (person, type, age) VALUES ('C2', 'Child', 19);
INSERT INTO family (person, type, age) VALUES ('C3', 'Child', 22);
INSERT INTO family (person, type, age) VALUES ('C4', 'Child', 15);

```

<h4>SQL</h4>

```sql
with cte1 as
(select PERSON, TYPE, AGE, row_number() over(partition by type order by PERSON) as rnk
from family where TYPE = 'Adult'),
cte2 as
(select PERSON, TYPE, AGE, row_number() over(partition by type order by PERSON) as rnk
from family where TYPE = 'Child')
select cte1.PERSON, cte2.PERSON from cte1 left JOIN cte2 on cte1.rnk = cte2.rnk
```
