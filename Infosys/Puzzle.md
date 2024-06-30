## Q. Solve the Puzzle
```sql
create table input (
id int,
formula varchar(10),
value int
);

insert into input values (1,'1+4',10),(2,'2+1',5),(3,'3-2',40),(4,'4-1',20);
```


<h4>Input</h4>

 ID| formula| value 
--- | --- | ---
 1|'1+4'|10
 2|'2+1'|5
 3|'3-2'|40
 4|'4-1'|20

<h4>SQL</h4>

```sql
with cte as (select input.*, SUBSTR(formula, 1, 1) AS first_input, SUBSTR(formula,3,1) as sec_input, SUBSTR(formula,2,1) as op
FROM input)
select i1.*, case when c.op='+' then i1.value + i2.value 
                when c.op='-' then i1.value - i2.value
                when c.op='*' then i1.value * i2.value
                else i1.value/i2.value end as new_value 
from cte c left join input i1 on c.FIRST_INPUT = i1.id left join input i2 on c.SEC_INPUT = i2.id order by c.id
```

<h4>OUTPUT</h4>

ID| FORMULA|	VALUE|	NEW_VALUE
--- | --- | --- | ---
1|	1+4|	10|	30
2|	2+1|	5|	15
3|	3-2|	40|	35
4|	4-1|	20|	10
