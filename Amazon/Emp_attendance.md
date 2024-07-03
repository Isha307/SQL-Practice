## Q. Generate a report to showcase the presence and absence of each employee.

```sql
create table emp_attendance(
	employee varchar(10),
	dates date,
	status varchar(20)
);

insert into emp_attendance values('A1', to_date('2024-01-01','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A1', to_date('2024-01-02','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A1', to_date('2024-01-03','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A1', to_date('2024-01-04','yyyy-mm-dd'), 'ABSENT');
insert into emp_attendance values('A1', to_date('2024-01-05','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A1', to_date('2024-01-06','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A1', to_date('2024-01-07','yyyy-mm-dd'), 'ABSENT');
insert into emp_attendance values('A1', to_date('2024-01-08','yyyy-mm-dd'), 'ABSENT');
insert into emp_attendance values('A1', to_date('2024-01-09','yyyy-mm-dd'), 'ABSENT');
insert into emp_attendance values('A1', to_date('2024-01-010','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A2', to_date('2024-01-06','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A2', to_date('2024-01-07','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A2', to_date('2024-01-08','yyyy-mm-dd'), 'ABSENT');
insert into emp_attendance values('A2', to_date('2024-01-09','yyyy-mm-dd'), 'PRESENT');
insert into emp_attendance values('A2', to_date('2024-01-10','yyyy-mm-dd'), 'ABSENT');
```

<h4>SQL</h4>

```sql
WITH cte1 AS (
    SELECT 
        employee, dates, 
        dates - ROW_NUMBER() OVER (PARTITION BY employee, status ORDER BY dates) AS date_grp, 
        status
    FROM  emp_attendance
)
SELECT 
    employee, MIN(dates) AS from_date, MAX(dates) AS to_date, status
FROM cte1
GROUP BY employee,  date_grp, status
ORDER BY employee, from_date;

```
