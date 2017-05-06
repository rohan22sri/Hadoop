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

![](media/14ba72a63b3e2c6ff63972320e7ecf36.png)

![](media/feeea801dd610cc84fdd728d07d6e9a1.png)

Table - omniture\_all:

![](media/37f65a4186f4fd15a451b998d41e4794.png)

6 .

![](media/37f65a4186f4fd15a451b998d41e4794.png)

7. create view omniture\_final by refining omniture\_all table. We will only
select important column.

![](media/8a332bf2275482d13d85cac282afc599.png)

![](media/f6dde66e42d0667e5a470a266e7632c7.png)

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

![](media/69be54e572d58209d38c187e19adb809.png)

![](media/596708869cca2d573afaa5da16992db8.png)

**Step 2: Access the Website Clickstream Data with Excel**

1.  Connect ms excel 2013(query wizard) with cloudera vm

![](media/d542b9c1b4d1e7a79a42be31aa2bb143.png)

1.  Install cloudera odbc driver (32 bit). Configure and the same will be
    reflected in ms excel 2013

![](media/0c9b2ed8cd4f5186b838d2010cc26afe.png)

3 .

![](media/2d086aff1aadfc5f3ba997925af1c7d1.png)

![](media/a8cf15c1bc507bbf1b82354d407c0752.png)

![](media/a1800c8ff40dab1dac899b96ed095763.png)

![](media/37f450f26cbaadd3831809930a9b422a.png)

![](media/33c47d7c64eee7b71339bd4fa8a14b37.png)

![](media/9650d3c92a73058ca41f9b8dcd200b92.png)

![](media/5cb952116e93ee472b814854fa451e6e.png)

1.  .This is the final table we get in excel for analysis in excel

![](media/0dba7d2e3cd53945da161924ff58200a.png)

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
