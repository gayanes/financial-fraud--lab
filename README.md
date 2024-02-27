# Financial Fraud Lab

The relationship between a bank and their customers relies on the trust that any unauthorized or fraudulent activity is caught quickly and handled accordingly. By using a dataset of historic fraudulent activity and creating an ensemble classifier, the goal of this project is to assess whether a fraudulent transaction has occured. 

## EDA and Pre-Processing

1. Which insights did you gain from your EDA?


The histograms of the quantitative columns show that the data is right skewed, with the majority of balances and transactions being of a smaller amount of currency, which makes sense as most individuals' transactions and balances will be for smaller amounts.

The amount of fraudulent transactions is very small and only happens for transfer and withdrawal (cash_out) activities, implying no fraudulent activity occurs for debit, payment, or cash_in (deposit) transactions. This is surprising to me for two reasons: (1) this data set only considers an action fraud if money was taken out of a bank account maliciously, but (2) debits aren't considered for fraud, despite the potential for a malicious debit activity.

Initially it seems like the payment transaction type doesn't have data for oldbalanceDest and newbalanceDest, but upon further inspection,  all the data for payment is zero and doesn't easily appear on the box plot.

When plotting the blalances against the transaction amounts, the scatterplots show that fraudulent transactions have fairly strong, positive correlations using all of the predictor variables and non-fraudulent transactions have very weak correlations.


2. How did you determine which columns to drop or keep? If your EDA
informed this process, explain which insights you used to determine
which columns were not needed.


I knew the nameOrig and nameDest columns would not be relevant for testing fraud detection because repeated fraudulent activities using the same accounts would be much easier to spot, and that account can be shut down. And since the step column would be a measure of time and we live in a global society, it does not seem like time would heavily affect the frequency or time of fraudulent activity. I also dropped the isFlaggedFraud column as that model marked none of the data as fraud.

Initially it seemed like the initial and final balance columns wouldn't be useful since they were so difficult to visualize. But the scatterplots showed that the fraudulent data  had strong correlations using the balance columns.



## Modeling

3. Which hyperparameter tuning strategy did you use? Grid-search or
random-search? Why?

4. How did your model's performance change after discovering optimal
hyperparameters?

5. What was your final F1 Score?