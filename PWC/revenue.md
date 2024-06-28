## Q. Find the company whose revenue is increasing every year?
```sql
create table company_revenue 
(
company varchar(100),
year int,
revenue int
);

INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC1', 2000, 100);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC1', 2001, 110);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC1', 2002, 120);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC2', 2000, 100);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC2', 2001, 90);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC2', 2002, 120);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC3', 2000, 500);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC3', 2001, 400);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC3', 2002, 600);
INSERT INTO company_revenue (company, year, revenue) VALUES ('ABC3', 2003, 800);

```

<h4>Company Revenue</h4>

 Company | ABC1 | ABC1 | ABC1 | ABC2 | ABC2 | ABC2 | ABC3 | ABC3 | ABC3 | ABC3 
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- 
 Year | 2000 | 2001 | 2002 | 2000 | 2001 | 2002 | 2000 | 2001 | 2002 | 2003 
 Revenue | 100  | 110  | 120  | 100  | 90   | 120  | 500  | 400  | 600  | 800  


```sql
with cte as (select COMPANY, YEAR, REVENUE - lag(revenue,1,0) over(partition by company order by "YEAR") as profit
from company_revenue)
select DISTINCT COMPANY from company_revenue where COMPANY not in (select COMPANY from cte where profit<0)
```

<h4>OUTPUT</h4>

Company |
--- |
ABC1 |
