# Final Project


## Twenty Research Queries

### Research Question 1

* Write the current research question here (you can copy and paste it from the `research_questions.md` document.)

What department is responsible for the most __red__ parts.

* Place all queries below for this particular question.

``` SQL
SELECT 
count(n.ColorCurrent)
FROM 
nonconformance n
WHERE
n.ColorCurrent == 'RED';
```
RESULT SHOWING TOTAL REDS: 15542
```SQL
SELECT 
n.ColorCurrent, wc.Department, count(*)
FROM 
nonconformance n, workcenter wc, joboperation jo
WHERE 
n.ColorCurrent == 'RED'
AND
n.JobOpID == jo.JobOpID
AND
jo.WcID == wc.WcID
GROUP BY 
wc.Department
ORDER BY
count(*) DESC
LIMIT 
10;
```
RESULT SHOWING TOP 10 DPTS PRODUCING REDS:
```
Color Current | Department | Count
RED|M1 TEAM A|3085
RED|M1 TEAM D|1731
RED|SG TEAM D|1666
RED|INACTIVE|1506
RED|SC TEAM A|800
RED|SG TEAM B|794
RED|M1 TEAM B|789
RED|CSR|668
RED|SG TEAM C|649
RED|M1 TEAM H|615
```
```SQL 
SELECT 
n.createdby, n.ColorCurrent, wc.Department, count(*)
FROM 
nonconformance n, workcenter wc, joboperation jo
WHERE 
n.ColorCurrent == 'RED'
AND
n.JobOpID == jo.JobOpID
AND
jo.WcID == wc.WcID
GROUP BY 
n.createdby
ORDER BY
count(*) DESC
LIMIT 
10;
```
RESULT SHOWING TOP 10 RED PRODUCERS:
```
Created By | Color Current | Department | Count
65ecb0f5ce2aa5fe1a59b1cd2c34c177f22c2ccf|RED|M1 GRIND|227
cf88992d6bc31baab1761b4fff8c2b6679be2ddb|RED|M1 TEAM A|163
567151408d3f825a1e05a086fa213b5edd8b7a41|RED|M1 GRIND|152
231b482771045936b1e03646813bb52f1bf62002|RED|M1 SHIPPING|152
171616cce1609c59f2e43ab4e628f3527dfa45c2|RED|SG TEAM D|152
d5df71ad526210f1d238e974cb830548c5e8fc66|RED|M1 TEAM A|144
4f9815cc707bb4329eabdb828db8a52e19e8c8f8|RED|M1 TEAM A|142
228f51f9da51a547896dd3d17e1b4b1cffa2746f|RED|M1 INSPECT|131
94032e2a25de73e991c8ad268bf5a1606cc26788|RED|M1 TEAM A|130
cbb3dc5aa85489e9ae6723567ac40ff6906bfb65|RED|M1 TEAM A|127
```
```SQL
SELECT 
n.ColorCurrent, wc.Department, count(*)
FROM 
nonconformance n, workcenter wc, joboperation jo
WHERE 
n.ColorCurrent == 'RESOLVED: WAS RED'
AND
n.JobOpID == jo.JobOpID
AND
jo.WcID == wc.WcID
GROUP BY 
wc.Department
ORDER BY
count(*) DESC
LIMIT 
10;
```
RESULT SHOWING TOP 10 RESOLVED COLOR BY DPT: 
```
Color | Department | Count
RESOLVED: WAS RED|M1 TEAM A|29
RESOLVED: WAS RED|SG TEAM C|16
RESOLVED: WAS RED|INACTIVE|16
RESOLVED: WAS RED|CSR|14
RESOLVED: WAS RED|SG TEAM B|13
RESOLVED: WAS RED|M1 GRIND|10
RESOLVED: WAS RED|M1 TEAM H|8
RESOLVED: WAS RED|M2 TEAM E|6
RESOLVED: WAS RED|M1 TEAM D|5
RESOLVED: WAS RED|SG TEAM D|4
```
```SQL
SELECT 
n.createdby, n.ColorCurrent, wc.Department, count(*)
FROM 
nonconformance n, workcenter wc, joboperation jo
WHERE 
n.ColorCurrent == 'RED'
AND 
wc.Department == 'M1 TEAM A'
AND
n.JobOpID == jo.JobOpID
AND
jo.WcID == wc.WcID
GROUP BY 
n.createdby
ORDER BY
count(*) DESC
LIMIT 
10;
```
RESULT SHOWING TOP 10 RED PRODUCERS IN M1 TEAM A (FIRST MOST):
```
Created By | Color | Team | Count
cf88992d6bc31baab1761b4fff8c2b6679be2ddb|RED|M1 TEAM A|138
d5df71ad526210f1d238e974cb830548c5e8fc66|RED|M1 TEAM A|114
94032e2a25de73e991c8ad268bf5a1606cc26788|RED|M1 TEAM A|113
7812febac3e0917283053c814f12d4ed243d081f|RED|M1 TEAM A|108
5e0e4a553cc1aed16a4d57c500ddd4ffefd8ca70|RED|M1 TEAM A|106
aa5cf7c89a01af85350ce44498e5954fb50e7c3d|RED|M1 TEAM A|93
64eb482e87eb9a9425013c27294536a3795180e7|RED|M1 TEAM A|82
c28128d1943138e96d63bc235d32c55cdcfbdd9b|RED|M1 TEAM A|68
346d9db6ef9bad2ed1d63d8d1cb6e9438004ec7f|RED|M1 TEAM A|67
b91ea2904713009bf6e621e3c4ea98ea4aae20eb|RED|M1 TEAM A|64
```
```SQL
SELECT 
n.createdby, n.ColorCurrent, wc.Department, count(*)
FROM 
nonconformance n, workcenter wc, joboperation jo
WHERE 
n.ColorCurrent == 'RED'
AND 
wc.Department == 'M1 TEAM D'
AND
n.JobOpID == jo.JobOpID
AND
jo.WcID == wc.WcID
GROUP BY 
n.createdby
ORDER BY
count(*) DESC
LIMIT 
10;
```
RESULT SHOWING TOP 10 RED PRODUCERS IN M1 TEAM D (SECOND MOST):
```
Created By | Color | Team | Count
2ca319a9ea11833f40478748081d69477a7cf450|RED|M1 TEAM D|123
11905fea38805a9bb26deb97ce0d1a439611a6a2|RED|M1 TEAM D|91
acb0de16dc01c155f5d8805cb804d3baf2bf7f55|RED|M1 TEAM D|85
75e171424a712ac01ce7d3c61331b1cc9264c6c0|RED|M1 TEAM D|76
cefaf61f716a8d6f806a69717fc362ff301b6ab3|RED|M1 TEAM D|75
b1bb155d4d867db98a77c02ad808f49d7bad7d53|RED|M1 TEAM D|70
08fe9321a48857635232c17c39f428f1c94998d1|RED|M1 TEAM D|70
0cb32af3e77202807b43960b7a9919ad7e77e903|RED|M1 TEAM D|68
e451bd0f7f2c8515065d7cd8fe0af84fcdc9d164|RED|M1 TEAM D|54
d350294ab56931a785d97c60184231acf2f57314|RED|M1 TEAM D|50
```
```SQL
SELECT 
n.createdby, n.ColorCurrent, wc.Department, count(*)
FROM 
nonconformance n, workcenter wc, joboperation jo
WHERE 
n.ColorCurrent == 'RED'
AND 
wc.Department == 'SG TEAM D'
AND
n.JobOpID == jo.JobOpID
AND
jo.WcID == wc.WcID
GROUP BY 
n.createdby
ORDER BY
count(*) DESC
LIMIT 
10;
```
RESULT SHOWING TOP 10 RED PRODUCERS IN SG TEAM D (THIRD MOST):
```
Created By | Color | Team | Count
171616cce1609c59f2e43ab4e628f3527dfa45c2|RED|SG TEAM D|151
d7fd67f60019c6615f28912f935b7a2476ce8189|RED|SG TEAM D|115
d847ef255991ae238ee25e3b4473e00c4cad430a|RED|SG TEAM D|107
5602229f64062d57925a21822c7304e3a9c1006a|RED|SG TEAM D|104
0939b349183d82db0ce986e9d08aaffeec4dc71d|RED|SG TEAM D|102
a0570b1509e7c9fa8cc2ded85e4e2b35963ccc28|RED|SG TEAM D|94
fbbd399b9ec7151ae3faa5a04e98b29e2b23d49c|RED|SG TEAM D|92
7fad65a6931adb7dd9a49cc4e00fab49c5b3ad38|RED|SG TEAM D|71
cecec97948d7f6c62cd7b45a38c0e9f244c5b289|RED|SG TEAM D|70
6fcae63b36dd61ce04ae49c063c897bfab6a2272|RED|SG TEAM D|67
```

