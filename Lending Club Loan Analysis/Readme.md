**Project: Bank Loan Analysis**

**About Company:**

Lending Club (LC) is one of the largest online credit marketplace, facilitating
personal loans, business loans, and financing for elective medical procedures.
Borrowers access lower interest rate loans through a fast and easy online or
mobile interface. Investors provide the capital to enable many of the loans in
exchange for earning interest. LC operate fully online with no branch
infrastructure, and use technology to lower cost and deliver an amazing
experience. LC pass the cost savings to borrowers in the form of lower rates and
investors in the form of attractive returns. LC is transforming the banking
system into a frictionless, transparent and highly efficient online marketplace,
helping people achieve their financial goals everyday.

**How LC Operates:**

As a personal loan or business loan borrower, you can get an instant quote in
minutes with no impact to your credit score. Once you select an offer, you can
watch as funds are committed by investors who are choosing to invest in you and
your success.

If you’re investing, you can open an account in minutes and build a portfolio
of hundreds or thousands of loans made to quality borrowers. You’ll receive
monthly payments of principal and interest, which you can withdraw or reinvest.

If you’re looking for medical financing, you can apply online or through our
network of more than 10,000 providers across the country.

No matter what kind of loan you’re interested in, everything is done online, so
the whole process is fast, convenient and private.

All loans facilitated by Lending Club are issued by a bank and subject to the
same consumer protection, fair lending, and disclosure requirements as any other
bank loan.

**Business Objective:**

**The objective of this analysis to understand loans performance in different
dimensions. In order to understand loans performance the company would like to
do following analysis using available data.**

**Total Loan issuance by yearly & quarterly and calculate growth rate by
quarter on quarter and year on year**

**Percentage of loans based on reported loan purpose. (Note:** Loan purpose
describes the reported intent of borrowers from the most recent completed
quarter and may not reflect actual usage. Investors should rely on loan grades
rather than loan purpose)

**Loan Issuance by state – classify the states based on loan issuance by \$50+
MM, \$25-50 MM, \$10-25 MM and \$0-10 MM**

**Find the last quarter average interest rates by different term loans and
overall**

**Find the historical returns by loan grade(Historical performance by grade for
all issued loans) and overall**

**Find the historical average interest rates by loan terms and loan grades
(also for overall)**

**What is percentage of loans by different loan grades by each year and loan
term level (also for overall)**

**What is the loan performance details by different loan grades and overall**

**Find Net Annualized returns by vintage by different loan grades and different
loan terms (also for overall**

**What is loan status migration over 9 months (Net Charge offs: 120+days
delinquency)**

**Input Data Loans Data(4 Files):** These files contain complete loan data for
all loans issued through the time period stated, including the current loan
status (Current, Late, Fully Paid, etc.) and latest payment information. The
file containing loan data through the "present" contains complete loan data for
all loans issued through the previous completed calendar quarter.

**Declined Loan Data(3 Files):** These files contain the list and details of all
loan applications that did not meet Lending Club's credit underwriting policy.

**Detailed Data Dictionary:** The Data Dictionary includes definitions for all
the data attributes included in the Historical data file and the In Funding data
file. **Data Download Link .**

**Expected outcome:**

As per basic expectations, you need to come up with the analysis as per the
business objective. Please refer analysis samples to get understand the
questions

**(Optional)** The data is very rich. You can come with many analysis related to

Loans performance

Understanding on rejection of loans

Investor performance

Delinquency rates by each quarter or year

Prepayment rates by each quarter or year

Cumulative charge offs

**High Level Steps:**

Upload the data in HDFS.

Optional: create tables in sql server/mysql and use sqoop to transfer files
from sql server/my sql to HDFS

View & Refine the data

Create tables and Views in Hive.

Create final tables for loans and rejection loans by appending data from
individual files

Perform the analysis using Hive/Pig/Impala to solve the business questions

Optional: Connect to tableau or any other reporting tool to visualize the data

Optional: You can also use the final file for doing different analysis using
R/R-Studo

Optional: Analyse the data in Rstudio.

![ScreenShot](https://github.com/rohan22sri/Hadoop/blob/master/Lending%20Club%20Loan%20Analysis/media/architecture.png)
