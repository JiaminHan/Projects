Q1
Code:
SELECT * FROM Customers
WHERE Country='UK';

Result:
Number of Records: 7
CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country
4	Around the Horn	Thomas Hardy	120 Hanover Sq.	London	WA1 1DP	UK
11	B's Beverages	Victoria Ashworth	Fauntleroy Circus	London	EC2 5NT	UK
16	Consolidated Holdings	Elizabeth Brown	Berkeley Gardens 12 Brewery	London	WX1 6LT	UK
19	Eastern Connection	Ann Devon	35 King George	London	WX3 6FW	UK
38	Island Trading	Helen Bennett	Garden House Crowther Way	Cowes	PO31 7PJ	UK
53	North/South	Simon Crowther	South House 300 Queensbridge	London	SW7 1RZ	UK
72	Seven Seas Imports	Hari Kumar	90 Wadhurst Rd.	London	OX15 4NB	UK
Q2:What is the name of the customer who has the most orders?
Code:
SELECT Customers.CustomerName, Count(OrderID) as number FROM Orders
LEFT JOIN Customers ON Orders.CustomerID=Customers.CustomerID
GROUP BY CustomerName
ORDER BY number DESC;

Result:
Ernst HandelQ3: Which supplier has the highest average product price?
Code:
SELECT SupplierName,  AVG(Products.Price) FROM Suppliers
inner Join Products on Products.SupplierID=Suppliers.SupplierID
GROUP BY SupplierName
ORDER BY AVG(Price) DESC;

Result:
Aux joyeux ecclésiastiquesQ4: How many different countries are all the customers from? (Hint: consider DISTINCT.)
Code
SELECT COUNT(DISTINCT(Country)) FROM [Customers];

Result:
21Q5: What category appears in the most orders?
Code
SELECT CategoryName, COUNT(orderID) FROM Categories
JOIN Products on Categories.CategoryID=Products.CategoryID
JOIN OrderDetails on Products.ProductID=OrderDetails.ProductID
GROUP BY Categories.CategoryID
ORDER BY COUNT(orderID) DESC;

or
Select Count (*), CategoryID, CategoryName FROM (Select OrderDetails.ProductID, OrderDetails.OrderID, Products.*, Categories.* FROM [OrderDetails]
Join Products on Products.ProductID=OrderDetails.ProductID
Join Categories on Categories.CategoryID=Products.CategoryID
Group By OrderID, Products.CategoryID)
GROUP BY CategoryID

Result:
Dairy ProductsQ6: What was the total cost for each order?
Code:
SELECT Orders.OrderID, SUM(Quantity*Price) as TotalCost FROM Orders
JOIN OrderDetails on OrderDetails.OrderID=Orders.OrderID
JOIN Products on Products.ProductID=OrderDetails.ProductID
GROUP BY Orders.OrderID;

Result:
OrderID	TotalCost
10248	566
10249	2329.25
10250	2267.25
10251	839.5
10252	4662.5
10253	1806
10254	781.5
10255	3115.75
10256	648
10257	1400.5
10258	2529.75
10259	126
10260	2183.9
10261	560
10262	782.2
10263	3086.4
10264	906.25
10265	1470
10266	456
10267	5040
10268	1377.1000000000001
10269	846
10270	1720
10271	60
10272	1821.1999999999998
10273	2679.5
10274	673.5999999999999
10275	384
10276	525
10277	1503.6
10278	1862.4
10279	585
10280	766.5
10281	108.2
10282	194.34
10283	1770
10284	1816.95
10285	2726.8
10286	3772
10287	1158
10288	112
10289	599.25
10290	2713.8500000000004
10291	692.8
10292	1620
10293	1061
10294	2359.5
10295	152
10296	1315.5
10297	1776
10298	3909.5
10299	438
10300	760
10301	944
10302	3388.8
10303	1555
10304	1193
10305	5197.25
10306	624.15
10307	530.5
10308	111
10309	2202.5
10310	421
10311	336
10312	2019.9
10313	228
10314	2910
10315	646
10316	3547.5
10317	360
10318	301
10319	1490.4
10320	645
10321	180
10322	140
10323	205.5
10324	7698.45
10325	1873.25
10326	1227.5
10327	2828.65
10328	1462
10329	6025.12
10330	2431.5
10331	111.75
10332	2792
10333	1192.5
10334	181
10335	3181.5
10336	396
10337	3087.52
10338	1168.35
10339	4330.4
10340	3205.8
10341	515
10342	2876
10343	1982.5
10344	3570
10345	3662
10346	2164
10347	1160.1
10348	495
10349	178.8
10350	891.75
10351	7103.599999999999
10352	194
10353	13427
10354	711.1600000000001
10355	600
10356	1383
10357	1701.68
10358	565
10359	4572.2
10360	9244.250000000002
10361	2842
10362	1938.8
10363	559
10364	1187.5
10365	504
10366	170.25
10367	1044.85
10368	2294.05
10369	3159.8
10370	1467.5
10371	114
10372	15353.6
10373	2135
10374	573.75
10375	423.25
10376	525
10377	1272
10378	129
10379	1200.6
10380	1776.02
10381	140
10382	3628.76
10383	1123.75
10384	2778
10385	1080
10386	207.5
10387	1323.6
10388	1594.5
10389	2292
10390	2845.2
10391	108
10392	1800
10393	4135.6
10394	553
10395	2920
10396	2380.8
10397	1054
10398	3420
10399	2207
10400	3829.59
10401	4837.02
10402	3393.5
10403	1258.95
10404	2096.9
10405	500
10406	2527
10407	1492.5
10408	2030.2
10409	399
10410	1002.5
10411	1514.25
10412	465
10413	2656
10414	290.6
10415	128
10416	902
10417	14104
10418	2268.5
10419	2760
10420	2372
10421	1595.6999999999998
10422	62.46
10423	1275
10424	14366.5
10425	600
10426	422.75
10427	813.75
10428	240
10429	2186.5
10430	7245
10431	3155
10432	610.3
10433	1064
10434	450
10435	790
10436	2763.5
10437	491.99999999999994
10438	710.5
10439	1348.7
10440	7246.01
10441	2195
10442	2246
10443	673.2Q7 Which employee made the most sales (by total price)?