* In clear and meaningful language, explain what the queries are showing.

The queries above are responsible for going through and connected the databases in order to display who is responsible for the most __RED__ parts. In doing so, I first had to get a gauge for how many __RED__ parts there were. The first query is responsible just for totaling the __RED__ parts. This allows for later analysis calucations. The second query then joins the databases from the nonconformance, workcenter, and joboperation databases in order to obtain the top 10 __RED__ part producing departments. This will allow for us to pinpoint where the __RED__ parts are originating from. Then, I look at the overall top 10 __RED__ producing indviduals based upon the created by code from the nonconformance table. This allows for us to see regardless of department who is responsible for the most __RED__ parts. Then I moved into showing how many of the __RED__ parts were resolved within each of the top 10 departments. This allows for us to understand what departments are making strides to remedy the errors. Lastly, I took the __top three__ departments that produced the most __RED__ parts and analyzed who within the department is responsible for the most noncompliance.

* Please provide several lines of output from the queries.

SEE ABOVE WITH QUERIES

* Describe what we learn from this output.

We learned that the M1 TEAM A, M1 TEAM D, and SG TEAM D departments are the top 3 __RED__ part producing departments. This allows for us to narrow down the search for the departments that perhaps need new equipment or training in order to reduce waste. M1 TEAM A is responsible for __19.84%__ of the __RED__ parts, M1 TEAM D is responsible for __11.13%__,  and SG TEAM D is responsible for __10.71%__. This highlights the importance of targeting these deparments as they account for __41.68%__ of the total __RED__ parts produced within this sample data. We also can see that worker __65ecb0f5ce2aa5fe1a59b1cd2c34c177f22c2ccf__ is responsible for __1.46%__ of all __RED__ parts. This is important because this employee perhaps needs more training or evaluated for their issues.

