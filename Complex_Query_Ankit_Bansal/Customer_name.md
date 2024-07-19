## Find First Name , Middle Name and Last Name of a Customer.

```sql
create table customers (
  customer_name varchar(30)
);
insert into customers values ('Ankit Bansal');
insert into customers values ('Vishal Pratap Singh');
insert into customers values ('Michael'); 
```

<h4>SQL</h4>

```sql
--select * from customers
with cte as (SELECT customers.*,LENGTH(CUSTOMER_NAME), LENGTH(CUSTOMER_NAME) - LENGTH(replace(CUSTOMER_NAME, ' ','')) as no_of_space, 
instr(CUSTOMER_NAME, ' ') as first_space, instr(CUSTOMER_NAME, ' ' ,instr(CUSTOMER_NAME, ' ')+1) as second_space
FROM customers)
SELECT cte.*, 
    case when NO_OF_SPACE>0 then SUBSTR(CUSTOMER_NAME, 1, first_space-1)
         else CUSTOMER_NAME end AS first_name,
    case when NO_OF_SPACE>1 then SUBSTR(CUSTOMER_NAME, first_space+1, length(CUSTOMER_NAME) - SECOND_SPACE+1)
         else NULL end AS second_name,
    case when NO_OF_SPACE = 0 then NULL
         when NO_OF_SPACE=1 then SUBSTR(CUSTOMER_NAME, first_space+1, length(CUSTOMER_NAME) - first_space)
         when NO_OF_SPACE=2 then SUBSTR(CUSTOMER_NAME, SECOND_SPACE+1, length(CUSTOMER_NAME) - SECOND_SPACE)
         else NULL end AS last_name
FROM cte;
```
