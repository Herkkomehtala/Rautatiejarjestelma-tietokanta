# SQL kyselyt

* **Hae tietyn yhtiön kaikki junat.** (Rogersound)  
```
SELECT train.TrainID, train.Manufacturer, train.SeatAmount, train.Horsepower FROM train
INNER JOIN  company ON train.Company_CompanyID = company.CompanyID
WHERE company.Name = 'Rogersound';
```  
![sql_query1](uploads/497aed09e43b189a006e4a03b17668c1/sql_query1.PNG)  

* **Hae tietyn henkilön kaikki liput.** (Salla Holappa)  

```
SELECT p.PersonID, p.Firstname, p.Lastname, r.Seat, r.Price FROM person p
INNER JOIN receipt r ON p.PersonID = r.Person_PersonID
WHERE p.Firstname = 'Salla' AND p.Lastname = 'Holappa';
``` 

![sql_query2](uploads/05fcc6379395863c646e6cf8cd42316d/sql_query2.PNG)  

* **Hae tietyn junan kaikki huoltoraportit.** (Juna ID 1)  

```
SELECT train.TrainID, Date, Type, Status, Other FROM maintenancereport
INNER JOIN train ON train.TrainID = Train_TrainID
WHERE train.TrainID = '1';
```  
![sql_query3](uploads/5c3b034c1f1e076220626cf0962077f5/sql_query3.PNG)  

* **Hae tietyn junan kaikki huoltoraportit tietyltä aikaväliltä.** (Juna ID 1, aikaväli 2018-02-01 ja 2021-02-28)  

```
SELECT train.TrainID, m.Date, m.Type, m.Status, m.Other FROM maintenancereport m
INNER JOIN train ON train.TrainID = m.Train_TrainID
WHERE train.TrainID = 1 AND (m.Date BETWEEN CAST('2018-02-01' AS DATE) AND CAST('2021-02-28' AS DATE));
```  

![sql_query4](uploads/c6a62129a7fe5b07bc6b731f85591184/sql_query4.PNG)  

* **Hae tietyn junan matkatunnit ja niiden keskiarvo.** (Juna ID 1)  

```
SELECT train.TrainID, SEC_TO_TIME(AVG(TIME_TO_SEC(trip.EstimatedTime))) AS AverageTripHours, SEC_TO_TIME(SUM(TIME_TO_SEC(trip.EstimatedTime))) AS TotalTripHours FROM trip
INNER JOIN train ON train.TrainID = trip.Train_TrainID
WHERE train.TrainID = 1;
```  

![sql_query5](uploads/ab288161c400361cdd43c964df815256/sql_query5.PNG)  

* **Hae tietyn matkan kaikki matkustajat** (Matka ID 1)  

```
SELECT p.Firstname, p.Lastname, p.TYPE, r.Seat, r.Price FROM trip
INNER JOIN trip_has_receipt tr ON tr.Trip_TripID = TripID
INNER JOIN Receipt r ON r.ReceiptID = tr.Receipt_ReceiptID
INNER JOIN Person p ON p.PersonID = r.Person_PersonID
WHERE TripID = 1;
```  

![sql_query6](uploads/ca049bfc18d88ced65570460b8c5b2bd/sql_query6.PNG)  

* **Hae tietyn matkan kaikki henkilökunta** (Matka ID 1)  

```
SELECT p.Firstname, p.Lastname, p.TYPE, s.Rank, s.Salary FROM trip
INNER JOIN staff s ON s.Trip_TripID = TripID
INNER JOIN person p ON p.PersonID = s.Person_PersonID
WHERE TripID = 1;
```  
![sql_query7](uploads/3540ccac386a5187a864e14909178d95/sql_query7.PNG)  

* **Hae tietyn henkilökuntajäsenen työtunnit** (Kaari Kulju)  

```
SELECT p.Firstname, p.Lastname, SEC_TO_TIME(SUM(TIME_TO_SEC(EstimatedTime))) as TotalHours  FROM trip
INNER JOIN staff s ON s.Trip_TripID = TripID
INNER JOIN person p ON p.PersonID = s.Person_PersonID
WHERE p.Firstname = 'Kaari' AND p.Lastname = 'Kulju';
```  
![sql_query10](uploads/c7f04a79d918ba16d2b967c0b6ffbc3d/sql_query10.PNG)  

* **Hae tietyn matkan rahtitavarat** (Matka ID 5)  

```
SELECT tr.TrainID, f.Category, f.Type, f.Amount, f.TotalWeight FROM trip
INNER JOIN freight f ON f.Trip_TripID = TripID
INNER JOIN train tr ON tr.TrainID = Train_TrainID
WHERE f.Trip_TripID = 5;
```  

![sql_query8](uploads/4a6623de91df0bbb0ae23580763b2690/sql_query8.PNG)  

* **Hae tietyn junan kaikkien kuljetettujen rahtitavaroiden paino ja niiden keskiarvo** (Juna ID 4)  

```
SELECT tr.TrainID, AVG(f.TotalWeight) AS AVG_Weight, SUM(f.TotalWeight) AS SUM_TotalWeight FROM trip
INNER JOIN freight f ON f.Trip_TripID = TripID
INNER JOIN train tr ON tr.TrainID = Train_TrainID
WHERE tr.TrainID = 4;
```  

![sql_query9](uploads/dff56c0d92495b231af92a418e5ffd66/sql_query9.PNG)  

* **Hae tietylle asemalle tullut rahtitavara, yhtiö ja sen juna joka toimitti kyseisen rahtitavaran.** (Oulu)  

```
SELECT c.Name AS Delivering_Company,tr.TrainID, f.Category, f.Type, f.Amount, f.TotalWeight FROM trip
INNER JOIN freight f ON f.Trip_TripID = TripID
INNER JOIN train tr ON tr.TrainID = Train_TrainID
INNER JOIN company c ON c.CompanyID = tr.Company_CompanyID
WHERE ArrivalStation = 'Oulu';
```

![sql_query11](uploads/aa561e8dba12ea429caca4baa10377c6/sql_query11.PNG)  
HUOM! Jos haluaa tietää mitä rahtia on lähtenyt joltakin asemalta, pitää vain vaihtaa 'ArrivalStation' 'DepartingStation'.