---


### Research Question 2

* Write the current research question here (you can copy and paste it from the `research_questions.md` document.)

What are the costs involved with nonconformances.

* Place all queries below for this particular question.

``` SQL
SELECT 
jo.jobid, j.unit_price, j.order_quantity, count(*)
FROM
nonconformance n, job j, joboperation jo
WHERE
n.ColorCurrent == 'RED'
AND
n.jobopid == jo.jobopid
AND
jo.jobid == j.jobid
GROUP BY
jo.jobid
ORDER BY
count(*) DESC
LIMIT
10;
```
RESULT OF TOP 10 MOST POPULAR ORDERS THAT HAD RED PARTS: 
```
Job ID | Unit Price | Order Quantity | Count (Times Ordered)
7a7b900f-e72a-46ec-9102-a20761e8e11a|239.82|226|19
5d752699-768d-4d1f-a110-20246d71c265|19.05|1600|18
ae578ed0-6902-4093-b32c-1f39262f0116|75.29|9|16
9eaf0d2d-7d5b-4f8d-bf22-6de98c9af925|116.35|185|16
73c7e4f3-1342-4b87-aa3e-6deb505ddd08|85.0|400|15
d70b04aa-4bc4-4856-bfe6-64e2d7b5e16e|81.86|185|14
c7b95cbb-405e-4d81-9090-9692a5041c38|64.3|620|14
996df5e3-4379-4226-9bce-098f09663105|63.42|700|13
0783b699-d508-4572-9e46-70546c50ef7d|35.57|631|13
86664991-d34b-4a1c-881a-f5aaf5de1dc6|450.32|35|12
```
```SQL
SELECT 
jo.jobid, j.unit_price, j.order_quantity, count(*)
FROM
nonconformance n, job j, joboperation jo
WHERE
n.ColorCurrent == 'RED'
AND
n.jobopid == jo.jobopid
AND
jo.jobid == j.jobid
GROUP BY
jo.jobid
ORDER BY
j.unit_price DESC
LIMIT
10;
```
RESULT OF TOP 10 MOST EXPENSIVE UNITS ORDERED WITH RED PARTS:
```
Job ID | Unit Price | Order Quantity | Count (Times Ordered)
5a30fe8f-e777-4956-ba5e-77e12e52b212|12869.67|9|2
02296ba9-101e-4d57-94f4-a9d9f0afb52d|11461.1|0|1
659bbf2d-fa23-4245-9d14-739f5e72f8a0|9077.74|2|3
022c776e-30fe-4e0e-b97e-446bf1d7225a|8750.74|10|1
1ca726ef-9ab5-4be2-b2b2-8d4ae09e59d4|7331.35|10|3
cda879a5-8e76-4c2c-b25d-8df564e8d46c|7188.2|7|3
beedb34a-3937-4e88-bb1b-4abcdb693dbb|7188.2|1|1
5aa9cfe7-8fa8-49d5-8d8c-baca0885dc55|6052.3|3|2
2f72c7f9-86c0-409d-99d7-2f4b80629a21|5955.37|3|1
7a00aadb-bfc5-4312-ace0-bf8824103930|5867.66|1|1
```
```SQL
SELECT 
SUM(j.unit_price * j.order_quantity)
FROM
nonconformance n, job j, joboperation jo
WHERE
n.ColorCurrent == 'RED'
AND
n.jobopid == jo.jobopid
AND
jo.jobid == j.jobid;
```
RESULT OF TOTAL COST OF ORDERS WITH RED PARTS: 221663494.04
```SQL
SELECT 
jo.jobid, j.unit_price * j.order_quantity AS total_price
FROM
nonconformance n, job j, joboperation jo
WHERE
n.ColorCurrent == 'RED'
AND
n.jobopid == jo.jobopid
AND
jo.jobid == j.jobid
GROUP BY 
jo.jobid
ORDER BY
total_price DESC
LIMIT
10;
```
RESULT OF TOP 10 MOST EXPENSIVE ORDERS WITH RED PARTS: 
```
Job ID | Total Price
05cb1379-33c4-495f-b121-99c625a9aa4d|228432.75
5a91b8f3-1b19-4523-9a57-7f691eea3a40|215264.0
bb7336b3-7c11-42fc-a399-bad868892e15|202773.67
88630045-c748-420d-940c-06e5c0f04143|182000.0
259bb610-17f9-45ac-82e7-07184e1de806|182000.0
3c3ab729-9401-408c-ac7c-7955b3e8cb4b|174724.37
c3a4b40d-055a-45d7-ba1f-1bd02c6b6932|160232.64
58610570-8036-4c36-b63f-8c2c355f398b|153450.0
f7ca6834-5afd-4f83-84db-9b6a3ea65421|149978.0
ee4afcb8-b93a-4046-88a6-553e0328eb74|148549.01

```
```SQL
SELECT 
jo.jobid, j.unit_price * j.order_quantity AS total_price, jm.material
FROM
nonconformance n, job j, joboperation jo, jobmaterialguess jm
WHERE
n.ColorCurrent == 'RED'
AND
n.jobopid == jo.jobopid
AND
jo.jobid == j.jobid
AND 
j.jobid == jm.jobid
GROUP BY 
jo.jobid
ORDER BY
total_price DESC
LIMIT
10;
```
RESULT OF TOP 10 MOST EXPENSIVE ORDERS WITH RED PARTS AND THEIR MATERIAL:
```
Job Id | Total Price | Material
05cb1379-33c4-495f-b121-99c625a9aa4d|228432.75|CERROTRUCAKE
5a91b8f3-1b19-4523-9a57-7f691eea3a40|215264.0|15-5RD3.50LC
bb7336b3-7c11-42fc-a399-bad868892e15|202773.67|9440791-1P
88630045-c748-420d-940c-06e5c0f04143|182000.0|INCO718RD5.50
259bb610-17f9-45ac-82e7-07184e1de806|182000.0|INCO718RD5.50
3c3ab729-9401-408c-ac7c-7955b3e8cb4b|174724.37|MS21209F1-15
c3a4b40d-055a-45d7-ba1f-1bd02c6b6932|160232.64|15-5RD6.75
58610570-8036-4c36-b63f-8c2c355f398b|153450.0|C729RD2.25
f7ca6834-5afd-4f83-84db-9b6a3ea65421|149978.0|MS21209F1-15
ee4afcb8-b93a-4046-88a6-553e0328eb74|148549.01|15-5RD6.75
```
```SQL
SELECT 
jo.jobid, j.unit_price, j.order_quantity, jm.material
FROM
nonconformance n, job j, joboperation jo, jobmaterialguess jm
WHERE
n.ColorCurrent == 'RED'
AND
n.jobopid == jo.jobopid
AND
jo.jobid == j.jobid
AND 
j.jobid == jm.jobid
GROUP BY 
jo.jobid
ORDER BY
j.unit_price DESC
LIMIT
10;
```
RESULT OF TOP 10 MOST EXPENSIVE UNITS ORDERED WITH RED PARTS WITH MATERIAL:
```
Job ID | Unit Price | Order Quantity | Material
5a30fe8f-e777-4956-ba5e-77e12e52b212|12869.67|9|15-5RD8.00
02296ba9-101e-4d57-94f4-a9d9f0afb52d|11461.1|0|UNKNOWN
659bbf2d-fa23-4245-9d14-739f5e72f8a0|9077.74|2|2124PL3.00 X 7.20 DIA
022c776e-30fe-4e0e-b97e-446bf1d7225a|8750.74|10|219179 PLUG
1ca726ef-9ab5-4be2-b2b2-8d4ae09e59d4|7331.35|10|6061PL7.00X7.75X10.75
cda879a5-8e76-4c2c-b25d-8df564e8d46c|7188.2|7|57755-98
beedb34a-3937-4e88-bb1b-4abcdb693dbb|7188.2|1|57755-98
5aa9cfe7-8fa8-49d5-8d8c-baca0885dc55|6052.3|3|6AL4VPL2.50X7.25ODX5.25ID
2f72c7f9-86c0-409d-99d7-2f4b80629a21|5955.37|3|CERROTRUCAKE
7a00aadb-bfc5-4312-ace0-bf8824103930|5867.66|1|C71500RD6.50
```

