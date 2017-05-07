Project4: Analyzing machine & sensor data

1 . Uploading the data in HDFS using hue :

![](media/aa47d38f42f40a245340db657ae591f9.png)

2 . Creating the HVAC\_stage table in Hive :

![](media/cfd6e8679810c20651a2ce208b547789.png)

![](media/06496ca50a27f95d3ccbff30819dc7be.png)

![](media/0a3541a6526c32af9049929aeddadc6e.png)

![](media/c3dffb4ca16f7eb628248e5eef06c41a.png)

![](media/b07d5257132d62001775d94a8ea0fece.png)

![](media/11ba7c515b8916f2866e80760161c7b4.png)

![](media/f6d818e083d35c84077b69d18ed1052d.png)

3 . Create table buildings\_stage

![](media/642c6d7c51108a85cee84ac15611f93e.png)

![](media/bf8e7d82fe7445c98039c6c25a7cd324.png)

4 . For faster execution in hive we can create a new table hvac and save in orc
format .

![](media/cd5e87c3a3fa6f5d62af8287fdc95c67.png)

5 . Create a hvac\_tempeatures table including three new column:

temp\_diff , temprange, extremetemp .

![](media/85f895c6fe5cd452d2326405ebd788d1.png)

![](media/c16340e711c109ca633edb1621801dff.png)

6 . create a table hvac\_building by combining both the tables :

![](media/8c8c2481e63f64d49ad5bb28b9d19d2b.png)

![](media/0f8387f903415b85abf74904fd4759e3.png)

7 . Integration of our hive table with MS Excel 2013 .

(Steps has already been explained in Project 1)

8.

Analysis on the basis of desired requirement:

Ques 1 .

Data visualization/analysis by mapping the buildings that are most frequently
outside of the optimal temperature range. Calculate count of extremetemp (i.e
where the temperature was more than five degrees higher or lower than the target
temperature) by each country and temprange ?

![](media/d93141ccf2d2b76b019eeaf35a631a7c.png)

![](media/9dfaf3de85a2f5d8600accf823b1a18b.png)

Hence we see that Finland has most extreme temperature count .

Ques 2 .

Which country offices run hot (Hot offices can lead to employee complaints and
reduced productivity) and which offices run cold (Cold offices cause elevated
energy expenditures and employee discomfort). Calculate count of offices run in
hot and count of office run in cold by country.

![](media/2a3196d91afa68f43a96ea47cc1ad1a5.png)

Mapping all the countries running hot .

![](media/f63d1c101cfbb8a03811bf7e14547e8e.png)

Mapping all the countries running cold :

![](media/1c943a0a9e76e5ece98762eff1c3642f.png)

Ques 3 : Calculate count of extreme temp by hvacproduct :

![](media/f847f1ff0c9ee4f0c17f04a8e89df23e.png)

Here we see that AC100 is most reliable and regulates temperature well and
FN39TG fails to maintain the standards .

Excel 2013 analysis report link (please install power view in excel to view
report )

https://drive.google.com/open?id=0BxjYrCpAmIoqVUZZSENsWmlIc0k
