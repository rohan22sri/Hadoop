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


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image9.png)


Table - omniture\_all:

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image10.png)


6 .

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image11.png)


7. create view omniture\_final by refining omniture\_all table. We will only
select important column.

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image12.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image13.png)



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

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image14.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image15.png)


**Step 2: Access the Website Clickstream Data with Excel**

1.  Connect ms excel 2013(query wizard) with cloudera vm

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image16.png)


1.  Install cloudera odbc driver (32 bit). Configure and the same will be
    reflected in ms excel 2013

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image17.png)


3 .

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image18.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image19.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image20.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image21.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image22.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image23.png)


![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image24.png)


1.  .This is the final table we get in excel for analysis in excel

![ScreenShot](https://raw.githubusercontent.com/rohan22sri/Hadoop/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/image25.png)


5. Analysis using Power view

![](media/49ad081e483b6f2372134b4f5ea79542.png)

![](media/b909e5ce288c3c0d9fdf4160ad6abaae.png)

Ques 1.

Analyze the clickstream data by location

Here we are analysis ip usage all over the continent :

Analysis over USA:-here we are counting usage of our website by counting total
ip

![](media/625727f2b22872eebe836541ddbb0c19.png)

Analysis of website user in France by counting IP:

![](media/b6dd98b6109c8d46e57b61464ae7b6c5.png)

Analysis of website usage by counting IP on American states

![](media/cae7763fb5cb60f81e710bee1c89589e.png)

Ques 2: Filter the data by product category

Here we can analyse all category over all over the continent. I have shown
category count in USA states below:

![](media/7e96d20b9e282213feb88dda44f32d23.png)

Ques 3 . Graph the website user data by age and gender

Here we analysing the most active age group for females for category ‘clothing’.

It comes to be 22 to 32 for category clothing .

Similarly we can analyse other age group for various category .

![](media/f9f4ad66efe2989e4b8ab1860f008a84.png)

Ques 4 : Pick a target customer segment

Here we are analysing active age group who visits the website regularly.

It comes to be 25 – 34 . PFB.

![](media/dd2a58a4c2144eeb2c38ba1fe37f273c.png)

1.  . Identify a few web pages with the highest bounce rates

A page is considered to have high bounce rate if it is the last page the user
visit before leaving the page .

![](media/e07efc395a173acb04243f63de16dd0c.png)

![](media/90f2e3ec6a63e11877033ddc229a6488.png)

So finally we have some of the url having maximum bounce rate .

**Excel sheet link for analysis(need to have ms excel 2013+ and power view
activated )**

**https://drive.google.com/open?id=0BxjYrCpAmIoqYjNWZFZMYjMxdTg**
