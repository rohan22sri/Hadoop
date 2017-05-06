**Project1: Big Data Analytics using Clickstream Data**

Step 1: View and Refine the Website Clickstream Data .

1.  Upload all the 3 logs in Hue and make corresponding tables for it .

2. 

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image1.bmp)

3.

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image2.png)

4.

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image3.png)

5. from metastore browser create all the three tables :

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image4.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image5.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image6.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image7.png)


Table -url\_mapping:

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image8.png)





Table - omniture\_all:

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image9.png)


6 .

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image10.png)


7. create view omniture\_final by refining omniture\_all table. We will only
select important column.

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image11.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image12.png)



8. create a final table by joining all three

create table webanalytics\_final as

select

to\_date(o.ts) logdate,

o.url,

o.ip,

o.city,

upper(o.state) state,

o.country,

p.category,

CAST(datediff(from\_unixtime(unix\_timestamp()),from\_unixtime
(unix\_timestamp(u.birth\_date,'dd-MMM-yy')))/365 as int) age,

u.gender gender

from omniture\_final o inner join url\_mapping p on o.url=p.url

left outer join reguser1 u on o.swid =concat('{',u.swid,'}')

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image13.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image14.png)


**Step 2: Access the Website Clickstream Data with Excel**

1.  Connect ms excel 2013(query wizard) with cloudera vm

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image15.png)


1.  Install cloudera odbc driver (32 bit). Configure and the same will be
    reflected in ms excel 2013

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image16.png)


3 .

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image17.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image18.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image19.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image20.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image21.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image22.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image23.png)


1.  .This is the final table we get in excel for analysis in excel

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image24.png)


5. Analysis using Power view

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image25.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image26.png)


Ques 1.

Analyze the clickstream data by location

Here we are analysis ip usage all over the continent :

Analysis over USA:-here we are counting usage of our website by counting total
ip

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image27.png)


Analysis of website user in France by counting IP:

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image28.png)

Analysis of website usage by counting IP on American states
![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image29.png)

Ques 2: Filter the data by product category

Here we can analyse all category over all over the continent. I have shown
category count in USA states below:

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image30.png)

Ques 3 . Graph the website user data by age and gender

Here we analysing the most active age group for females for category ‘clothing’.

It comes to be 22 to 32 for category clothing .

Similarly we can analyse other age group for various category .

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image31.png)

Ques 4 : Pick a target customer segment

Here we are analysing active age group who visits the website regularly.

It comes to be 25 – 34 . PFB.

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image32.png)

1.  . Identify a few web pages with the highest bounce rates

A page is considered to have high bounce rate if it is the last page the user
visit before leaving the page .

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image33.png)

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image34.png)

So finally we have some of the url having maximum bounce rate .

**Excel sheet link for analysis(need to have ms excel 2013+ and power view
activated )**

**https://drive.google.com/open?id=0BxjYrCpAmIoqYjNWZFZMYjMxdTg**
