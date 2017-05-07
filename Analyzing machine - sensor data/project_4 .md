Project4: Analyzing machine & sensor data

1 . Uploading the data in HDFS using hue :

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image1.png)

2 . Creating the HVAC\_stage table in Hive :

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image2.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image3.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image4.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image5.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image6.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image7.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image8.png)

3 . Create table buildings\_stage

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image9.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image10.png)

4 . For faster execution in hive we can create a new table hvac and save in orc
format .

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image11.png)

5 . Create a hvac\_tempeatures table including three new column:

temp\_diff , temprange, extremetemp .

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image12.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image13.png)

6 . create a table hvac\_building by combining both the tables :

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image14.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image15.png)

7 . Integration of our hive table with MS Excel 2013 .

steps : https://github.com/rohan22sri/Hadoop/blob/master/cloudera%205.8%20hive%20and%20ms%20excel%20integration/integration_steps.md

8.

Analysis on the basis of desired requirement:

Ques 1 .

Data visualization/analysis by mapping the buildings that are most frequently
outside of the optimal temperature range. Calculate count of extremetemp (i.e
where the temperature was more than five degrees higher or lower than the target
temperature) by each country and temprange ?

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image16.png)

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image17.png)

Hence we see that Finland has most extreme temperature count .

Ques 2 .

Which country offices run hot (Hot offices can lead to employee complaints and
reduced productivity) and which offices run cold (Cold offices cause elevated
energy expenditures and employee discomfort). Calculate count of offices run in
hot and count of office run in cold by country.

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image18.png)

Mapping all the countries running hot .

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image19.png)

Mapping all the countries running cold :

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image20.png)

Ques 3 : Calculate count of extreme temp by hvacproduct :

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Analyzing%20machine%20-%20sensor%20data/media/image21.png)

Here we see that AC100 is most reliable and regulates temperature well and
FN39TG fails to maintain the standards .

Excel 2013 analysis report link (please install power view in excel to view
report )

https://drive.google.com/open?id=0BxjYrCpAmIoqVUZZSENsWmlIc0k
