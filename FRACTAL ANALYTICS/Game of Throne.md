## Q. For each region find house which has won maximum no of battles. display region, house and no of wins?
```sql
Create the 'king' table
CREATE TABLE king (
    k_no INT PRIMARY KEY,
    king VARCHAR(50),
    house VARCHAR(50)
);

-- Create the 'battle' table
CREATE TABLE battle (
    battle_number INT PRIMARY KEY,
    name VARCHAR(100),
    attacker_king INT,
    defender_king INT,
    attacker_outcome INT,
    region VARCHAR(50),
    FOREIGN KEY (attacker_king) REFERENCES king(k_no),
    FOREIGN KEY (defender_king) REFERENCES king(k_no)
);

delete from king;
INSERT INTO king (k_no, king, house) VALUES
(1, 'Robb Stark', 'House Stark'),
(2, 'Joffrey Baratheon', 'House Lannister'),
(3, 'Stannis Baratheon', 'House Baratheon'),
(4, 'Balon Greyjoy', 'House Greyjoy'),
(5, 'Mace Tyrell', 'House Tyrell'),
(6, 'Doran Martell', 'House Martell');

delete from battle;
-- Insert data into the 'battle' table
INSERT INTO battle (battle_number, name, attacker_king, defender_king, attacker_outcome, region) VALUES
(1, 'Battle of Oxcross', 1, 2, 1, 'The North'),
(2, 'Battle of Blackwater', 3, 4, 0, 'The North'),
(3, 'Battle of the Fords', 1, 5, 1, 'The Reach'),
(4, 'Battle of the Green Fork', 2, 6, 0, 'The Reach'),
(5, 'Battle of the Ruby Ford', 1, 3, 1, 'The Riverlands'),
(6, 'Battle of the Golden Tooth', 2, 1, 0, 'The North'),
(7, 'Battle of Riverrun', 3, 4, 1, 'The Riverlands'),
(8, 'Battle of Riverrun', 1, 3, 0, 'The Riverlands');
```


<h4>KING</h4>

K_NO | 1 | 2 | 3 | 4 | 5 | 6 
--- | --- | --- | --- |--- |--- |--- 
King | Robb Stark | Joffrey Baratheon | Stannis Baratheon | Balon Greyjoy | Mace Tyrell | Doran Martell 
House | House Stark | House Lannister | House Baratheon | House Greyjoy | House Tyrell | House Martell

<h4> BATTLE </h4>

K_NO | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8
--- | --- | --- | --- |--- |--- |--- |--- |--- 
NAME | Battle of Oxcross | Battle of Blackwater | Battle of the Fords | Battle of the Green Fork | Battle of the Ruby Ford | Battle of the Golden Tooth	 | Battle of Riverrun | Battle of Riverrun 
ATTACKER_KING | 1 | 3 | 1 | 2 | 1 | 2 | 3 | 1
DEFENDER_KING | 2 | 4 | 5 | 6 | 3 | 1 | 4 | 3 
ATTACKER_OUTCOME | 1 | 0 | 1 | 0 | 1 | 0 | 1 | 0
REGION | The North | The North | The Reach | The Reach | The Riverlands | The North | The Riverlands | The Riverlands

<h4>SQL</h4>

```sql
with cte as (select BATTLE_NUMBER, NAME, CASE when ATTACKER_OUTCOME = 1 then ATTACKER_KING
                            else DEFENDER_KING end as winner, REGION from BATTLE b ),
 cte2 as(select  REGION, HOUSE, count(WINNER) as no_of_wins, rank() over(partition by region order by count(WINNER) DESC) as rnk 
from  KING k join cte c on k.K_NO = c.WINNER group by HOUSE,REGION order by REGION )
select REGION, HOUSE, no_of_wins from cte2 where rnk=1
```

<h4>OUTPUT</h4>
<p align="center">
  <img src = "https://github.com/Isha307/SQL-Practice/blob/main/01.png">
</p>