* In clear and meaningful language, explain what the queries are showing.

These queries are responsible for evalutaing the costs involved with a noncompliance __RED__ part. In order to do so, I started with pulling the information on the top 10 most popular orders with a __RED__ part involved. Following that result, I looked into the most expenisve unit prices of the parts ordered that featured a __RED__ part. After that, I looked into the total cost all of the orders with a __RED__ part. This total was astonsihing. In order to provide more insights, I looked into the most expensive orders by multiplying the unit price by the number of units purchased. I then paired this information with the material to provide more information as to a possible connection between material and non-conformance that will be dug into later in the document. Finally, I backtracked a few queries and added the material to the most expensive units to get a deeper understanding of these expensive materials.

* Please provide several lines of output from the queries.

SEE ABOVE WITH QUERIES

* Describe what we learn from this output.

From this output we see that there is a total of over 221 million dollars worth of orders that contain some level of __RED__ parts within the database. This figure is astonishing as these orders are no small levels of revenue. This provides scope to the reserach that we are conducting as these are important orders for business. We also see that there are a handful of repeat orders that have consistently received __RED__ parts with order __7a7b900f-e72a-46ec-9102-a20761e8e11a__ showing up in the database 19 times. When we look at the most expenisve units that contain a __RED__ part, we see a part made of __15-5RD8.00__ worth over 12000. With the value of this order, a __RED__ part with a defect would lead to a significant loss for the company. In terms of the repeat orders, we see the material __CERROTRUCAKE__ show up as the most expeinsve order that received __RED__ parts with a total cost of __228432.75__ for the order. If there are delays in production for these orders, the company will begin to lose business that could cause losing out to competitors. Overall, we see a significant need for the departments to start to minimize the amount of __RED__ parts produced.

