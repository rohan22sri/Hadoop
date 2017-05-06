Project5: Bigdata Analytics in retail

1.  Create database project\_5;

2.  Use project\_5;

3.  [./media/image1.png](./media/image1.png)

4 .

![](media/ca26ea33e3f77ff8340a20f56063af24.png)

5 .

![](media/f66e2a78bcde84867c3337cf95bce9a7.png)

6 .

![](media/b17519a6ede066f1f614b418988136b3.png)

7 .

![](media/d62b17bab4ab4455d197981e834bcfad.png)

8 .

![](media/e8a09a4e929cbbc38aaa2166f594917c.png)

9 .

![](media/6d9caca7d67f1c52fb114eafa2a3a01c.png)

10 .

![](media/e6939bc0c26764147b7188dcb3eb0438.png)

11 . Create a new table category which categories products in different category
.

I have manually categorised each product into category . This will help me in
recommending products to other .

![](media/055ec07acf6f51f72212aeb43f289e27.png)

12.

![](media/6a88f3638ed88a3c7cd740ce89960622.png)

13 .

![](media/1664098f27ba1dab604f4e77a68dd5af.png)

14 .

![](media/93e19408813ea17aa75c6e377cc8e2df.png)

15 . custall2 is my final view on which analysis will be done .

![](media/84b94bcce276c4879800f6e9fb000d31.png)

**Integration with ms excel 2013**

Steps has been explained in Project 1 .

![](media/bb50495db218f7048687c678bc899246.png)

Ques : Analyse spending capacity and pattern of customer

Here we have analysed spending capacity of customer by calculating total amount
spent by a customer’s email id . We see the graph in decreasing order my amount
spent .

![](media/740c58e4de40bd2867f65fb6a8c6f3cb.png)

Pattern of customer on all the 3 days :

We have analysed the 3 days pattern of a customer shopping by choosing the
customer name in filter .

![](media/47a9b0b4f4761a32cbb90ecf27ca308a.png)

Ques 2 : Choose potential customers that will spend

The customer purchasing the maximum products seems to be the most active user
and hence we can call it as potential customer .

![](media/3b57e98a3e0256becc4a1beb91a1ed3d.png)

Ques 3 : Identify product recommendations for customers

For this we will create a new table ‘recomm’ in which we will choose the
customer email id and will find related products purchased by customer .The
related products will be chosen from table ‘category’ . Now table ‘recomm’ will
be my final table which will let me know the suggested products for that
particular email id .

![](media/884fefb4c06c18e2a03d911bb8e34c3a.png)

Importing column from table ‘recomm’ :

![](media/9871b32b6af5e9ecf478ae4644a6ace8.png)

The suggested product for the particular email id is as shown below :

![](media/c351a08c3b93e2071c81304b20174bb1.png)

![](media/3c45fd3bfe750d088137d858b54cfc22.png)

Choose the email id for whom you want to suggest product in filter .The graph
shows what product can be suggested to these email id .

![](media/8017ec7a9832809c4a52386b8b5c5a56.png)

A bar representation of the same :

![](media/d56456c800612b40682e96359a59c205.png)

Excel file link :

https://drive.google.com/open?id=0BxjYrCpAmIoqR3JQdk0tbk9hdE0