Code:
SELECT Employees.EmployeeID, LastName, FirstName, SUM(Price*Quantity) AS Total FROM [Employees]
JOIN Orders ON Orders.EmployeeID=Employees.EmployeeID
JOIN OrderDetails ON OrderDetails.OrderID=Orders.OrderID
JOIN Products ON Products.ProductID=OrderDetails.ProductID
GROUP BY Employees.EmployeeID 
ORDER BY Total DESC;

Result:
Margaret PeacockQ8 Which employees have BS degrees? (Hint: look at the LIKE operator.)
Code:
SELECT * FROM [Employees]
WHERE Notes LIKE '%BS%';

Result: 
Leverling, Janet
Buchanan, StevenQ9: Which supplier of three or more products has the highest average product price? (Hint: look at the HAVING operator.)
Code:
SELECT SupplierName,AVG(Price) FROM [Products]
JOIN Suppliers ON Suppliers.SupplierID=Products.SupplierID
GROUP BY Suppliers.SupplierID
HAVING COUNT(Suppliers.SupplierID) > 2
ORDER BY AVG(Price) DESC;

Result:
Tokyo Traders
# Part III


```python
import pandas as pd
```


```python
import sqlite3
conn=sqlite3.connect('database.sqlite')
c = conn.cursor()
```


```python
#Q1:Which team scored the most points when playing at home?
c.execute('SELECT home_team_api_id, home_team_goal,team_long_name FROM match JOIN Team ON team_api_id=home_team_api_id ORDER BY home_team_goal DESC LIMIT 1 ')
q1=c.fetchall()
print(q1)
```

    [(8640, 10, 'PSV')]



```python
#Q2: Did this team also score the most points when playing away?
c.execute('SELECT away_team_api_id, away_team_goal,team_long_name FROM match JOIN Team ON team_api_id=away_team_api_id ORDER BY away_team_goal DESC LIMIT 1')
q2=c.fetchall()
print(q2)
    
```

    [(9847, 9, 'Paris Saint-Germain')]



```python
#Q3: How many matches resulted in a tie?
c.execute('SELECT COUNT(match_api_id) FROM match WHERE home_team_goal=away_team_goal')
q3=c.fetchall()
print(q3)
```

    [(6596,)]



```python
#Q4: How many players have Smith for their last name? How many have 'smith' anywhere in their name?
c.execute('SELECT COUNT(player_name) FROM Player WHERE player_name LIKE "% Smith" ')
q41=c.fetchall()
print(q41)
```

    [(15,)]



```python
c.execute('SELECT COUNT(player_name) FROM Player WHERE player_name LIKE "%smith%" ')
q42=c.fetchall()
print(q42)
```

    [(18,)]



```python
#Q5 What was the median tie score? Use the value determined in the previous question for the number of tie games.
#Hint: PostgreSQL does not have a median function. Instead, think about the steps required to calculate a median 
#and use the WITH command to store stepwise results as a table and then operate on these results.
c.execute(
'SELECT AVG(home_team_goal) FROM (SELECT home_team_goal FROM match WHERE home_team_goal=away_team_goal ORDER BY home_team_goal LIMIT 2 OFFSET (SELECT (COUNT(home_team_goal) - 1) / 2 FROM match WHERE home_team_goal=away_team_goal))')
q5=c.fetchall()
q5
```




    [(1.0,)]




