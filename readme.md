# Exploration of Prosper Loan Data

## Dataset

Prosper is America’s first marketplace lending platform, with over $9 billion in funded loans. This data set contains 113,937 loans with 81 variables on each loan,  including loan amount, borrower rate (or interest rate), current loan  status, borrower income, borrower employment status, borrower credit  history, and the latest payment information.

This notebook will document my efforts to explore and clean an interesting dataset from the Prosper peer-to-peer lending platform, and to then make some visualizations to answer few questions. 


The original data can be found here: 

https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv. 

A variable dictionary concisely explaining the data can be found here: 

https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit?usp=sharing.


## Summery of Findings
There are many questions one could ask on this data, but in this exercise I focused on one question specifically: Is there a relationship between varibles that can help us figuring out the ultimate insight of loan will be completed of defaulted. Prosper loans pay pretty hefty interest rates to their creditors and defaulted loans make their business unprofitable. There is thus a significant financial incentive to accurately finding relatioships in varaibles specifically for Loan status. 

I explored it visually and programmatically, clean the data, explore the data with some visualisations and try to find the relationships/patterns in data.

#### Observations for Cleaning
Missing Values can be seen Income and few coulmns.
No need of redundant ListingKey and other unique identifier columns.
Data types should be more appropriate.
Variables have a wide variety of ranges, may be there are outliers.
My main interest is in Loan's outcome. List of possible outcomes need to be examined carefully to think a way to shorten it into only two categories.(Tidiness issue)

## Key Insights for Presentation

We have many statuses of Loans here in this dataset. It was tough to decide that what distinguishes completed loans from defaulted loans. Because there is no way to tell whether "current" loans will eventually default or completed, we cannot use them for our analysis. Nearly half of the dataset is not useful to us, as the loans are still outstanding.

Since we want to have a conservative approach in estimates but still want to retain data, let's assume all the"Cancelled", "Past due" and "chargedoff" loans are defaulted and FinalPaymentInProgress are completed.

Thus we'll be left with three categories only: "Current" ,"Completed" and "Defaulted".

33 percent is a huge slice of defaulters here. May be Prosper need to make changes in their loan recovery system. Since slice of Defaulted Loans is quite large we can explore other features that might help in predicting if a Loan would be defaulted in future.

Most of the loans were for Three years i.e 36 months. One year (12 months) loans are least popular.
Most of the borrowers are working full time. Only 1 percent borrowers declared themselves as not employed.
The distribution of APR is very interesting. It does not looks normal or even unimodal. One thing is quite evident that o.36 is the most frequent APR in whole dataframe.

A small peak centered at 0.1, a large peak centered at 0.2. There is also a fairly large peak centered 0.3. Additionally, The sharpest peak is at 0.36. Only very few loans have APR greater than 0.43.

Average Borrowere Rate is 20% but there are peers who are paying only 13% and 49% interest rate as well.That is a big spread with standard deviation of 0.08.
Distribution of Original Amount of Loan is right skewed. Most of the peers borrowed less than ten thousands but some peers borrowed much larger amounts and made the distributon right skewed. Average amount borrowed stands at 6341.

When plotted on log scale distribution turns out to be multimodel with very sharp peeks. Most of the stated monthly incomes are within 1t housand to 20 thousand dollars.

It can be seen clearly that Loans borrowed for 60 months were defaulted more that half percent of time. Loans taken for 12 months have the highest ratio of pay back. May be Prosper can emphasize more on 12 months loans because they are paid back most of the time.

Loans borrowed for 60 months were defaulted more that half percent of time. 

The distribution of the loan amount seems to be consistent between both status of loan(Completed,Defaulted).

36 months Loans are most popular among all employment statuses. Employed is the only category with sisgnificant number of peers whoe borrowed for 60 months and 12 months as well.

Self-employed, Other and not-available have the highest ratio of defaulters. While unexpectedly part-time workers completed their loans even better than full time and Employed categories.

Loan Amount and BorrowerAPR has a weak negative correlation. It makes sense that when one increases other decreases.

I can see that BorrowerRate and BorrowerAPR have a very strong positive correlation.

Monthly Income and Loan Amount have a weak positive correlation. Peers with higher incomes borrow larger amounts is a big statement but there is a tendency we can say.

Monthly Income and BorrowerRate have a very weak negative correlation. Almost negligable.
Looks like peers who borrowed more than 25000 and less than 35000 paidback most of the time and monthly income is a better indicator/preditor of being a defaulter or paying back the loan. Peers with higher monthly incomes have a higher rate of paying back the loans.

I already found a strong positive correlation between borrowerAPR and borrower Rate and now I extended my research to see the impact of the Amount borrowed. The multivariate exploration showed that the relationship between borrower APR and loan amount is positive and higher amonuts of loan almost invisible.

Relationship of loan rate and loan amount is not affected weather the loan is paidback or defaulted.Both have a weak negative correlation among them.

It looks like Term doesn't have effect on relationship of Loan rate and LoanAmount.

With income in bracket of 500-1000, sample of 100 obseravtions, point plot does not give any clear information but it looks like peers with higher income and lower borrow Rate complete their loans. It didnt revealed any new information.


```python

```
