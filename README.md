# Prosper Loan Data Exploration
## by (Aly Abdelkader)





## Introduction
>Our objective in this project is to perform an exploratory and explicative visual analysis of the prosper loan dataset. We aim at finding out what factors affect a BorrowerAPR and what affects the borrower’s interest rate (BorrowerRate). This dataset contains 113,937 loans with 81 variables on each loan, including loan amount, borrower rate (or interest rate), current loan status, borrower income, and more.
## Dataset
We started our analysis with  113,937 records and  81 variables. After the Wrangling process we ended up with 22570 record and 19 variables.

## Preliminary Wrangling

### Visual assessment
### Programmatic assessement
##### Quality issue #1: ListingCreationDate, ClosedDate are not in proper data 
##### Quality issue #2:  ListingCategory should contains the value directly eg: Business instead of 3. The column name should also be modify
##### Quality issue #3:  EmploymentStatus is not in proper data type 
##### Quality issue #4: The dataset contains too much null values
##### Tidiness Issue #1: The dataset contains 81 features many of which we are not interested by.
##### Tidiness Issue #2: The Credit score is splited in CreditScoreRangeUpper and CreditScoreRangeLower. From the search on the web, Credit score is among the important factors of a loan.
### Cleaning
#### Definition #1: Convert ListingCreationDate, ClosedDate to date time format. 
#### Definition #2 & #3: Modify ListingCategory column name and assign direct String object value, convert it and Employment Status to category data type
#### Definition #4: Join CreditScoreRangeLower and CreditScoreRangeUpper in one column  named CreditScore Average by taking the average of the two columns
#### Definition #5: Select features of interest
### Definition: Handle null data
### What is the structure of your dataset?
> The dataset originaly inluded 113,937 loans with 81 variables on each loan.
> After the wrangling process, we kept a  dataset that  inludes 22570 loans with 19 variables on each loan, including loan amount, borrower rate (or interest rate), current loan status, borrower income, and more. Most of these variables are numerics except for LoanStatus, ListingCreationDate, Term,ProsperRating (Alpha) and some other variables which are either String object or boolean.<br/> 
> The current status of a loan can be: Cancelled,  Chargedoff, Completed, Current, Defaulted, FinalPaymentInProgress, PastDue. The PastDue status will be accompanied by a delinquency bucket.

### What is/are the main feature(s) of interest in your dataset?

I am interested in finding out what factors affect the borrower’s interest rate (BorrowerRate) and the Borrower's Annual Percentage Rate (BorrowerAPR
) for the loan. So the main feature of interest are the Borrower's Annual Percentage Rate and the interest rate.

### What features in the dataset do you think will help support your investigation into your feature(s) of interest?

> In regard to a loan status and the interest rate, the following 17 features are going to be important and informative for our investigation. I expect that Borrower's Occupation, ProsperScore,ListingCategory and StatedMonthlyIncome will have the strongest effect. <br/>
<br/><b>CreditGrade:</b> The Credit rating that was assigned at the time the listing went live. Applicable for listings pre-2009 period and will only be populated for those listings.
<br/><br/><b>Term:</b> The length of the loan expressed in months.
<br/><br/><b>LoanStatus:</b> The current status of the loan: Cancelled,  Chargedoff, Completed, Current, Defaulted, FinalPaymentInProgress, PastDue. The PastDue status will be accompanied by a delinquency bucket.
<br/><br/><b>ListingCreationDate:</b> The date the listing was created. 
<br/><br/><b>BorrowerAPR:</b> The Borrower's Annual Percentage Rate (APR) for the loan.
<br/><br/><b>BorrowerRate:</b> The Borrower's interest rate for this loan. 
ProsperRating (Alpha):</b> The Prosper Rating assigned at the time the listing was created between AA - HR.  Applicable for loans originated after July 2009.
<br/><br/><b>ProsperScore:</b> A custom risk score built using historical Prosper data. The score ranges from 1-10, with 10 being the best, or lowest risk score.  Applicable for loans originated after July 2009.
<br/><br/><b>ListingCategory:</b> The category of the listing that the borrower selected when posting their listing: 0 - Not Available, 1 - Debt Consolidation, 2 - Home Improvement, 3 - Business, 4 - Personal Loan, 5 - Student Use, 6 - Auto, 7- Other, 8 - Baby&Adoption, 9 - Boat, 10 - Cosmetic Procedure, 11 - Engagement Ring, 12 - Green Loans, 13 - Household Expenses, 14 - Large Purchases, 15 - Medical/Dental, 16 - Motorcycle, 17 - RV, 18 - Taxes, 19 - Vacation, 20 - Wedding Loans
<br/><br/><b>BorrowerState:</b> The two letter abbreviation of the state of the address of the borrower at the time the Listing was created.
<br/><br/><b>Occupation:</b> The Occupation selected by the Borrower at the time they created the listing.
<br/><br/><b>EmploymentStatus:</b> The employment status of the borrower at the time they posted the listing.
<br/><br/><b>IsBorrowerHomeowner:</b> A Borrower will be classified as a homowner if they have a mortgage on their credit profile or provide documentation confirming they are a homeowner.
<br/><br/><b>DebtToIncomeRatio:</b> The debt to income ratio of the borrower at the time the credit profile was pulled. This value is Null if the debt to income ratio is not available. This value is capped at 10.01 (any debt to income ratio larger than 1000% will be returned as 1001%).
<br/><br/><b>StatedMonthlyIncome:</b> The monthly income the borrower stated at the time the listing was created.
<br/><br/><b>OnTimeProsperPayments:</b> Number of on time payments the borrower had made on Prosper loans at the time they created this listing. This value will be null if the borrower has no prior loans.
<br/><br/><b>Recommendations:</b> Number of recommendations the borrower had at the time the listing was created.
<br/><br/><b>MonthlyLoanPayment:</b> The scheduled monthly loan payment.
<br/><br/><b>LoanOriginalAmount:</b> The origination amount of the loan.
<br/><br/><b>CreditScoreAvg:</b> The aveage of CreditScoreRangeUpper and CreditScoreRangeLower.




