**Company**  
```
INSERT INTO company (CompanyID, Name, CEO) VALUES
(1, 'Rogersound', 'Joel Sallinen'),
(2, 'Dun Rite', 'Ismo Laitela'),
(3, 'Asian Fusion', 'Severi Huovinen'),
(4, 'VR', 'Kaarina Luusua');
```  

```
+-----------+--------------+-----------------+
| CompanyID | Name         | CEO             |
+-----------+--------------+-----------------+
|         1 | Rogersound   | Joel Sallinen   |
|         2 | Dun Rite     | Ismo Laitela    |
|         3 | Asian Fusion | Severi Huovinen |
|         4 | VR           | Kaarina Luusua  |
+-----------+--------------+-----------------+
```  

**TRAIN**  

```
INSERT INTO TRAIN (TrainID, Manufacturer, SeatAmount, Horsepower, Company_CompanyID) VALUES
(1, 'Robinson INC', 300, 5000, 1),
(2, 'Irving Trains', 250, 4500, 2),
(3, 'Greyvoid', 500, 7350, 4),
(4, 'La Petite Boulangerie', 550, 5600, 1),
(5, 'Robinson INC', 10, 7300, 3);
```  

```
+---------+-----------------------+------------+------------+-------------------+
| TrainID | Manufacturer          | SeatAmount | Horsepower | Company_CompanyID |
+---------+-----------------------+------------+------------+-------------------+
|       1 | Robinson INC          |        300 |       5000 |                 1 |
|       2 | Irving Trains         |        250 |       4500 |                 2 |
|       3 | Greyvoid              |        500 |       7350 |                 4 |
|       4 | La Petite Boulangerie |        550 |       5600 |                 1 |
|       5 | Robinson INC          |         10 |       7300 |                 3 |
+---------+-----------------------+------------+------------+-------------------+
```  

**MAINTENANCEREPORT**  

```
INSERT INTO maintenancereport (MaintenanceID, Date, Type, Status, Other, Train_TrainID) VALUES
(1, '2017-10-15', 'Engine', 'Good', NULL, 1),
(2, '2020-06-21', 'Bathroom', 'Faulty', "Toilets didn't work", 2),
(3, '2019-01-02', 'Brakes', 'Good', NULL, 1),
(4, '2020-12-02', 'Radio transceiver', 'Good', NULL, 3);
```  

```
+---------------+------------+-------------------+--------+---------------------+---------------+
| MaintenanceID | Date       | Type              | Status | Other               | Train_TrainID |
+---------------+------------+-------------------+--------+---------------------+---------------+
|             1 | 2017-10-15 | Engine            | Good   | NULL                |             1 |
|             2 | 2020-06-21 | Bathroom          | Faulty | Toilets didn't work |             2 |
|             3 | 2019-01-02 | Brakes            | Good   | NULL                |             1 |
|             4 | 2020-12-02 | Radio transceiver | Good   | NULL                |             3 |
+---------------+------------+-------------------+--------+---------------------+---------------+
```  
**TRIP**  

```
INSERT INTO trip (TripID, DepartingStation, ArrivalStation, EstimatedTime, TotalDistance, Train_TrainID) VALUES
(1, 'Pasila', 'Oulu', '08:25:00', 850, 1),
(2, 'Rovaniemi', 'Oulu', '01:12:00', 170, 2),
(3, 'Ylivieska', 'Kauhava', '01:35:00', 145, 1),
(4, 'Mikkeli', 'Tampere', '01:45:00', 250, 3),
(5, 'Tampere', 'Alavieska', '04:10:00', 450, 4),
(6, 'Kauhava', 'Helsinki', '06:11:00', 610, 5);
```

```
+--------+------------------+----------------+---------------+---------------+---------------+
| TripID | DepartingStation | ArrivalStation | EstimatedTime | TotalDistance | Train_TrainID |
+--------+------------------+----------------+---------------+---------------+---------------+
|      1 | Pasila           | Oulu           | 08:25:00      |           850 |             1 |
|      2 | Rovaniemi        | Oulu           | 01:12:00      |           170 |             2 |
|      3 | Ylivieska        | Kauhava        | 01:35:00      |           145 |             1 |
|      4 | Mikkeli          | Tampere        | 01:45:00      |           250 |             3 |
|      5 | Tampere          | Alavieska      | 04:10:00      |           450 |             4 |
|      6 | Kauhava          | Helsinki       | 06:11:00      |           610 |             5 |
+--------+------------------+----------------+---------------+---------------+---------------+
```  

**PERSON**  

```
INSERT INTO person (PersonID, Firstname, Lastname, Birthday, TYPE, Gender) VALUES
(1, 'Salla', 'Holappa', '1978-11-12', 'Customer', 'F'),
(2, 'Tuukka', 'Tallus', '1991-02-02', 'Customer', 'M'),
(3, 'Sanna', 'Inberg', '1949-10-05', 'Customer', 'F'),
(4, 'Tapani', 'Lindman', '1984-09-08', 'Customer', 'M'),
(5, 'Retu', 'Rantala', '1997-12-27', 'Customer', 'M'),
(6, 'Armas', 'Hanhi', '1989-01-21', 'Customer', 'M'),
(7, 'Kaari', 'Kulju', '1985-07-12', 'Staff', 'O'),
(8, 'Helvi', 'Tukio', '1984-03-28', 'Staff', 'F'),
(9, 'Petteri', 'Ketola', '1992-08-15', 'Staff', 'M');
```  

