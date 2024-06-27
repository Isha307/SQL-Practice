## Q. Find origin and destination for each cid?
```sql
CREATE TABLE flights 
(
    cid VARCHAR(512),
    fid VARCHAR(512),
    origin VARCHAR(512),
    Destination VARCHAR(512)
);

INSERT INTO flights (cid, fid, origin, Destination) VALUES ('1', 'f1', 'Del', 'Hyd');
INSERT INTO flights (cid, fid, origin, Destination) VALUES ('1', 'f2', 'Hyd', 'Blr');
INSERT INTO flights (cid, fid, origin, Destination) VALUES ('2', 'f3', 'Mum', 'Agra');
INSERT INTO flights (cid, fid, origin, Destination) VALUES ('2', 'f4', 'Agra', 'Kol');
```

<h4>Flights</h4>

cid | 1 | 1 | 2 | 2 
--- | --- | --- | --- | ---
  fid | f1 | f2 | f3 | f4 
origin | Del | Hyd | Hyd | Blr
Destination | Mum | Agra | Agra | Kol

```sql
SELECT f1.cid, f1.origin, f2.destination from flights f1 join flights f2
on f1.cid = f2.cid where f1.destination = f2.origin order by f1.cid
```
