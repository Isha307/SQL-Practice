## Q. Find nth occurrence of sunday in future from given day.

```sql
DECLARE @today_date DATE;
DECLARE @n NUMBER;
SET today_date = TO_DATE('09/07/2024', 'DD/MM/YYYY');
SET n = 3;
   
select dateadd(week, @n-1,dateadd(day, 8-datepart(weekday, @today_date), @today_date));
```