```python
#Q6 What percentage of players prefer their left or right foot? Hint: Calculate either the right or left foot, whichever is easier based on how you setup the problem.
c.execute("SELECT COUNT(DISTINCT(player_fifa_api_id)) FROM Player_Attributes WHERE preferred_foot=='left'" )
q61=c.fetchall()
q61
```




    [(3202,)]




```python
c.execute('SELECT COUNT(DISTINCT(player_fifa_api_id)) FROM Player_Attributes')
q62=c.fetchall()
percentage=q61[0][0]/q62[0][0]*100
percentage
```




    28.945941059482916



# PART IV

Q1:Using the same tennis data, find the number of matches played by each player in each tournament. (Remember that a player can be present as both player1 or player2).
SELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      us_men_2013) UNION ALL
	  (SELECT player2
FROM 
      us_men_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      us_ladies_2013) UNION ALL
	  (SELECT player2
FROM 
      us_ladies_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      aus_ladies_2013) UNION ALL
	  (SELECT player2
FROM 
      aus_ladies_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      aus_men_2013) UNION ALL
	  (SELECT player2
FROM 
      aus_men_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      french_men_2013) UNION ALL
	  (SELECT player2
FROM 
      french_men_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      french_ladies_2013) UNION ALL
	  (SELECT player2
FROM 
      french_ladies_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1
FROM 
      french_ladies_2013) UNION ALL
	  (SELECT player2
FROM 
      french_ladies_2013)) AS player
	  GROUP BY player1
	  ORDER BY matches DESC
Q2: Who has played the most matches total in all of US Open, AUST Open, French Open? Answer this both for men and women.
SELECT player1, COUNT(player1) as matches FROM
((SELECT player1 FROM french_men_2013) 
 UNION ALL(SELECT player2 FROM french_men_2013)
 UNION ALL(SELECT player1 FROM us_men_2013)
 UNION ALL(SELECT player2 FROM us_men_2013)
 UNION ALL(SELECT player1 FROM aus_men_2013)
 UNION ALL(SELECT player2 FROM aus_men_2013)
) AS player
	  GROUP BY player1
	  ORDER BY matches DESCSELECT player1, COUNT(player1) as matches FROM
((SELECT player1 FROM french_ladies_2013) 
 UNION ALL(SELECT player2 FROM french_ladies_2013)
 UNION ALL(SELECT player1 FROM us_ladies_2013)
 UNION ALL(SELECT player2 FROM us_ladies_2013)
 UNION ALL(SELECT player1 FROM aus_ladies_2013)
 UNION ALL(SELECT player2 FROM aus_ladies_2013)
) AS player
	  GROUP BY player1
	  ORDER BY matches DESC
WITH aus_ladies_players AS
(SELECT
SUBSTRING(player1, 1, 1) || ' ' ||
SUBSTRING(player1, STRPOS(player1,' ') + 1, 8000) AS name
FROM aus_ladies_2013
UNION ALL
SELECT SUBSTRING(player2, 1, 1) || ' ' ||
SUBSTRING(player2, STRPOS(player2, ' ') + 1, 8000) AS name
FROM aus_ladies_2013),

us_ladies_players AS
(SELECT player1 AS name
FROM us_ladies_2013
UNION ALL
SELECT player2 AS name
FROM us_ladies_2013),

french_ladies_players AS
(SELECT SUBSTRING(player1, 1, 1) || ' ' ||
SUBSTRING(player1, STRPOS(player1, ' ') + 1, 8000) AS name
FROM french_ladies_2013
UNION ALL
SELECT SUBSTRING(player2, 1, 1) || ' ' ||
SUBSTRING(player2, STRPOS(player2, ' ') + 1, 8000) AS name
FROM french_ladies_2013),

all_players AS
(SELECT name
FROM aus_ladies_players
UNION ALL
SELECT name
FROM us_ladies_players
UNION ALL
SELECT name
FROM french_ladies_players)

SELECT name, count(name) AS count
FROM all_players
GROUP BY name
ORDER BY count DESC


