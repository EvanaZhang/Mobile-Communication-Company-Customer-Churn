# Mobile-Communication-Company-Customer-Churn
Machine Learning (R, Classification, Decision Tree)

Executive Summary (All the tables and figures are shown in the pdf file)
[Churn Project Analysis Report.pdf](https://github.com/EvanaZhang/Mobile-Communication-Company-Customer-Churn/files/9804998/Churn.Project.Analysis.Report.pdf)

                   
Problem 
Mobile communication companies are paying attention to the increasing number of people who would like to stop using phone services. This project will include two models (a logistic regression model and a decision tree model) to determine why consumers will stop using the phone services through different areas, and provide with recommendations and build a profile of the customers most likely to stop using their services. 

According to the “Data Analysis” part, I believe that consumers who opt for paperless billing and with different phone models are more likely to keep their phone services. (There’s only one phone model has a positive coefficient of rising the loss rate.) Therefore, I don’t think that network speed or for the most of the phone model will impact the loss rate, paperless billing is the main effect of the loss rate. 
Key Findings 
•	There’re around 50.9% customers who have many phones are more likely to continue using the phone services.
•	Among all types of phone models, customers who use Samsung.Galaxy.S20…S20.Plus are more likely to keep the phone services. 
•	Customers who use an unlimited streaming phone plan are approximately 88.42% likely to stop using the phone services.
•	Customers who don’t have a mobile hotspot on their phone are more likely to keep the phone service. 
Model Performance Summary & Interpretation
This dataset has total 34 variables which includes 11 numeric variables, 22 character variables, and 1 date variables. I removed some of the variables that I think is not very relevant or important for further analysis, and I also convert the senior_citizen variable to character and the target variable “churn” to a factor before building the models. By comparing all the models, we noticed that the default logistic regression model has the highest accuracy and area under ROC curve (AUC). 

Because of the dataset’s imbalance which leads to the misleading accuracy, we should compare the precision value of each model to make sure we have a model with the best performance. According to the “FPR/TPR/Precision & Recall (Apply with threshold of 0.1)” part (will be shown later in the data analysis steps), we can see that logistic has the highest precision which means the logistic regression model returns more relevant results. 

Recommendations
•	The company should consider to implement a long-term plan to increase the number of bills for avoid a high churn/loss rate of the customers. 
•	According to my model, more customers prefer using the paperless billing method are more likely to keep the phone services. Thus, the company should consider to use more paperless billing instead of non-paperless billing method. 
•	The company could create some ads or provide some discount, or may be some new products/phone services to encourage customer to buy more, so that if there’s a loss rate happen, the company could still keep their profitability.  

Detailed Analysis & Steps
The table below show the overview of both training and evaluate data files (Table 1)
 
The table below presents the field detail information of categorical variables (Table 2)
 
The table below presents numeric variable descriptive statstics (Table 3) 
Here’s the frequency and percentage of the target variable (churn) – Frequency Analysis
 (Table 4)
 
(Figure 1)

Initial Screening & Exploration (charts)
The boxplots below show the relationship between each numeric variable and the target variable
 	 
 	 
 	 
 	
Each of the boxplot shows what each numeric variable data looks like, most of them (monthly_minutes, streaming_minutes, total_billed, prev_balance) have a lot of outliers which might be a factor to impact the models and results later. Only late_payment and number_phone has a few outliers compare to others. 


Correlation Analysis
 


Data Preparation & Transformation 
According to the data profile presented in Table 2 and Table 3, almost all categorical and numeric variables have missing values. Since the number of the missing values from each variable are quite close to each other, I decided to select the variables that related to churn through three aspects: network speed influence, phone model, paperless billing. Therefore, I remove some of the categorical variables and numeric variables with a lot of text type information in the dataset, such as ip address, phone area code, billing address, customer reg date, email domain, billing city, billing postal, billing state, contract code, currency code, mailing code, billing address, and gender. The final step before partitioning the data into training and testing split, we need to convert the target variable “churn” into a factor. 

Model Building & Training 
Recipe: After partition the data into the form of 70/30 train and test split, I use the step_rm() function to remove the customer ID variable, since I found out that it is not quite useful for building either the logistic regression models or decision tree. 
-	The table below shows what variables include and used for building models. The target variable “churn” is highlighted in Yellow. 
 

Importance Plots

Logistic Regression Full Model	Lasso L1 Regression with the penalty tried on 0.01
 	 

Ridge Regression L2 Importance 	
Decision Tree Model 1
 	 
Decision Tree 2	
 	

Compare the Logistic Regression Models 

Confusion Matrix 

Logistic Regression Full Model	
 	 
Decision Tree Model 1	

 	 
Decision Tree Model 2	
 	 

Compare the Decision Tree Models

 
Based on the information above, decision tree 1 has the higher precision with lower mn_log_loss, accuracy and recall, and decision tree 2 has a lower precision with higher recall, mn_log_loss, accuracy. 

FPR/TPR/Precision & Recall (Apply with threshold of 0.1)

Model Type	Precision (FPR)	Recall (TPR)
Logistic Regression		
Decision Tree 1		
Decision Tree 2		

Score Distribution for Test Dataset

Logistic Regression 	Decision Tree 1
 	 
Decision Tree 2	
 	