---


### Research Question 3

* Write the current research question here (you can copy and paste it from the `research_questions.md` document.)

- 1) We want to identify the percentage of the red mistakes out of all of them
  2) We want to find which percentage is resolved red from all of the mistakes
  3) We want to find what is the most popular mistake codes among reds
  4) We want to find which mistake codes are the least popular  
  5) We want to know who creates the most of the red parts
    

* Place all queries below for this particular question.


1) We want to identify the percentage of the red mistakes out of all of them:
``` SQL
select count(JobOpID) from nonconformance where ColorCurrent=="RED";

15542
```
``` SQL
select count(JobOpID) from nonconformance;

20420
```
--------------------
76.11 percent

2) We want to find which percentage is resolved red from all of the mistakes
``` SQL
select count(JobOpID) from nonconformance where ColorCurrent=="RESOLVED: WAS RED";

166
```
---------------------
0.8 perent - it''s insignificant

3) We want to find what is the most popular mistake codes among reds
``` SQL
select DefectCodeDisplayText, count(DefectCodeDisplayText) from (select ColorCurrent, DefectCodeDisplayText from nonconformance where ColorCurrent=="RED") group by DefectCodeDisplayText order by count(DefectCodeDisplayText) DESC ;


103A-ID O/S	2365
101D-LENGTH OUTR U/S	1455
517-PART MUTILATION	1149
104B-OD U/S	1107
404-SET-UP PART	990
```
4) We want to find which mistake codes are the least popular 
``` SQL
select DefectCodeDisplayText, count(DefectCodeDisplayText) from (select ColorCurrent, DefectCodeDisplayText from nonconformance where ColorCurrent=="RED") group by DefectCodeDisplayText order by count(DefectCodeDisplayText) ASC ;

205C-ELECTRO ETCH	1
504-DOCUMENTATION	1
505-PACKAGING	1
508-UNAPPROVED SOURC	1
520-PART DISASSEMB	1
```

5) We want to know who creates the most of the red parts
``` SQL
select CreatedBy, count(CreatedBy) from (select ColorCurrent, DefectCodeDisplayText, CreatedBy from nonconformance where ColorCurrent=="RED") group by CreatedBy order by count(CreatedBy) DESC ;

65ecb0f5ce2aa5fe1a59b1cd2c34c177f22c2ccf	230
231b482771045936b1e03646813bb52f1bf62002	192
4f9815cc707bb4329eabdb828db8a52e19e8c8f8	171
64b34252f756c8b37d8a97af92b9fc9c21182cc6	166
cf88992d6bc31baab1761b4fff8c2b6679be2ddb	165


```

* In clear and meaningful language, explain what the queries are showing.

The first two queries are showing the number of red mistakes and number of total mistakes, thus letting us to estimate which part of all of mistakes red ones take. The third one calculates the total number of red mistakes that were resolved. The fourth and fifth query are designed to show the most and least popular mistakes, additionally calculating their total number. The sixth query identifies the id of the creator of the mistake.


* Please provide several lines of output from the queries.
NUMBER OF RED MISTAKES
15542

NUMBER OF TOTAL MISTAKES
20420
  
NUMBER OF RESOLVED RED MISTAKES
166

THE MOST POPULAR MISTAKES

103A-ID O/S	2365
101D-LENGTH OUTR U/S	1455
517-PART MUTILATION	1149
104B-OD U/S	1107
404-SET-UP PART	990

THE LEAST POPULAR MISTAKES

205C-ELECTRO ETCH	1
504-DOCUMENTATION	1
505-PACKAGING	1
508-UNAPPROVED SOURC	1
520-PART DISASSEMB	1

CREATORS WITH THE BIGGEST NUMBER OF MISTAKES

