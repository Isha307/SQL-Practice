## Write a SQL query to return all employee whose salary is same in same department.

```sql
CREATE TABLE emp_salary(
    emp_id INTEGER  NOT NULL,
    name VARCHAR(20)  NOT NULL,
    salary VARCHAR(30),
    dept_id INTEGER
);

INSERT INTO emp_salary VALUES (101, 'sohan', '3000', '11');
INSERT INTO emp_salary VALUES (102, 'rohan', '4000', '12');
INSERT INTO emp_salary VALUES (103, 'mohan', '5000', '13');
INSERT INTO emp_salary VALUES (104, 'cat', '3000', '11');
INSERT INTO emp_salary VALUES (105, 'suresh', '4000', '12');
INSERT INTO emp_salary VALUES (109, 'mahesh', '7000', '12');
INSERT INTO emp_salary VALUES (108, 'kamal', '8000', '11');
```
<h4>SQL</h4>

```sql
with cte as (
select EMP_ID, NAME, SALARY, DEPT_ID,
rank() over(partition by dept_id order by SALARY) as rnk 
from emp_salary
)
select c1.EMP_ID, c1.NAME, c1.SALARY, c1.DEPT_ID 
from cte c1 join cte c2 on c1.DEPT_ID = c2.DEPT_ID and c1.rnk = c2.rnk and c1.EMP_ID <> c2.EMP_ID
order by c1.DEPT_ID, c1.EMP_ID

```
