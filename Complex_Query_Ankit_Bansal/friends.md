## Q. Write a Query to find out person_id, name, number of friends, sum of marks, a person who have friend with total marks grater than 0. 

```sql
Create table friend (
 pid int,
 fid int
);

insert into friend (pid , fid ) values ('1','2');
insert into friend (pid , fid ) values ('1','3');
insert into friend (pid , fid ) values ('2','1');
insert into friend (pid , fid ) values ('2','3');
insert into friend (pid , fid ) values ('3','5');
insert into friend (pid , fid ) values ('4','2');
insert into friend (pid , fid ) values ('4','3');
insert into friend (pid , fid ) values ('4','5');

create table person (
  PersonID int,
  Name varchar(50),
  Score int
);
insert into person(PersonID,Name ,Score) values('1','Alice','88');
insert into person(PersonID,Name ,Score) values('2','Bob','11');
insert into person(PersonID,Name ,Score) values('3','Devis','27');
insert into person(PersonID,Name ,Score) values('4','Tara','45');
insert into person(PersonID,Name ,Score) values('5','John','63');
```

<h4>SQL</h4>

```sql
SELECT p1.PERSONID, p1.NAME, SUM(p2.SCORE) as total_score_of_frnd, count(f.pid) as no_of_frnd
FROM person p1 
JOIN friend f ON p1.PERSONID = f.PID 
JOIN person p2 ON f.FID = p2.PERSONID 
GROUP BY p1.PERSONID, p1.NAME having SUM(p2.SCORE) > 100
ORDER BY p1.PERSONID;
```
