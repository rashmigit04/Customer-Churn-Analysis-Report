## INTRODUCTION
Churn analysis is a process that businesses use to evaluate the rate at which they lose customers, and to find ways to reduce that rate. It's also known as customer attrition, and can be minimized by assessing the product or service being offered, and how people are using it.
 
High attrition rates can have detrimental effects on a bank's profitability, reputation, and overall success, making it essential for banks to employ strategies that not only attract new customers but also retain and satisfy their existing client base. By understanding why customers are leaving, businesses can take steps to improve their offerings and retain more customers in the long run.

The tool I used for this case study is Microsoft Power BI.

## PREPARATION
In preparation, I made clear what the objectives were, extracted the data from Kaggle, cleaned and transformed it to ensure accurate analysis, and loaded it into Microsoft Power BI for modeling and analysis.

## OBJECTIVES
The objective of this analysis is to discover various factors contributing to increased customer churn rate at the bank, and provide the business users with these insights which they can use to make informed decisions and strategies on how to improve customer retention and reduce churn rate.

Customer Segmentation: Analyze the data based on customer characteristics such as gender, country, and age range to identify different customer segments.

Product Portfolio Management: Analyze the "Products Number" column to understand customers' preferences and purchase behavior.

Credit Card Management: Assess the "Credit Card Status" column to monitor the usage and status of credit cards. Identify customers with active credit cards and those who may need assistance or incentives to increase credit card usage.

Customer Retention: Analyze the "Activeness" column and the "Churn Status" column to understand customer churn patterns.

Salary Range Analysis: Evaluate the “Salary Range” columns to gain insights into the income distribution of customers.

## RAW DATA
The dataset for the project has the following columns:

customer_id, 
credit_score, 
country, 
gender, 
age, 
tenure, 
balance, 
product_number, 
credit_card, 
active_member, 
estimated_salary, 
churn

## DATA PREPARATION
Imported the dataset into Power BI and transformed it in Power query as follows:

Renamed the data from Bank Customer Churn Prediction to Customer Data for clarity.
Eliminated the auto-generated header, by promoting the first row of my data to become the header.
Removed irrelevant columns like estimated_salary.

## DATA CATEGORIZATION AND GROUPING
To clearly label the product_number column, I utilized the replace values option. Since it indicates the account type a customer owns, I replaced product 1,2,3, and 4, with Product 1, Product 2, Product 3, and Product 4 respectively and deleted the original column.

There was a wide range between the minimum and maximum values for the age, credit_score, balance columns. So, I grouped each of them using conditional column function.

Columns like churn, active_member and credit_card had boolean datatypes of 1 and 0, essentially representing true or false. So. I formatted them by using the replace values option to change them to more intuitive data types.
For active_member column, 0 = Not Active, 1 = Active
For churn column, 0 = Not Churned, 1 = Churned
For credit_card column, 0 = No, 1 = Yes

## DATA TRANFORMATION
Created Queries to organize data for better analysis and reporting.

 Renamed the columns where needed, to make them meaningful enough.
      active_member = Activity Status, 
      customer_id = Customer ID, 
      churn = Churn Status, 
      balance = Account Balance, 
      products_number = Product Type

## DATA VISUALIZATION
Created few DAX measures:

Customers(Number of customers) - Total Customers
Customers = COUNT('Customer Data’[customer ID])
Customers Churned - Count of Customers "Churned"
Customers Lost = CALCULATE(COUNT('Customer Data’[Churn Status]), 'Customer Data’ 
[Churn Status] = “Churned") 
Churn Rate (%) - Customers/ Customer Churned
Churn Rate = 'Customer Data'[Customers Lost]/'Customer Data'[Customers] 

Measures were:
Customers: 10K
Customers Lost: 2037
Churn Rate: 20.4%

## CONCLUSION
1. People collecting extremely high salaries are not active among those that left.
2. According to gender analysis, females even among middle-aged people (aged 41-50 years) tend to stop business with the bank.
3. People with Product 1 stop business with the bank. This could be caused by customers not getting enough value from the products purchased.
4. Countries France and Germany have the highest rate of inactivity.

## RECOMMENDATIONS
So based on the above findings, the following recommendations are suggested:

1. The stakeholders could consider creating products that target seniors close to their early retirement.
2. An incentive program could be considered for customers who have maintained longer relationships with the bank.
3. Customers with limited product adoption should be given more attention and develop strategies to improve their financial well-being. Offer personalized financial guidance, product recommendations, or incentives to increase engagement and loyalty.
4. In the same way, an exclusive package such as travel and vacation packages, subsidized investment portfolio, etc., could be considered for the customers in the >200k account balance group, to reduce the rate at which they leave the Bank.
5. The business needs to address why there is a 100% Churn rate for Product 2 customers with an account balance of 1k-10k and how to get them back in business.
6. Based on gender and age information, this should be used to segment customers and develop targeted marketing campaigns for the specific age group.
7. Tailor messaging, product offerings, and promotions to the specified countries to enhance customer engagement and drive revenue growth.
   

In Summary, age group of 51–60, people with low credit scores and those with high account balances (>200k) are most likely to churn. The bank should consider the recommendations above and other effective strategies that can address the findings, to better customer retention and reduce churn rate.



In this Power BI analysis, I transformed raw data into a report that identified key factors contributing to customer churn at the bank. With this report, stakeholders can manage the churn situation for salaried customers by focusing on these key factors and evaluating the results of any changes made periodically.

## THANK YOU

# CONTRIBUTOR:
Rashmi Singh









