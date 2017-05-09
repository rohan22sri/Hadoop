Project3: Lending club Loan Analysis

(Analysis excel sheet is attached at last of page)

1.  Creating sub-table for all the 4 loan issued and combing them into final
    table LCE .

   ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image1.png)

    create external table lca

    (

    id int ,

    member\_id int ,

    loan\_amnt smallint ,

    funded\_amnt smallint ,

    funded\_amnt\_inv smallint ,

    term string ,

    int\_rate string ,

    installment float ,

    grade string ,

    sub\_grade string ,

    emp\_title string ,

    emp\_length string ,

    home\_ownership string ,

    annual\_inc smallint ,

    verification\_status string ,

    issue\_d string ,

    loan\_status string ,

    pymnt\_plan string ,

    url string ,

    desc string ,

    purpose string ,

    title string ,

    zip\_code string ,

    addr\_state string ,

    dti bigint ,

    delinq\_2yrs bigint ,

    earliest\_cr\_line string ,

    inq\_last\_6mths tinyint ,

    mths\_since\_last\_delinq string ,

    mths\_since\_last\_record string ,

    open\_acc tinyint ,

    pub\_rec bigint ,

    revol\_bal smallint ,

    revol\_util string ,

    total\_acc tinyint ,

    initial\_list\_status string ,

    out\_prncp float ,

    out\_prncp\_inv float ,

    total\_pymnt float ,

    total\_pymnt\_inv float ,

    total\_rec\_prncp float ,

    total\_rec\_int float ,

    total\_rec\_late\_fee float ,

    recoveries float ,

    collection\_recovery\_fee float ,

    last\_pymnt\_d string ,

    last\_pymnt\_amnt float ,

    next\_pymnt\_d string ,

    last\_credit\_pull\_d string ,

    collections\_12\_mths\_ex\_med bigint ,

    mths\_since\_last\_major\_derog string ,

    policy\_code bigint ,

    application\_type string ,

    annual\_inc\_joint string ,

    dti\_joint string ,

    verification\_status\_joint string ,

    acc\_now\_delinq bigint ,

    tot\_coll\_amt string ,

    tot\_cur\_bal string ,

    open\_acc\_6m string ,

    open\_il\_6m string ,

    open\_il\_12m string ,

    open\_il\_24m string ,

    mths\_since\_rcnt\_il string ,

    total\_bal\_il string ,

    il\_util string ,

    open\_rv\_12m string ,

    open\_rv\_24m string ,

    max\_bal\_bc string ,

    all\_util string ,

    total\_credit\_rv string ,

    inq\_fi string ,

    total\_fi\_tl string ,

    inq\_last\_12m string

    )

    ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'

    WITH SERDEPROPERTIES (

    "separatorChar" = ",",

    "quoteChar" = "\\"")

    location '/user/cloudera/project\_3/LoanStats3a'

    tblproperties ("skip.header.line.count"="2");

    Similarly lcb, lcc and lcd table are created .

    2 .Create lce which is union of table lca , lcb, lcc, lcd .

    ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image2.png)

    3 . creating a new view lce\_refined and including a new column (ie deciding
    quarter by seeing moths on issue\_d column)

    create view lce\_refined as

    select \*,

    case

    when substr(issue\_d,1,3) in ('Jan','Feb','Mar')

    then 'Q1'

    when substr(issue\_d,1,3) in ('Apr','May','Jun')

    then 'Q2'

    when substr(issue\_d,1,3) in ('Jul','Aug','Sep')

    then 'Q3'

    when substr(issue\_d,1,3) in ('Oct','Nov','Dec')

    then 'Q4'

    end as q

    from lce

    where issue\_d !='Null'

    ;

     ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image3.png)

Ques :

Total Loan issuance by yearly & quarterly and calculate growth rate by quarter
on quarter and year on year

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image4.png)

Analysis;

(Integration with ms excel as explained in project 1)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image5.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image6.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image7.png)

We can see the quarter view of total loan issue above .

Yearly performance :

Creating a view for year analysis .

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image8.png)

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image9.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image10.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image11.png)

Yearly loan issued analysis .

Ques 2 :Percentage of loans based on reported loan purpose.

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image12.png)

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image13.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image14.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image15.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image16.png)

We can see dept\_consolidation as the major purpose for loan .

**Loan Issuance by state**

Creating the requisite table

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image17.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image18.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image19.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image20.png)

4 .Find the last quarter average interest rates by different term loans and
overall

Note last quarter for available data is Q3-2015 as created in lce\_refined

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image21.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image22.png)

Overall avg for last quarter :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image23.png)

Ques 5 : Find the historical returns by loan grade(Historical performance by
grade for all issued loans) and overall

drop view return\_loan\_grade;

create view return\_loan\_grade as

select grade, power((1+(sum(((total\_rec\_int + total\_rec\_late\_fee -
recoveries -
collection\_recovery\_fee)/loan\_amnt)\*loan\_amnt)/sum(loan\_amnt))),12)-1 as
cal

from lce\_refined

group by grade;

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image24.png)

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image25.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image26.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image27.png)

Calculation of return loan grade by percentage .

Ques : 6 Find the historical average interest rates by loan terms and loan
grades (also for overall)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image28.png)

Analysis:

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image29.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image30.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image31.png)

Avg interest by grade .

Creating a new view for more analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image32.png)

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image33.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image34.png)

For grade as A and 36 months loan term,avg interest rate over different year

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image35.png)

Interest rate over year for all the grade and all loan term

Ques :7 What is percentage of loans by different loan grades by each year and
loan term level (also for overall)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image36.png)

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image37.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image38.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image39.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image40.png)

Grade percentage for 36 months loan term over different year

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image41.png)

Grade percentage for 60 months loan term over different year

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image42.png)

Grade percentage for overall term over different year .

Ques What is the loan performance details by different loan grades and overall

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image43.png)

drop view loan\_performance\_detail ;

create view loan\_performance\_detail as

select grade,substr(issue\_d,5,8) yr , sum(funded\_amnt) total\_issued ,
sum(total\_pymnt) fully\_paid , sum(out\_prncp) current1 ,
sum(total\_rec\_late\_fee) late1 ,sum(recoveries + collection\_recovery\_fee) as
charged\_off ,

sum(total\_rec\_prncp) principal , sum(total\_rec\_int) interest\_pay ,
avg(substr(int\_rate,1,5)) as avg1 , power((1+(sum(((total\_rec\_int +
total\_rec\_late\_fee + recoveries -
collection\_recovery\_fee)/funded\_amnt)\*funded\_amnt)/sum(funded\_amnt))),12)-1
avg\_return

from lce\_refined

group by grade,substr(issue\_d,5,8);

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image44.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image45.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image46.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image47.png)

Comparison of terms such as
avg\_return,avg,charged\_off,current1,interest\_pay,late fees , principal etc
for grade **C** between year 2013 and 2014 .

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image48.png)

Loan performance for all year and grade as A in tabular form .

Ques : **What is loan status migration over 9 months**

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image49.png)

Analysis :

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image50.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image51.png)

 ![ScreenShot]( https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/image52.png)

\-----------------------------------end------------------------------------------------------------------------

Link of excel 2013 file :
https://drive.google.com/open?id=0BxjYrCpAmIoqS2lMajRsNy1mVEE