65ecb0f5ce2aa5fe1a59b1cd2c34c177f22c2ccf	230
231b482771045936b1e03646813bb52f1bf62002	192
4f9815cc707bb4329eabdb828db8a52e19e8c8f8	171
64b34252f756c8b37d8a97af92b9fc9c21182cc6	166
cf88992d6bc31baab1761b4fff8c2b6679be2ddb	165


* Describe what we learn from this output.
We learn that around 3 out of 4 mistakes are red mistakes, confirming the concers about them. The number of resolved red mistakes is unfortunately insignificant. We also found the statistics of the most popular mistakes - with this it would be easier to find the problems in the process and thus to fix them. We also have found the least popular mistakes - they happened roughly 1 time each so we can conclude3 that they might be insignificant. Additionally there is a statistic of the creators that made the mistakes - we can track problems using their work and them to find a solution to fix them.
---


### Research Question 4

* Write the current research question here (you can copy and paste it from the `research_questions.md` document.)

4a ->Which Workcenters were Involved in Faulty Productions?

4b ->What is the fault frequency in quick setup operations compared to longer setup operations?

4c ->How does the frequency of 'RED' nonconformance incidents vary with different estimated setup hours in job operations?

4d ->What is the distribution of nonconformance incidents across various defect codes in the production process?"

```SQL
4a SELECT joboperation.WcID  FROM joboperation, nonconformance WHERE joboperation.JobOpID = nonconformance.JobOpID AND nonconformance.ColorCurrent = "RED";

4b 

    Query for Fault Frequency in Quick Setup Operations:

    SELECT COUNT(*) AS QuickSetupFaultFrequency FROM nonconformance, joboperation WHERE ColorCurrent = "RED" AND joboperation.Est_Setup_Hrs < 0.25 AND joboperation.JobOpID = nonconformance.JobOpID;


    Query for Fault Frequency in Longer Setup Operations 

    SELECT COUNT(*) AS LongerSetupFaultFrequency FROM nonconformance, joboperation WHERE ColorCurrent = "RED" AND joboperation.Est_Setup_Hrs >= 0.25 AND joboperation.JobOpID = nonconformance.JobOpID;


4c-> SELECT joboperation.Est_Setup_Hrs, COUNT(nonconformance.ColorCurrent) FROM nonconformance, joboperation WHERE nonconformance.ColorCurrent = "RED" AND joboperation.JobOpID = nonconformance.JobOpID
GROUP BY joboperation.Est_Setup_Hrs;


4d-> SELECT DefectCodeDisplayText, COUNT(nonconformance.ColorCurrent) FROM nonconformance, joboperation WHERE joboperation.JobOpID = nonconformance.JobOpID
GROUP BY DefectCodeDisplayText;

```

* In clear and meaningful language, explain what the queries are showing.

4a- Query for Workcenters Involved in Faulty Productions:

The query returns 15,542 rows of results in 9.56 seconds.The sample output provided consists of the same Workcenter ID repeated multiple times for instance "9825a111-018c-47c4-9357-7d708313104b". This suggests that the same Workcenter ID is associated with multiple job operations that produced faulty (RED) parts.

4b- Queries for Fault Frequency in Quick and Longer Setup Operations:

The query for Quick Setup Operations returns a fault frequency of 2,472.
The query for Longer Setup Operations returns a fault frequency of 13,070.
From this, we can infer that there are more faults (nonconformance incidents with "RED" status) in job operations with longer setup times compared to those with quick setups.

4c- Query for Frequency of 'RED' Nonconformance Incidents by Estimated Setup Hours:

The results show the distribution of fault frequencies (nonconformance incidents with "RED" status) across different estimated setup hours.For example, there are 2,470 incidents with an estimated setup time of 0.0 hours, 1 incident with 0.15 hours, 355 incidents with 0.25 hours, and so on. This provides insights into how fault frequencies vary with different estimated setup times. It indicates that setup times of 0.0 hours have a high fault frequency.

4d- Query for Distribution of Nonconformance Incidents by Defect Codes:

The results show the distribution of fault frequencies (nonconformance incidents with "RED" status) across different defect codes.For example, there are 3 incidents associated with the defect code "001-AUDIT FINDING," 46 incidents with "100-CUSTOMER ERROR," 233 incidents with "101A-LENGTH INNR O/S," and 236 incidents with "101B-LENGTH INNR U/S," among others.This provides insights into which defect codes are more frequently associated with nonconformance incidents, helping identify common issues in the production process.


* Please provide several lines of output from the queries.

