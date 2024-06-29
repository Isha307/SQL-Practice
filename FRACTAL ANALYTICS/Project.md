## Q. Find the total assignments for each project, ensuring projects with no assignments display 0?
```sql
-- Create the Project table
CREATE TABLE Project (
    ID INT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL
);

INSERT INTO Project (ID, Name) VALUES (1, 'Project A');
INSERT INTO Project (ID, Name) VALUES (2, 'Project B');
INSERT INTO Project (ID, Name) VALUES (3, 'Project C');
INSERT INTO Project (ID, Name) VALUES (4, 'Project D');

-- Create the Assignment table
CREATE TABLE Assignment (
    ProjectID INT,
    EmployeeID INT
);

INSERT INTO Assignment(ProjectID, EmployeeID) VALUES (1, 101);
INSERT INTO Assignment(ProjectID, EmployeeID) VALUES (1, 102);
INSERT INTO Assignment(ProjectID, EmployeeID) VALUES (2, 103);
INSERT INTO Assignment(ProjectID, EmployeeID) VALUES (3, 104);
INSERT INTO Assignment(ProjectID, EmployeeID) VALUES (3, 105);

-- Create the Employee table
CREATE TABLE Employee (
    ID INT,
    Name VARCHAR(255)
);

INSERT INTO Employee(ID, Name) VALUES (101, 'Aarav');
INSERT INTO Employee(ID, Name) VALUES (102, 'Mayur');
INSERT INTO Employee(ID, Name) VALUES (103, 'Shrikant');
INSERT INTO Employee(ID, Name) VALUES (104, 'Sanika');
INSERT INTO Employee(ID, Name) VALUES (105, 'Saurabh');

```


<h4>Project</h4>

 ID| Name|
--- | ---
 1|Project A
 2|Project B
 3|Project C
 4|Project D


<h4> Assignment </h4>

ProjectID|EmployeeID
--- | ---
 1| 101
 1| 102
 2| 103
 3| 104
 3| 105
 
<h4>Employee</h4>

ID| Name
--- | ---
101| Aarav
102| Mayur
103|Shrikant
104| Sanika
105| Saurabh

<h4>SQL</h4>

```sql
select p.name, count(a.PROJECTID) as Total_number from project p left join assignment a on p.id = a.PROJECTID 
left join employee e on a.EMPLOYEEID = e.ID
group by p.name order by p.name
```

<h4>OUTPUT</h4>

Name| TOTAL_NUMBER
--- | ---
Project A |	2
Project B |	1
Project C	| 2
Project D	| 0
