## Write the SQL query to find the total number of people present inside the hospital.

```sql
CREATE TABLE hospital (
 emp_id INT,
 action VARCHAR(10),
 time DATE
);

INSERT INTO hospital (emp_id, action, time) VALUES (1, 'in', TO_DATE('2019-12-22 09:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (1, 'out', TO_DATE('2019-12-22 09:15:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (2, 'in', TO_DATE('2019-12-22 09:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (2, 'out', TO_DATE('2019-12-22 09:15:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (2, 'in', TO_DATE('2019-12-22 09:30:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (3, 'out', TO_DATE('2019-12-22 09:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (3, 'in', TO_DATE('2019-12-22 09:15:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (3, 'out', TO_DATE('2019-12-22 09:30:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (3, 'in', TO_DATE('2019-12-22 09:45:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (4, 'in', TO_DATE('2019-12-22 09:45:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO hospital (emp_id, action, time) VALUES (5, 'out', TO_DATE('2019-12-22 09:40:00', 'YYYY-MM-DD HH24:MI:SS'));
SELECT * FROM hospital;
```

<h4>SQL</h4>

```sql
WITH cte AS (
SELECT emp_id,
SUM(CASE WHEN action = 'in' THEN 1 ELSE 0 END) AS in_count,
SUM(CASE WHEN action = 'out' THEN 1 ELSE 0 END) AS out_count
FROM hospital
GROUP BY emp_id
)
SELECT COUNT(emp_id) AS total_present
FROM cte
WHERE in_count > out_count;
```