```sql

4a  "Which Workcenters were Involved in Faulty Productions?"

    Result: 15542 rows returned in 9560ms

    9825a111-018c-47c4-9357-7d708313104b
    9825a111-018c-47c4-9357-7d708313104b
    9825a111-018c-47c4-9357-7d708313104b


4b  "What is the fault frequency in quick setup operations compared to longer setup operations?"
 
    Query for Fault Frequency in Quick Setup Operations  = 2472
    Query for Fault Frequency in Longer Setup Operations = 13070

4c  "How does the frequency of 'RED' nonconformance incidents vary with different estimated setup hours in job operations?"

    0.0     2470
    0.15    1
    0.17	1
    0.25	355
    0.4	1
    0.45	1
    0.48	2

4d  "What is the distribution of nonconformance incidents across various defect codes in the production process?"

    001-AUDIT FINDING	3
    100-CUSTOMER ERROR	46
    101A-LENGTH INNR O/S	233
    101B-LENGTH INNR U/S	236
    101C-LENGTH OUTR O/S	359

```

* Describe what we learn from this output.

In the pursuit of enhancing profitability and reducing waste, the four queries provide valuable insights into different aspects of the production process.

Firstly, the query for Workcenters Involved in Faulty Productions (4a) helps us pinpoint specific Workcenters consistently associated with faulty productions. This information is crucial for targeted improvements, whether through specialized training or process enhancements, leading to higher-quality products and reduced scrap, ultimately translating into increased profits.

Secondly, the queries comparing Fault Frequency in Quick and Longer Setup Operations (4b) highlight the potential impact of setup times on fault occurrence. Lowering fault frequencies in longer setup operations can directly lead to cost savings and improved profit margins. Conversely, if quick setup operations exhibit a lower fault frequency, it prompts us to explore optimization opportunities across operations, further enhancing profitability.

Thirdly, the query analyzing the Frequency of 'RED' Nonconformance Incidents by Estimated Setup Hours (4c) provides insights into the relationship between setup times and fault frequency. Identifying an ideal setup duration that minimizes defects offers the potential for waste reduction and higher product quality, leading to increased customer satisfaction and profits.

Lastly, the query addressing the Distribution of Nonconformance Incidents by Defect Codes (4d) empowers us to focus on common defect codes, implementing targeted process improvements and reducing rework and scrap costs. By minimizing defects associated with specific defect codes, we directly impact profitability.

To summarize,I think these queries and their analyses offer a roadmap for process optimization, waste reduction, and profit maximization. By identifying areas requiring improvement, implementing tailored enhancements, and optimizing operations based on the insights gained, we can elevate product quality, reduce costs, and significantly enhance profitability.

---

### Research Question 5

* Write the current research question here (you can copy and paste it from the `research_questions.md` document.)

5a-> Can we identify nonconformance issues that were addressed and closed within the specific timeframe of the first half of 2023?

5b -> How frequently do nonconformance issues occur in different workcenters?

5c -> What is the average duration it takes for nonconformance issues to be resolved in job operations, and how does this duration vary across different job operations?

5d -> What is the duration between the scheduled start date of job operations and the date they were closed for nonconformance issues, and how does this duration vary across different job operations?

* Place all queries below for this particular question.

``` SQL
5a-> SELECT joboperation.JobOpID FROM joboperation JOIN nonconformance ON joboperation.JobOpID = nonconformance.JobOpID JOIN joboperationclosedate ON joboperation.JobOpID = joboperationclosedate.JobOpID WHERE joboperationclosedate.LastChangeHistoryClosedDate BETWEEN '2023-01-01' AND '2023-06-30';

5b-> SELECT joboperation.WcID, COUNT(nonconformance.JobOpID) FROM joboperation JOIN nonconformance ON joboperation.JobOpID = nonconformance.JobOpID JOIN joboperationclosedate ON joboperation.JobOpID = joboperationclosedate.JobOpID GROUP BY joboperation.WcID;

5c-> two approaches: 
        SELECT joboperation.JobOpID, AVG(julianday(joboperationclosedate.LastChangeHistoryClosedDate) - julianday(joboperation.Sched_Start)) AS AverageDays FROM joboperation JOIN nonconformance ON joboperation.JobOpID = nonconformance.JobOpID JOIN joboperationclosedate ON joboperation.JobOpID = joboperationclosedate.JobOpID GROUP BY joboperation.JobOpID;

        SELECT joboperation.JobOpID, AVG(DATEDIFF(joboperationclosedate.LastChangeHistoryClosedDate, joboperation.Sched_Start)) FROM joboperation JOIN nonconformance ON joboperation.JobOpID = nonconformance.JobOpID JOIN joboperationclosedate ON joboperation.JobOpID = joboperationclosedate.JobOpID GROUP BY joboperation.JobOpID;

5d-> SELECT joboperation.JobOpID, 
       (julianday(joboperationclosedate.LastChangeHistoryClosedDate) - julianday(joboperation.Sched_Start)) AS Duration
FROM joboperation JOIN joboperationclosedate ON joboperation.JobOpID = joboperationclosedate.JobOpI ORDER BY Duration DESC;

```

* In clear and meaningful language, explain what the queries are showing.

5a-> This research question focuses on identifying nonconformance issues that were successfully addressed and closed during the defined timeframe of the first half of 2023. The query associated with this question allows us to pinpoint these issues, providing insights into the company's ability to resolve quality issues promptly and efficiently within a specific time frame.