# Summary of Findings

## Univariate Exploration

### Borrower's rate distribution

When investigating the BorrowerRate and the stated monthly income, the distribution looked skewed. So, When we took a closer look by reducing the size of the bins, we could see that the borrower's rate and Borrower's APR seem to be following a normal distribution with many values concentrated between 0.1 and 0.2. We can observe two spikes on the right which are probably outliers. 

### Borrower's APR distribution
Borrower's APR has a normal distribution with many value concentrated between 0.1 and 0.2

### Distribution of Stated Monthly Income
This distribution is a litle bit skewed on the right showing most of the borrowers make lest than 10000 a month.

### LoanOriginalAmount Distribution
LoanOriginalAmount Distribution had an unusual distribution. We performed a logarithmic transformation to see the distribution closer, which looks like a normal distribution.


## Bivariate Exploration

### Correlation Between Loan's Numeric features
From the heatmap plot, there is a strong positive correlation between BorrowerAPR and BorrowerRate, then between LoanOriginalAmount and MonthlyLoanPayment. On the other hand, the CreditScoreAVG negatively correlate with BorrowerAPR and BorrowerRate. This means the higher the borrower's credit score, the lower his loan's rate and annual percentage rate.

### Corellation between BorrowerAPR and IsBorrowerHomeowner
Homeowners have the smallest median. The shape of the distribution for homeowners (wide in the middle) indicates borrowers who own a house have an APR highly concentrated around the median.

###  Corellation between BorrowerRate and IsBorrowerHomeowner
This distribution is similar to that of BorrowerAPR and IsBorrowerHomeowner.

### Corellation between BorrowerAPR and ListingCategory
The median and the IQR vary depending on the purpose of the loan. From the graph, loan for Student Use seems to have the highest APR median.

### Corellation between BorrowerAPR and BorrowerState
A remarkable point here is that people in ALABAMA State (AL) have the highest APR median (0.24). This means the middle 50 % of people in this State pay more for a loan as compared to the 50 % of people in other states. On the other hand, Rhode Island State (RI) has the widest IQR and has the highest incurred cost of a loan as compared to all other States. We can also notice alot of outliers for the FL, NJ, NY, WI states.


## Multivariate Exploration

### Relationship between BorrowerRate, StatedMonthlyIncome and IsBorrowerHomeowner

We can observe from this plotting that whether a borrower is a homeowner or not, this does not affect the BorrowerRate and BorrowerAPR. However, we can see that people with homes tend to have a high monthly income.

### Credit grade and ListingCategory related to BorrowerAPR and CreditScoreAvg
Here, we can observe some interesting facts about people with credit grade AA. People with this credit grade borrowing money for Auto mobile purpose tend to have lower APR, consequently induring lower annual cost for loans.

### EmploymentStatus and ListingCategory influence on BorrowerAPR
From this plot, we can see that part-timer in many listing category seems to have higher APR (AUto, Student use, Home improvement, Debt consolidation).


> Our analysis consisted to performe an exploratory and explicative visual analysis of the prosper loan dataset and  find out what factors affect a BorrowerAPR and  borrower’s interest rate (BorrowerRate). 
 Through this exploration, we discovered that most of the borrowers come from The California State, and we also find out that, the higher the Credit Score, the lower  the  BorrowerAPR and BorrowerRate. Also, retired people tend to have low APR and low rates, consequently, enduring lower costs on loans compared to part-timers.
 Univariate Exploration


## Key Insights for Presentation

In our presentation, we will focus on showing how the CreditScore varies with the borrower's annual percentage and loan rate. We will also focus on showing how the majority of borrowers are from California state. Finally, we will end by showing the BorrowerAPR, BorrowerRAte relationship with the Listing Category. 