```python
WITH aus_men_players AS
(SELECT
SUBSTRING(player1, 1, 1) || ' ' ||
SUBSTRING(player1, STRPOS(player1,' ') + 1, 8000) AS name
FROM aus_men_2013
UNION ALL
SELECT SUBSTRING(player2, 1, 1) || ' ' ||
SUBSTRING(player2, STRPOS(player2, ' ') + 1, 8000) AS name
FROM aus_men_2013),

us_men_players AS
(SELECT player1 AS name
FROM us_men_2013
UNION ALL
SELECT player2 AS name
FROM us_men_2013),

french_men_players AS
(SELECT SUBSTRING(player1, 1, 1) || ' ' ||
SUBSTRING(player1, STRPOS(player1, ' ') + 1, 8000) AS name
FROM french_men_2013
UNION ALL
SELECT SUBSTRING(player2, 1, 1) || ' ' ||
SUBSTRING(player2, STRPOS(player2, ' ') + 1, 8000) AS name
FROM french_men_2013),

all_players AS
(SELECT name
FROM aus_men_players
UNION ALL
SELECT name
```
Men: "R Nadal"	"14"
Women:"V Azarenka"	"18"
Q3: Who has the highest first serve percentage? (Just the maximum value in a single match.)
WITH aus_ladies_players AS
(SELECT
SUBSTRING(player1, 1, 1) || ' ' ||
SUBSTRING(player1, STRPOS(player1,' ') + 1, 8000) AS name,fsp_1 as fsp
FROM aus_ladies_2013
UNION ALL
SELECT SUBSTRING(player2, 1, 1) || ' ' ||
SUBSTRING(player2, STRPOS(player2, ' ') + 1, 8000) AS name,fsp_2 as fsp
FROM aus_ladies_2013),

us_ladies_players AS
(SELECT player1 AS name,fsp_1 as fsp
FROM us_ladies_2013
UNION ALL
SELECT player2 AS name,fsp_2 as fsp
FROM us_ladies_2013),

french_ladies_players AS
(SELECT SUBSTRING(player1, 1, 1) || ' ' ||
SUBSTRING(player1, STRPOS(player1, ' ') + 1, 8000) AS name, fsp_1 as fsp
FROM french_ladies_2013
UNION ALL
SELECT SUBSTRING(player2, 1, 1) || ' ' ||
SUBSTRING(player2, STRPOS(player2, ' ') + 1, 8000) AS name,fsp_2 as fsp
FROM french_ladies_2013),

all_players AS
(SELECT name, fsp
FROM aus_ladies_players
UNION ALL
SELECT name,fsp
FROM us_ladies_players
UNION ALL
SELECT name,fsp
FROM french_ladies_players)

SELECT name, max(fsp)
FROM all_players
GROUP BY name
ORDER BY max(fsp) DESC
Answer: "S Errani"	"93"


Q4: What are the unforced error percentages of the top three players with the most wins? (Unforced error percentage is % of points lost due to unforced errors. In a match, you have fields for number of points won by each player, and number of unforced errors for each field.)
SELECT player, SumUFE/SumTWP as answer FROM (SELECT player, COUNT(player), SUM(UFE) as SumUFE, SUM(TWP) as SumTWP FROM 
(SELECT "Player1" as player, "UFE.1" as UFE, "TPW.2" as TWP FROM "AusOpen_men_2013" WHERE "Result"=1 
UNION ALL SELECT "Player1" as player, "UFE.1" as UFE, "TPW.2" as TWP FROM "AusOpen_women_2013" WHERE "Result"=1 
UNION ALL SELECT "Player1" as player, "UFE.1" as UFE, "TPW.2" as TWP FROM "FrenchOpen_men_2013" WHERE "Result"=1 
UNION ALL SELECT "Player1" as player, "UFE.1" as UFE, "TPW.2" as TWP FROM "FrenchOpen_women_2013" WHERE "Result"=1 
UNION ALL SELECT "Player1" as player, "UFE.1" as UFE, "TPW.2" as TWP FROM "USOpen_men_2013" WHERE "Result"=1
UNION ALL SELECT "Player 1" as player, "UFE.1" as UFE, "TPW.2" as TWP FROM "USOpen_women_2013" WHERE "Result"=1
UNION ALL SELECT "Player2" as player, "UFE.2" as UFE, "TPW.1" as TWP FROM "AusOpen_men_2013" WHERE "Result"=0
UNION ALL SELECT "Player2" as player, "UFE.2" as UFE, "TPW.1" as TWP FROM "AusOpen_women_2013" WHERE "Result"=0
UNION ALL SELECT "Player2" as player, "UFE.2" as UFE, "TPW.1" as TWP FROM "FrenchOpen_men_2013" WHERE "Result"=0 
UNION ALL SELECT "Player2" as player, "UFE.2" as UFE, "TPW.1" as TWP FROM "FrenchOpen_women_2013" WHERE "Result"=0 
UNION ALL SELECT "Player2" as player, "UFE.2" as UFE, "TPW.1" as TWP FROM "USOpen_men_2013" WHERE "Result"=0 
UNION ALL SELECT "Player 2" as player, "UFE.2" as UFE, "TPW.1" as TWP FROM "USOpen_women_2013" WHERE "Result"=0) as New
GROUP BY player ORDER BY COUNT(player) DESC LIMIT 3)d;