5b-> This research question aims to analyze the frequency of nonconformance issues across various workcenters. The query counts nonconformance issues in each workcenter, enabling us to identify which areas experience a higher occurrence of quality or operational challenges. This information is crucial for prioritizing improvement efforts and allocating resources to address recurring problems.

5c-> This research question seeks to understand the average duration it takes to resolve nonconformance issues within job operations. By grouping job operations and calculating the average duration, we can identify variations in the time it takes to address and resolve quality issues, helping pinpoint areas where issue resolution can be optimized.

5d-> This research question focuses on calculating the duration between the scheduled start date of job operations and their closure due to nonconformance issues. The query orders these durations in descending order, allowing us to identify job operations with longer resolution times. This analysis helps in understanding the efficiency of addressing nonconformance issues and highlights areas where improvements can be made.

* Please provide several lines of output from the queries.

```sql

5a "Can we identify nonconformance issues that were addressed and closed within the specific timeframe of the first half of 2023?"

afaef980-ebdf-4b19-bf4d-2017ded85ab5
0d51f218-0b89-45b9-896f-121ffed52c9f
a6850c23-c572-4311-9ac4-012760bb2f57
0c2fb0e6-1335-46e7-9869-93bd5c4d8369
a0c2d24c-bb14-440a-b9a8-082ed18c6d3b
a0c2d24c-bb14-440a-b9a8-082ed18c6d3b
f8af04f3-037c-43a1-b7ea-bc7ddecd272d

5b  "How frequently do nonconformance issues occur in different workcenters?"

	1086
0017c626-f269-4bfe-9874-607458883274	1
0137ce78-6a19-4eb6-87fe-5836ff2e3d44	11
015a8e5a-fa71-4ffe-bc5b-0d798e0a5bb1	53
01d81cca-d802-4aff-9e58-fa5a90b0f190	3
02247f03-7339-49e0-9fc4-872c4c2b976c	1
0357298c-a167-4451-96dd-66038a181f77	4
036c38d5-4ff8-4a13-816f-262b3c7accfe	2

5c "What is the average duration it takes for nonconformance issues to be resolved in job operations, and how does this duration vary across different job operations?"

000138cf-d219-4a5e-8a07-95b958ad4d02	161.869787847158
000a8334-7531-4f2d-bbb8-099a2ac1c71b	-7.05826643528417
000eab7a-8fbb-4c3a-a48b-d5b1e7a970fa	
00131863-e392-429d-93b7-57de511964e1	6.93177230330184
001f8b22-82ed-4e58-abfc-365bb591fce2	
0022cd67-cf09-4f0b-937c-85405f6548cb	-5.19129741890356
0023f477-6e2f-4844-a0fa-91deb94a0d70	2.33042508084327
00270c83-89b9-4cc0-8420-a9629e1abfc9	23.7531178588979

5c "What is the duration between the scheduled start date of job operations and the date they were closed for nonconformance issues, and how does this duration vary across different job operations?"

a9a29419-a163-449e-a01a-16f37b5df1c8	10794.4256914007
312e8145-8eca-4a47-b131-18dc3754e7a1	10793.3274724535
6ba60bd7-b053-49a2-a2ec-c36f082f9847	2104.32651704876
14ef2672-24e8-4464-9d1f-6defcf93df95	1807.33845335664
80e33c70-40bf-4a4d-abb9-1aec5748ea2e	1567.78389933985
87683bcb-7dd8-4437-95ed-f03a597c11e3	1188.05963171273
c59eb1f8-f62c-41a7-ad03-19c082ac9c38	1185.2712320257


```

* Describe what we learn from this output.

Firstly, in response to question 5a, I identified specific nonconformance issues that were successfully addressed and closed within the timeframe of the first half of 2023. This information is crucial as it allows us to assess the efficiency of our issue resolution processes and evaluate our ability to meet quality standards within a specific timeframe.

Moving on to question 5b, I learned about the frequency of nonconformance issues across different workcenters. This data helps us pinpoint areas that experience a higher occurrence of quality or operational challenges. By identifying these areas, we can allocate resources and prioritize improvement efforts effectively, ultimately enhancing our overall operational efficiency.

Regarding question 5c, I gained insights into the average duration it takes to resolve nonconformance issues within job operations. This duration can vary across different operations, which is valuable information for process optimization. By understanding where issues take longer to resolve, we can focus on improving those areas to streamline our processes and reduce resolution times.

Lastly, question 5d provided data on the duration between the scheduled start date of job operations and the date they were closed due to nonconformance issues. This information helps us assess the efficiency of addressing nonconformance issues and highlights areas where improvements can be made to expedite issue resolution. In summary, these outputs empower us to make data-driven decisions, optimize our processes, and ultimately enhance our overall operational performance and product quality.

(Did you remember to place your name at the top of this document?)
