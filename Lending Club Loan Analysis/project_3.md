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

    ![](media/9188d0700ac41833208792c70d4a775a.png)

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

    ![](media/1ae2694802e65cbcebffa631a99f2652.png)

Ques :

Total Loan issuance by yearly & quarterly and calculate growth rate by quarter
on quarter and year on year

![](media/5273d099273bbeead4f9fcbd12605125.png)

Analysis;

(Integration with ms excel as explained in project 1)

![](media/bb48d04a4af694034b755e12cde563b9.png)

![](media/72ee67015111460c7f6b95ded88386e2.png)

![](media/eaf7c880948c185d590fcf4672ac135d.png)

We can see the quarter view of total loan issue above .

Yearly performance :

Creating a view for year analysis .

![](media/ded92b1c10a573051d8899892dac7049.png)

Analysis :

![](media/8c0472de64eed341a69b4bee8adb2ef5.png)

![](media/44710a74c4eb34aeaef9539911b94ee8.png)

![](media/2caee83110b5a12d6a76727526ddf757.png)

Yearly loan issued analysis .

Ques 2 :Percentage of loans based on reported loan purpose.

![](media/5bdd0dbd0fae956f9e353fc0afa88cc1.png)

Analysis :

![](media/6276179f458c45df7e6dde542458c70e.png)

![](media/728ecadcd5fb56bd836be89b00ee03de.png)

![](media/07642d457a0d22f12919117d15f854a1.png)

![](media/47adf3028ce385a7204ef207c1920c01.png)

We can see dept\_consolidation as the major purpose for loan .

**Loan Issuance by state**

Creating the requisite table

![](media/e6efb907857cd96baf909c1f268d72b8.png)

![](media/5b44fa2cab95d4bc2812168848e0c64a.png)

![](media/87d50510e74f5826940ea41f5baab082.png)

![](media/c3774933568e2225e041f9bb7be0f625.png)

4 .Find the last quarter average interest rates by different term loans and
overall

Note last quarter for available data is Q3-2015 as created in lce\_refined

![](media/524d010704cfc38ffaa52329f5c12fc0.png)

![](media/01af25d5b2f3b10cdf2d849ad28c37e2.png)

Overall avg for last quarter :

![](media/aa1f926b11f35055c37e8e59114ef8c9.png)

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

![](media/0fd17d8a4d1c093b8e065e8149f467f4.png)

Analysis :

![](media/3ad7f7788c2a661329ad4823ea4606af.png)

![](media/602c37c569de65028aa6ede58f9845cc.png)

![](media/97a61a61a56448070d1e53d1add588ae.png)

Calculation of return loan grade by percentage .

Ques : 6 Find the historical average interest rates by loan terms and loan
grades (also for overall)

![](media/83dfc36843119837f48b2ab03ac35476.png)

Analysis:

![](media/f09654700b6dd5c716f3f8282981b468.png)

![](media/5e023de70fd7d16db519f704f22f67f0.png)

![](media/2b90850869624ea0d8fe313566e4e2ee.png)

Avg interest by grade .

Creating a new view for more analysis :

![](media/3becd6cb4a1640b775a6bb5ac8a3473c.png)

Analysis :

![](media/5c200491380022db36c6dfc544f84ff3.png)

![](media/695573e01994203b64a82e7569adf1dd.png)

For grade as A and 36 months loan term,avg interest rate over different year

![](media/7f7e504187b47f60354e6557a447866b.png)

Interest rate over year for all the grade and all loan term

Ques :7 What is percentage of loans by different loan grades by each year and
loan term level (also for overall)

![](media/7993b4820606c25e58e6b1a313ef7887.png)

Analysis :

![](media/260168a32f4055a0e6d8f857941c814c.png)

![](media/9ac02be6d6e37b7635ecb5cfa81e79cc.png)

![](media/ce153f7efd37e17c350a6aa442db596d.png)

![](media/d67d002e1a38bf02bfe629d5c1f4506a.png)

Grade percentage for 36 months loan term over different year

![](media/653f0138191f2ccf348413bcb62e995e.png)

Grade percentage for 60 months loan term over different year

![](media/4b4968969d7022da1108f9b408e4df7d.png)

Grade percentage for overall term over different year .

Ques What is the loan performance details by different loan grades and overall

![](media/be27fb322da4672aa7a4d40a63fa21c6.png)

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

![](media/0b8a7f4b9435f875ef06250a4d3dcedb.png)

![](media/497893a86584d0b0c890d1781037608a.png)

![](media/a66a8f18ce7f4d22cfffe47fcf843bf5.png)

![](media/1300beb383f7046d4e038875b0d0b7f6.png)

Comparison of terms such as
avg\_return,avg,charged\_off,current1,interest\_pay,late fees , principal etc
for grade **C** between year 2013 and 2014 .

![](media/dec49fc586decd598ffd83d7758634ec.png)

Loan performance for all year and grade as A in tabular form .

Ques : **What is loan status migration over 9 months**

![](media/68ed20847d03304823f05534716b20a0.png)

Analysis :

![](media/bab1de1887c471572c442c8aa9d3034d.png)

![](media/ccbcf165d9bc56cae6b998cd0c3c1ab3.png)

![](media/4f39d881cb08c8532c5c83d7ffbb45ce.png)

\-----------------------------------end------------------------------------------------------------------------

Link of excel 2013 file :
https://drive.google.com/open?id=0BxjYrCpAmIoqS2lMajRsNy1mVEE
