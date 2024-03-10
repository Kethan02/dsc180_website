# Creating a more holistic Credit Score for Consumers
Lakshmikethan Bethamcharla, Darren Jiang, Sheng Zhou, Victor Thai
<br>
Section: B18, Mentors: Brian Duke & Berk Ustun
<br><br>

### **Why a New Credit Score**<br>
A credit score is a numerical rating that represents the perceived ability of a person or organizaton to fulfill their financial commitments. The current scoring system in place is one that has been established and in use for a great number of years now, without many changes. Many new systems and additional data on financial behavior are now in place that allow for greater granularity of a consumer's overall financial behavior even without a credit score. The current credit scoring system today primarily relies on a consumer’s previous credit history, leaving those that are just starting out with little to no credit history to be unable to qualify for any loans. With the rise of banking transactions and the use of personal transaction accounts, we aim to use this data to further extrapolate a consumer's behavior.
<br><br>

### **Introduction**<br>
Throughout this two-quarter long project, we aim to create a system that encapsulates all user behavior in a credit score using the provided banking transactions from Prism Data. Working alongside Prism Data, we build off of current methods they have in place and utilize abstract methods that one would consider "outside the box". By using new ideas that may not have been addressed before, this would benefit our overall analysis and predictive ability on a consumer's financial behavior. 

Add information about analysis methods used and model methods...

Add little bit on overall outputs...
<br><br>

### **Data**<br>
Our dataset is obtained from our industry partner, Prism Data. Prism data has given us samples of consumer inflow, outflow, consumer account data, along with credit application information to use for our analysis. All data has been omitted of personal identifiable information so no privacy is breached in our analysis and modeling.

Info on data and features...

Info on feature names and their meaning / relevance to analysis...
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

#### TF-IDF<br>

![Boxplots of Most Significant Features](boxplots_image.jpg)

<br><br>

### **Models**<br>

#### Logisitic Regression<br>

#### Neural Net<br>
<br><br>

### **Results**<br>

| Memo Classification Model | Accuracy |
| --- | --- |
| BERT | 88% |
| Logistic Regression with TF-IDF | 97% |
| Decision Tree Classifier with TF-IDF | 98% |


| Risk Assessment Model | ROC-AUC Score |
| --- | --- |
| Logistic Regression | 0.57778 |
| Sequential NN | 0.78500 |

<br><br>

### **Conclusion / Next steps**<br>
<br>