```
+----------+-----------+----------+------------+----------+--------+
| PersonID | Firstname | Lastname | Birthday   | TYPE     | Gender |
+----------+-----------+----------+------------+----------+--------+
|        1 | Salla     | Holappa  | 1978-11-12 | Customer | F      |
|        2 | Tuukka    | Tallus   | 1991-02-02 | Customer | M      |
|        3 | Sanna     | Inberg   | 1949-10-05 | Customer | F      |
|        4 | Tapani    | Lindman  | 1984-09-08 | Customer | M      |
|        5 | Retu      | Rantala  | 1997-12-27 | Customer | M      |
|        6 | Armas     | Hanhi    | 1989-01-21 | Customer | M      |
|        7 | Kaari     | Kulju    | 1985-07-12 | Staff    | O      |
|        8 | Helvi     | Tukio    | 1984-03-28 | Staff    | F      |
|        9 | Petteri   | Ketola   | 1992-08-15 | Staff    | M      |
+----------+-----------+----------+------------+----------+--------+
```  

**RECEIPT**  

```
INSERT INTO receipt (ReceiptID, Seat, Price, Person_PersonID) VALUES
(1, '1-23', 40, 1),
(2, '6-45', 23, 1),
(3, '4-101', 15, 2),
(4, '2-44', 33, 3),
(5, '8-12', 60, 4),
(6, '3-01', 28, 5);
```

```
+-----------+-------+-------+-----------------+
| ReceiptID | Seat  | Price | Person_PersonID |
+-----------+-------+-------+-----------------+
|         1 | 1-23  |    40 |               1 |
|         2 | 6-45  |    23 |               1 |
|         3 | 4-101 |    15 |               2 |
|         4 | 2-44  |    33 |               3 |
|         5 | 8-12  |    60 |               4 |
|         6 | 3-01  |    28 |               5 |
+-----------+-------+-------+-----------------+
```  

**FREIGHT**  

```
INSERT INTO freight (FreightID, Category, Type, Amount, TotalWeight, Trip_TripID) VALUES
(1, 'Bulk', 'Timber', 500, 35000, 1),
(2, 'Containerized', 'Heavy machinery', 50, 55000, 2),
(3, 'Liquid bulk', 'Petroleum', 10, 25000, 5),
(4, 'Bulk', 'Steel', 350, 15000, 3),
(5, 'Containerized', 'Electronics', 25, 60000, 5);
```  

```
+-----------+---------------+-----------------+--------+-------------+-------------+
| FreightID | Category      | Type            | Amount | TotalWeight | Trip_TripID |
+-----------+---------------+-----------------+--------+-------------+-------------+
|         1 | Bulk          | Timber          |    500 |       35000 |           1 |
|         2 | Containerized | Heavy machinery |     50 |       55000 |           2 |
|         3 | Liquid bulk   | Petroleum       |     10 |       25000 |           5 |
|         4 | Bulk          | Steel           |    350 |       15000 |           3 |
|         5 | Containerized | Electronics     |     25 |       60000 |           5 |
+-----------+---------------+-----------------+--------+-------------+-------------+
```  

**TRIP_HAS_RECEIPT**  

```
INSERT INTO trip_has_receipt (Trip_TripID, Receipt_ReceiptID) VALUES
(1, 3),
(1, 1),
(2, 4),
(3, 2),
(4, 6);
```

```
+-------------+-------------------+
| Trip_TripID | Receipt_ReceiptID |
+-------------+-------------------+
|           1 |                 1 |
|           1 |                 3 |
|           2 |                 4 |
|           3 |                 2 |
|           4 |                 6 |
+-------------+-------------------+
```  

**STAFF**  

```
INSERT INTO staff (Person_PersonID, Trip_TripID, Rank, Salary) VALUES
(7, 1, 'Conductor', 3500),
(8, 2, 'Chef', 2750),
(7, 3, 'Conductor', 3500),
(7, 4, 'Conductor', 3500),
(8, 5, 'Chef', 2750),
(9, 6, 'Train master', 6500);
```  

```
+-----------------+-------------+--------------+--------+
| Person_PersonID | Trip_TripID | Rank         | Salary |
+-----------------+-------------+--------------+--------+
|               7 |           1 | Conductor    |   3500 |
|               7 |           3 | Conductor    |   3500 |
|               7 |           4 | Conductor    |   3500 |
|               8 |           2 | Chef         |   2750 |
|               8 |           5 | Chef         |   2750 |
|               9 |           6 | Train master |   6500 |
+-----------------+-------------+--------------+--------+
```  

