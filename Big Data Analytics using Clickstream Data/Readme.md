Project1: Analytics using clickstream Data

Clickstream Data

Clickstream data is an information trail a user leaves behind while visiting a website. It is typically captured in semi-structured website log files.

These website log files contain data elements such as a date and time stamp, the visitor’s IP address, the destination URLs of the pages visited, and a user ID that uniquely identifies the website visitor. Potential Uses of Clickstream Data One of the original uses of Hadoop at Yahoo was to store and process their massive volume of clickstream data. Now enterprises of all types can use Hadoop and the cloudera to refine and analyze clickstream data. They can then answer business questions such as:

What is the most efficient path for a site visitor to research a product, and then buy it? (Path Optimization)

What products do visitors tend to buy together, and what are they most likely to buy in the future? (Association Analysis & Next product to buy)

Where should I spend resources on fixing or enhancing the user experience on my website? (Allocation of website resources) we will focus on the “path optimization” use case. Specifically: how can we improve our website to reduce bounce rates and improve conversion?


Input Data Here’s a summary of the data we’re working with:

Omniture logs – website log files containing information such as URL, timestamp, IP address, geocoded IP address, and user ID (SWID)

The Omniture log dataset contains about 4 million rows of data, which represents five days of clickstream data. Often, organizations will process weeks, months, or even years of data.

Users– CRM user data(registered Users) listing SWIDs (Software User IDs) along with date of birth and gender.

Products – CMS data that maps product categories to website URLs.

Data Download Link : https://dl.dropboxusercontent.com/u/335294585/BigData%20Projects/Project-1.rar

Expected Output: In order to optimize your website and convert more visits into sales and revenue.

Analyze the clickstream data by location

Filter the data by product category

Graph the website user data by age and gender

Pick a target customer segment

Identify a few web pages with the highest bounce rates

Use of Hadoop Ecosystem tools: Many tools can be helpful to work on this

Flume can be used for stream data to HDFS

Pig also can be load the data from local/HDFS and refine it

Hive can be used to create view/ refine the data

Pig/Hive/impala also can be used for data analytics

Visual Analytics can be performed By integrating Tableau/QlickView/Excel 2013/Jasper Reports

Predictive Analytics can be performed By integrating R/Python/SAS/Spark

Use of Hadoop Ecosystem tools: Many tools can be helpful to work on this

Flume can be used for stream data to HDFS

Pig also can be load the data from local/HDFS and refine it

Hive can be used to create view/ refine the data

Pig/Hive/impala also can be used for data analytics

Visual Analytics can be performed By integrating Tableau/QlickView/Excel 2013/Jasper Reports

Predictive Analytics can be performed By integrating R/Python/SAS/Spark Hadoop Ecosystem – Open source tools: *Talend Studio is open source data integration tool and making big data easier for ETL and data integration developers, without having to learn how to code Map Reduce. *R/Python are open source software tools for doing advanced statistical/machine learning *Jasper Reports is open source visual analytics tool which is similar to Tableau

High Level Steps:

Upload the data in HDFS.

View & Refine the click stream data

Create tables and Views in Hive.

Create final table by joining omniture website log data to the CRM data (registered users) and CMS data (products)

Create final file for the analysis

Connect to tableau or any other reporting tool to visualize the data

You can also use the final file for doing different analysis using R/R-Studo

Analyse the data in Rstudio


Architecture :

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Big%20Data%20Analytics%20using%20Clickstream%20Data/media/architecture.png)
