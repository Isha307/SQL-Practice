## Q. Find the email activity rank for each user. Email activity rank is defined by the total number of emails sent.

```sql
CREATE TABLE from_user (
    id INT,
    from_user VARCHAR(255),
    to_user VARCHAR(255),
    day INT
);

INSERT INTO from_user (id, from_user, to_user, day) VALUES (0, '6edf0be4b2267df1fa', '75d295377a46f83236', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (1, '6edf0be4b2267df1fa', '32ded68d89443e808', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (2, '6edf0be4b2267df1fa', '55e60cfcc9dc49c17e', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (3, '6edf0be4b2267df1fa', 'e0e0defbb9ec47f6f7', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (4, '6edf0be4b2267df1fa', '47be2887786891367e', 1);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (5, '6edf0be4b2267df1fa', '2813e59cf6c1ff698e', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (6, '6edf0be4b2267df1fa', 'a84065b7933ad01019', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (7, '6edf0be4b2267df1fa', '850badf89ed8f06854', 1);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (8, '6edf0be4b2267df1fa', '6b503743a13d778200', 1);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (9, '6edf0be4b2267df1fa', 'd63386c884aeb9f71d', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (10, '6edf0be4b2267df1fa', '5b8754928306a18b68', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (11, '6edf0be4b2267df1fa', '6edf0be4b2267df1fa', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (12, '6edf0be4b2267df1fa', '406539987dd9b679c0', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (13, '6edf0be4b2267df1fa', '114bafadff2d882864', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (14, '6edf0be4b2267df1fa', '157e3e9278e32aba3e', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (15, '75d295377a46f83236', '75d295377a46f83236', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (16, '75d295377a46f83236', 'd63386c884aeb9f71d', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (17, '75d295377a46f83236', '55e60cfcc9dc49c17e', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (18, '75d295377a46f83236', '47be2887786891367e', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (19, '75d295377a46f83236', '5b8754928306a18b68', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (20, '75d295377a46f83236', '850badf89ed8f06854', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (21, '75d295377a46f83236', '5eff3a5bfc0687351e', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (22, '75d295377a46f83236', '5dc768b2f067c56f77', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (23, '75d295377a46f83236', '114bafadff2d882864', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (24, '75d295377a46f83236', 'e0e0defbb9ec47f6f7', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (25, '75d295377a46f83236', '7cfe354d9a64bf8173', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (26, '5dc768b2f067c56f77', '114bafadff2d882864', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (27, '5dc768b2f067c56f77', '2813e59cf6c1ff698e', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (28, '5dc768b2f067c56f77', '91f59516cb9dee1e88', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (29, '5dc768b2f067c56f77', '5b8754928306a18b68', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (30, '5dc768b2f067c56f77', '6b503743a13d778200', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (31, '5dc768b2f067c56f77', 'aa0bd72b729fab6e9e', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (32, '5dc768b2f067c56f77', '850badf89ed8f06854', 1);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (33, '5dc768b2f067c56f77', '406539987dd9b679c0', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (34, '5dc768b2f067c56f77', '75d295377a46f83236', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (35, '5dc768b2f067c56f77', 'd63386c884aeb9f71d', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (36, '5dc768b2f067c56f77', 'ef5fe98c6b9f313075', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (37, '32ded68d89443e808', '55e60cfcc9dc49c17e', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (38, '32ded68d89443e808', 'e0e0defbb9ec47f6f7', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (39, '32ded68d89443e808', '850badf89ed8f06854', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (40, '32ded68d89443e808', '5eff3a5bfc0687351e', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (41, '32ded68d89443e808', '8bba390b53976da0cd', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (42, '32ded68d89443e808', '91f59516cb9dee1e88', 1);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (43, '32ded68d89443e808', '6edf0be4b2267df1fa', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (44, '32ded68d89443e808', 'd63386c884aeb9f71d', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (45, '32ded68d89443e808', '32ded68d89443e808', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (46, '32ded68d89443e808', '5dc768b2f067c56f77', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (47, '32ded68d89443e808', '406539987dd9b679c0', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (48, '32ded68d89443e808', 'a84065b7933ad01019', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (49, '32ded68d89443e808', '2813e59cf6c1ff698e', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (50, '32ded68d89443e808', 'cbc4bd40cd1687754', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (51, '32ded68d89443e808', 'aa0bd72b729fab6e9e', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (52, '32ded68d89443e808', '75d295377a46f83236', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (53, '32ded68d89443e808', '6b503743a13d778200', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (54, '32ded68d89443e808', '5b8754928306a18b68', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (55, '32ded68d89443e808', '47be2887786891367e', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (56, 'e0e0defbb9ec47f6f7', '5dc768b2f067c56f77', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (57, 'e0e0defbb9ec47f6f7', '2813e59cf6c1ff698e', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (58, 'e0e0defbb9ec47f6f7', '6b503743a13d778200', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (59, 'e0e0defbb9ec47f6f7', 'e22d2eabc2d4c19688', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (60, 'e0e0defbb9ec47f6f7', 'e6088004caf0c8cc51', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (61, 'e0e0defbb9ec47f6f7', 'aa0bd72b729fab6e9e', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (62, 'e0e0defbb9ec47f6f7', '55e60cfcc9dc49c17e', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (63, 'e0e0defbb9ec47f6f7', '850badf89ed8f06854', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (64, 'e0e0defbb9ec47f6f7', 'd63386c884aeb9f71d', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (65, 'e0e0defbb9ec47f6f7', 'a84065b7933ad01019', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (66, 'e0e0defbb9ec47f6f7', '32ded68d89443e808', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (67, 'e0e0defbb9ec47f6f7', '47be2887786891367e', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (68, 'e0e0defbb9ec47f6f7', '157e3e9278e32aba3e', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (69, 'e0e0defbb9ec47f6f7', 'cbc4bd40cd1687754', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (70, 'e0e0defbb9ec47f6f7', 'e0e0defbb9ec47f6f7', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (71, '6b503743a13d778200', '850badf89ed8f06854', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (72, '6b503743a13d778200', '55e60cfcc9dc49c17e', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (73, '6b503743a13d778200', 'cbc4bd40cd1687754', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (74, '6b503743a13d778200', 'e0e0defbb9ec47f6f7', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (75, '6b503743a13d778200', '7cfe354d9a64bf8173', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (76, '6b503743a13d778200', '32ded68d89443e808', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (77, '6b503743a13d778200', 'e6088004caf0c8cc51', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (78, '6b503743a13d778200', 'aa0bd72b729fab6e9e', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (79, '6b503743a13d778200', '5dc768b2f067c56f77', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (80, 'e22d2eabc2d4c19688', '8bba390b53976da0cd', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (81, 'e22d2eabc2d4c19688', 'e0e0defbb9ec47f6f7', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (82, 'e22d2eabc2d4c19688', 'ef5fe98c6b9f313075', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (83, 'e22d2eabc2d4c19688', '5eff3a5bfc0687351e', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (84, 'e22d2eabc2d4c19688', '47be2887786891367e', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (85, 'e22d2eabc2d4c19688', '406539987dd9b679c0', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (86, 'e22d2eabc2d4c19688', 'cbc4bd40cd1687754', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (87, 'e22d2eabc2d4c19688', '7cfe354d9a64bf8173', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (88, 'e22d2eabc2d4c19688', 'e6088004caf0c8cc51', 5);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (89, 'e22d2eabc2d4c19688', 'aa0bd72b729fab6e9e', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (90, 'e22d2eabc2d4c19688', '6edf0be4b2267df1fa', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (91, 'e22d2eabc2d4c19688', '157e3e9278e32aba3e', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (92, 'e22d2eabc2d4c19688', 'd63386c884aeb9f71d', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (93, 'd63386c884aeb9f71d', 'cbc4bd40cd1687754', 6);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (94, 'd63386c884aeb9f71d', '8bba390b53976da0cd', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (95, 'd63386c884aeb9f71d', '75d295377a46f83236', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (96, 'd63386c884aeb9f71d', '5b8754928306a18b68', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (97, 'd63386c884aeb9f71d', 'e6088004caf0c8cc51', 7);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (98, 'd63386c884aeb9f71d', 'e22d2eabc2d4c19688', 9);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (99, 'd63386c884aeb9f71d', '55e60cfcc9dc49c17e', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (100, 'd63386c884aeb9f71d', '5dc768b2f067c56f77', 3);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (101, 'd63386c884aeb9f71d', '32ded68d89443e808', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (102, 'd63386c884aeb9f71d', '157e3e9278e32aba3e', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (103, 'cbc4bd40cd1687754', '7cfe354d9a64bf8173', 10);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (104, 'cbc4bd40cd1687754', '114bafadff2d882864', 2);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (105, 'cbc4bd40cd1687754', '157e3e9278e32aba3e', 4);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (106, 'cbc4bd40cd1687754', 'e6088004caf0c8cc51', 1);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (107, 'cbc4bd40cd1687754', '5eff3a5bfc0687351e', 8);
INSERT INTO from_user (id, from_user, to_user, day) VALUES (108, 'cbc4bd40cd1687754', '5b8754928306a18b68', 5);
```

<h4>SQL</h4>

```sql
select from_user, count(from_user) as total_emails, row_number() 
over(order by count(from_user) desc)
from google_gmail_emails group by from_user
order by count(from_user) desc, from_user
```
