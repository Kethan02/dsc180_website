# Creating a more holistic Credit Score for Consumers
Lakshmikethan Bethamcharla, Darren Jiang, Sheng Zhou, Victor Thai
<br>
Section: B18, Mentors: Brian Duke & Berk Ustun
<br><br>

### **Why a New Credit Score**<br>
A credit score is a numerical rating that represents the perceived ability of a person or organization to fulfill their financial commitments. The current scoring system in place is one that has been established and in use for a great number of years now, without many changes. Many new systems and additional data on financial behavior are now in place that allow for greater granularity of a consumer's overall financial behavior even without a credit score. The current credit scoring system today primarily relies on a consumer’s previous credit history, leaving those that are just starting out with little to no credit history to be unable to qualify for any loans. With the rise of banking transactions and the use of personal transaction accounts, we aim to use this data to further extrapolate a consumer's behavior.
<br><br>

### **Introduction**<br>
Our project's goal is to create a credit score for individuals. We split the work into two parts: categorizing transactions and building a risk prediction model. First, we cleaned up messy transaction descriptions and used methods such as BERT to accurately classify transactions into categories like groceries or bills. Next, we created features from people's transaction history, account balances, and estimated income. We then built models like linear regression and neural networks to analyze these features and predict someone's risk of defaulting on a loan.
<br><br>

### **Data**<br>
We have four datasets: inflows (money going into accounts), outflows (money going out of accounts), accounts (details on account types and balances), and consumer (information on loan applications and defaults). The inflows dataset has around 513,000 transactions and the outflows dataset has around 1.3 million transactions. The accounts dataset contains information on nearly 4,700 unique accounts. The consumer dataset has details on almost 2,000 consumers and whether they defaulted on their first loan payment. Your goal is to develop a better credit assessment system using the banking records, transaction data, and account values in these datasets.
<br><br>

### **Feature Creation and Selection**<br>

| Feature Name | Description |
| --- | --- |
| balance_summary_stats | min, max, and standard dev of balance a consumer has in any of their accounts |
| cumulative weighted default monthly avg | get sum of average weighted value of overdraft per month |
| category_summary_stats | mean, median, min, and max of spending in each category throughout dataset |
| disposable_income | amount remaining after combining all inflow and outflow transactions |
| avg_monthly_spending | average amount of money spent in a month |
| num_avg_monthly_purchases | average number of purchases in a month |
| avg_monthly_cat_spending | average amount of money spent in a month for each category |
| avg_monthly_cat_count | average amount of purchases in a month for each category |
| num_savings_transfer | number of times someone has pulled from savings account |
| insufficient_bal | boolean for whether a consumer has an account that is <= 0 at time of evaluation |
| num_accounts | total number of accounts a consumer has |
| monthly_cat_slope | slope of spending for each category |
| non_essential_ratio | proportion of spending done in non-essential vs essential categories |
| stand_balance_slope | slope of monthly balance |
| positive remaining ratio | amount of months where cash flow is positive out of all months in dataset for each consumer |
| credit ratio | maximum number of consecutive months in which a consumer pays of a loan |
| prop spending | percentage of total consumer spending for each category |
| overdraft freq | boolean value of users with more than 1 monthly overdraft transaction |


We  created over 200 distinct input features like balance summaries, category spending, disposable income, monthly averages, and spending ratios. Creating monthly features required splitting the data by year and month and using the median. We filtered to the most effective features for the final model to avoid overfitting. 

![Boxplots of Most Significant Features](boxplot1.png)

<br><br>

### **Models**<br>


#### Logisitic Regression<br>
We created a Logistic Regression model to serve as a baseline. we created a logistic regression classifier using standard scikit-learn functions. The initial maximum number of epochs was set to 100, but increasing it to 1000 did not significantly improve the model's performance.

#### Neural Net<br>

We trained a sequential neural network initially for 500 epochs with batch size 8, then reduced to 200 epochs with batch size 64 for faster training. The neural network has 5 hidden layers with sizes 12, 24, 24, 12, and 6. It takes in 40 features and outputs the probability of default through a sigmoid function. We optimized the threshold by testing different values on the validation set to maximize the ROC-AUC score. The model with the lowest validation loss during training is used as the final model.

![Boxplots of Most Significant Features](Neural.png)
<br><br>

### **Results**<br>

For classifying memos by category of credit card transactions, we utilized our cleaned data
with three different models to see which could perform the best.

| Memo Classification Model | Accuracy |
| --- | --- |
| BERT | 88% |
| Logistic Regression with TF-IDF | 97% |
| Decision Tree Classifier with TF-IDF | 98% |

When looking at the results for the risk-assessment models:

| Risk Assessment Model | ROC-AUC Score |
| --- | --- |
| Logistic Regression | 0.57778 |
| Sequential NN | 0.78500 |

<br><br>

### **Conclusion / Next steps**<br>
We used both a logistic regression model and a sequential neural network model to determine the effectiveness of your features. The neural network provided more accurate results but took longer to train. The ROC-AUC score measures how well the model can distinguish between default and non-default cases. We created additional features like category spending summaries to give the models more insight into consumer behavior and risk. The next step is to filter down to the most impactful features to create the final credit scoring model.
<br>
