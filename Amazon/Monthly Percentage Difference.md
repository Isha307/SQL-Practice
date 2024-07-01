## Q. Given a table of purchases by date, calculate the month-over-month percentage change in revenue. 
```sql
CREATE TABLE sf_transaction (
    id INT PRIMARY KEY,
    created_at DATETIME,
    value INT,
    purchase_id INT
);


INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (1, '2019-01-01', 172692, 43);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (2, '2019-01-05', 177194, 36);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (3, '2019-01-09', 109513, 30);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (4, '2019-01-13', 164911, 30);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (5, '2019-01-17', 198872, 39);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (6, '2019-01-21', 184853, 31);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (7, '2019-01-25', 186817, 26);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (8, '2019-01-29', 137784, 22);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (9, '2019-02-02', 140032, 25);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (10, '2019-02-06', 116948, 43);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (11, '2019-02-10', 162515, 25);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (12, '2019-02-14', 114256, 12);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (13, '2019-02-18', 197465, 48);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (14, '2019-02-22', 120741, 20);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (15, '2019-02-26', 100074, 49);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (16, '2019-03-02', 157548, 19);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (17, '2019-03-06', 105506, 16);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (18, '2019-03-10', 189351, 46);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (19, '2019-03-14', 191231, 29);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (20, '2019-03-18', 120575, 44);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (21, '2019-03-22', 151688, 47);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (22, '2019-03-26', 102327, 18);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (23, '2019-03-30', 156147, 25);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (24, '2019-04-03', 192530, 36);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (25, '2019-04-07', 154765, 42);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (26, '2019-04-11', 113336, 12);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (27, '2019-04-15', 129073, 50);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (28, '2019-04-19', 123477, 21);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (29, '2019-04-23', 182142, 31);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (30, '2019-04-27', 116546, 39);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (31, '2019-05-01', 174748, 26);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (32, '2019-05-05', 155693, 42);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (33, '2019-05-09', 103012, 25);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (34, '2019-05-13', 187960, 33);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (35, '2019-05-17', 101202, 18);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (36, '2019-05-21', 112522, 10);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (37, '2019-05-25', 195969, 37);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (38, '2019-05-29', 117284, 40);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (39, '2019-06-02', 112956, 36);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (40, '2019-06-06', 174157, 29);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (41, '2019-06-10', 125975, 45);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (42, '2019-06-14', 110340, 29);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (43, '2019-06-18', 143066, 31);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (44, '2019-06-22', 153270, 11);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (45, '2019-06-26', 139635, 29);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (46, '2019-06-30', 157071, 35);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (47, '2019-07-04', 166552, 18);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (48, '2019-07-08', 197587, 34);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (49, '2019-07-12', 103958, 37);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (50, '2019-07-16', 111305, 28);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (51, '2019-07-20', 190266, 39);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (52, '2019-07-24', 116060, 44);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (53, '2019-07-28', 163802, 48);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (54, '2019-08-01', 188558, 21);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (55, '2019-08-05', 166528, 49);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (56, '2019-08-09', 141463, 28);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (57, '2019-08-13', 120110, 34);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (58, '2019-08-17', 159368, 12);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (59, '2019-08-21', 184900, 46);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (60, '2019-08-25', 190372, 38);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (61, '2019-08-29', 195877, 15);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (62, '2019-09-02', 143221, 21);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (63, '2019-09-06', 160413, 41);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (64, '2019-09-10', 183919, 43);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (65, '2019-09-14', 134535, 34);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (66, '2019-09-18', 188646, 31);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (67, '2019-09-22', 122706, 27);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (68, '2019-09-26', 160016, 21);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (69, '2019-09-30', 186777, 21);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (70, '2019-10-04', 165442, 50);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (71, '2019-10-08', 172445, 43);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (72, '2019-10-12', 167910, 21);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (73, '2019-10-16', 116646, 35);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (74, '2019-10-20', 163287, 15);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (75, '2019-10-24', 187293, 43);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (76, '2019-10-28', 144823, 11);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (77, '2019-11-01', 118317, 10);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (78, '2019-11-05', 166105, 38);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (79, '2019-11-09', 121128, 11);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (80, '2019-11-13', 177355, 38);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (81, '2019-11-17', 176442, 50);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (82, '2019-11-21', 129837, 10);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (83, '2019-11-25', 122363, 38);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (84, '2019-11-29', 125469, 10);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (85, '2019-12-03', 109657, 20);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (86, '2019-12-07', 108782, 35);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (87, '2019-12-11', 149235, 18);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (88, '2019-12-15', 187243, 36);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (89, '2019-12-19', 152538, 20);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (90, '2019-12-23', 178861, 34);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (91, '2019-12-27', 122675, 30);
INSERT INTO sf_transaction (id, created_at, value, purchase_id) VALUES (92, '2019-12-31', 104037, 18);
```
<h4>SQL</h4>

```sql
with cte as (select date_format( created_at,'%Y-%m') as month, sum(value) as tot_revenue
from sf_transactions group by date_format( created_at,'%Y-%m')),
cte2 as (select month, tot_revenue, lag(tot_revenue,1,0) over(order by month) as prev_month_revenue from cte)
select month as ym, Round((tot_revenue - prev_month_revenue)*100/prev_month_revenue,2) as revenue_diff_pct
from cte2
```
