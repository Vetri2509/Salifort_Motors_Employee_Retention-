# Nurturing Talent, Maximizing Potential: An Analysis of Employee Retention Strategies at Salifort Motors
##  Google Advanced Data Analytics Professional Certification Course Capstone Project 

## Introduction:

Salifort Motors is a fictional French-based alternative energy vehicle manufacturer.
As a data specialist working for Salifort Motors, I have been assigned by  The senior leadership team  with analyzing the data to come up with ideas for how to increase employee retention.

Here, I analyzed the data, which included variables such as monthly working hours, number of projects, promotion status, department, and salary.

The project requirements was mainly to build either a logistic regression or a decision tree model however I've  created 5 classification models namely Logistic Regression, Decision Tree with and without hyperparameter tuning, Random Forest, and XGBoost to correctly classify employees who'll leave or stay in the company. Then I evaluated the models using metrics such as accuracy, recall, precision, f1 score, and confusion matrix. 

Finally I summarized the results and presented the recommendations for Salifort’s Senior Leadership team and Human Resources (HR) team with an Executive Summary.
   
The Human Resource department at Salifort Motors wants to take some initiatives to improve employee satisfaction levels at the company. They collected data from employees and they want to analyse and find the answer to the question: **What’s likely to make the employee leave the company?** Predicting which employees are likely to quit, might help the company to identify factors that contribute to their leaving. A good model will help the company increase retention and job satisfaction for current employees, and save money and time training new employees.

## Tools used:
Python - for Data Cleaning, Exploratory Data Analysis and building machine learning model


## Methodologies used:
1. Exploratory Data Analysis
2. Descriptive Statistics
3. Logistic regression model
4. Decision tree
5. Random forest
6. XGBoost

The entire project from collecting and validating the data, exploratory data analysis, building machine learning models to predict employee churn and communicating the results to the stakeholders is based on PACE workflow. PACE is an acronym; each one of the letters represents an actionable stage in a project: plan, analyze, construct, and execute.

![Pace](https://github.com/Arpita-deb/Salifort_motors_HR_analytics/assets/139372731/a392c404-8909-4167-ba55-da276f42a830)

# (P)ACE - PLAN - UNDERSTANDING THE DATA IN THE PROBLEM CONTEXT

## About the Company:
Salifort Motors is a fictional French-based alternative energy vehicle manufacturer. Its global workforce of over 100,000 employees research, design, construct, validate, and distribute electric, solar, algae, and hydrogen-based vehicles. Salifort’s end-to-end vertical integration model has made it a global leader at the intersection of alternative energy and automobiles.    
## Key Stakeholders:
* Salifort’s Senior Leadership team
* Human Resources (HR) department team

## Statement of the Business Task:
The purpose of this project is to design a model that predicts whether an employee will leave the company based on their job title, department, number of projects, average monthly hours, and any other relevant data points. Our goal is to analyze the key factors driving employee turnover, build an effective model, and share recommendations for next steps with the leadership team. 

## Deliverables:
1. [Project Proposal](https://github.com/Arpita-deb/Salifort_motors_HR_analytics/files/12567932/Salifort.Motors.Project.Proposal.pptx)
2. [An executive summary with important insights and recommendations](https://github.com/Arpita-deb/Salifort_motors_HR_analytics/assets/139372731/10d137c5-8e37-4b88-8b2c-ffde573f68f9)
3. A jupyter notebook with all the codes
   
## About the Data Set:
This project uses a dataset called **HR_capstone_dataset.csv** from [Kaggle](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv). It represents 10 columns of self-reported information from employees of a multinational vehicle manufacturing corporation. The dataset contains 14,999 rows – each row is a different employee’s self-reported information and 10 columns.

### Data Dictionary:

| Column Name | Type | Description |
| :--- | :--- | :--- |
| satisfaction_level | int64 | The employee’s self-reported satisfaction level [0-1] |
| last_evaluation | int64 | Score of employee's last performance review [0–1] |
| number_project | int64 | Number of projects employee contributes to |
| average_monthly_hours | int64 | Average number of hours employee worked per month |
| time_spend_company | int64 | How long the employee has been with the company (years) |
| work_accident | int64 | Whether or not the employee experienced an accident while at work |
| left | int64 | Whether or not the employee left the company |
| promotion_last_5years | int64 | Whether or not the employee was promoted in the last 5 years |
| department | str | The employee's department |
| salary | str | The employee's salary (low, medium, or high) |


# P(A)CE - ANALYSIS -  EDA, CHECKING MODEL ASSUMPTIONS & SELECT MODEL

## Data Cleaning:


* Renamed the column names with their correct spellings
* Changed all the variable names to lower case with snake case formatting as and when needed

## Python packages selected: 
1. Operational Packages
   
   * NumPy - Allows for more mathematical operations in Python, provides functions for array-like objects, etc
   * Pandas - Creation of data frames, analyzing data, cleaning data, manipulating data, performing efficient operations on large data sets

2. Visualization Packages

   * MatPlotLib - Easy-to-learn difficult-to-master graphing library for Python. Great for quick, exploratory graphs
   * Seaborn - Built on top of matplotlib, allows for easier customization of plots compare to matplotlib

3. Machine Learning Packages
   * Sci-Kit Learn - Provides functionality for a host of machine learning models and analytical tools.

## Exploratory Data Analysis:

### Steps taken:
1. Loaded the required python packages and the dataset.
2. Had a general sense of the data using head(), info(), shape() functions.
3. Performed descriptive statistics and calculated the mean,median, mode, maximum and minimum value of the numerical variables.
4. Checked for null and duplicate values. Removed the duplicates and saved the data in a new dataframe.
5. Checked for class imbalance.
6. Visualized the distributions of numerical and categorical variables.
7. Created Correlation matrix and Heatmap to find relations between the variables.
8. Created visualizations like boxplot, histogram, scatterplot, bar charts and regplot to get detailed view of the dataset.
9. Saved the data frame as a csv file to work later for regression analysis and model building.

### Summary of the Exploratory Data Analysis: 

1. The dataset doesn't contain any missing value but has 3008 duplicated values. We've removed those and created a new dataset with 11991 rows.


2. 'left' will be our target variable. We realize the majority class is about 83.4% of the data set, it is moderately imbalanced (~20%).

3. There are 10 Departments in this dataset. The department of Sales has the highest number of employee churn.

![dept](https://github.com/Arpita-deb/Salifort_motors_HR_analytics/assets/139372731/78609a75-0f5b-4de2-b30a-d80466dcd04b)

4. There are 3 salary levels in this dataset. Majority of the left employees have a low salary level, followed by medium and high. When the salary level goes up, the possibility of leaving is decreased.

![salary](https://github.com/Arpita-deb/Salifort_motors_HR_analytics/assets/139372731/11a7d3f0-49e5-4ef2-add2-2955f207f0ca)

5. We could start by creating a stacked boxplot showing average_monthly_hours distributions for number_project, comparing the distributions of employees who stayed versus those who left.
   ![image](https://github.com/user-attachments/assets/6fe7e160-3f52-4ef8-9611-b2f8b1ddd24d)
   * There are two groups of employees who left the company: (A) those who worked considerably less than their peers with the same number of projects, and (B) those who worked much more.
   * The optimal number of projects for employees to work on seems to be 3–4. The ratio of left/stayed is very small for these cohorts.
   * If you assume a work week of 40 hours and two weeks of vacation per year, then the average number of working hours per month of employees working Monday–Friday = 50 weeks * 40 hours per week / 12 months = 166.67 hours per month. This means that, aside from the employees who worked on two projects, every group—even those who didn't leave the company—worked considerably more hours than this. It seems that employees here are overworked.

6.When examining average monthly hour v satisfaction levels using scatterplot we noticed that there was a sizeable group of employees who worked ~240–315 hours per month. 315 hours per month is over 75 hours per week for a whole year. It's likely this is related to their satisfaction levels being close to zero.
There is another group who worked ~210–280 hours per month, and they had satisfaction levels ranging ~0.7–0.9.
![image](https://github.com/user-attachments/assets/9f0dfe97-7988-4338-ae12-8c39b3093ba1)

7.Satisfaction level v Tenure
![image](https://github.com/user-attachments/assets/8701fb2c-80e5-4a89-a897-525dc0755ce5)

* Employees who left fall into two general categories: dissatisfied employees with shorter tenures and very satisfied employees with medium-length tenures.
* Four-year employees who left seem to have an unusually low satisfaction level. It's worth investigating changes to company policy that might have affected people specifically at the four-year mark, if possible.
* The longest-tenured employees didn't leave. Their satisfaction levels aligned with those of newer employees who stayed.
* The histogram shows that there are relatively few longer-tenured employees. It's possible that they're the higher-ranking, higher-paid employees.

8.Salary v Short  and Long Tenure
![image](https://github.com/user-attachments/assets/656546d5-0e84-41f9-bcc7-7e1820817a9a)
*The plots above show that long-tenured employees were not disproportionately comprised of higher-paid employees.

9.Average_monthly_hours v Last_evaluation.
![image](https://github.com/user-attachments/assets/ce1d7512-d4d7-4e92-8787-d37933fb3125)

* The scatterplot indicates two groups of employees who left: overworked employees who performed very well and employees who worked slightly under the nominal monthly average of 166.67 hours with lower evaluation scores.
* There seems to be a correlation between hours worked and evaluation score.
* There isn't a high percentage of employees in the upper left quadrant of this plot; but working long hours doesn't guarantee a good evaluation score.
* Most of the employees in this company work well over 167 hours per month.

10.Checking if employees who worked very long hours were promoted or not in the last five years
![image](https://github.com/user-attachments/assets/8c04c218-299e-4b79-aea1-92d8dbf8fc30)
The plot above shows that:
* very few employees who were promoted in the last five years left
* very few employees who worked the most hours were promoted
* all of the employees who left were working the longest hours


### Recommendations based on EDA on Employee Retention:

1. Sales department of Salifort Motors has the lowest retention rate. The leadership and HR team should look into the matter further.
2. If the company wants to keep the talent in the company, they must reduce the working hours for overworked employees.
3. They should look into the matter when employees with high satisfaction level and evaluation score still leaving the company.

### Some questions for further research:

The HR department can look further into the matter by asking the following questions:
1. Why 63% of the total employees worked overtime? Is overtime a reason for low satisfaction level among the employees?
2. Why do sales department has lowest retention rate?
3. Is number of project and promotions are given unjustly to employees?
4. Why employees with high satisfaction level and evaluation score still left the company? Is there other factors affecting the employee retention?

###  Selecting models for the project:
Since our predictor variable 'left' is a binary/categorical variable (i.e., with only 2 possibilities, either 0 if stayed or 1 if left) we'll go for a classification model. 
We'll build 4 models -
1. Logistic Regression
2. Decision Trees
3. Random Forest
4. XGBoost model

We'll choose the one with highest evaluation scores and implement it to predict whether an employee will leave or not.

# PA(C)E - CONSTRUCT AND EVALUATE MODEL

## Steps taken to build the models: 
1. Import packages, functions, and classes
2. Get data to work with and, if appropriate, transform it
3. Create a classification model and train (or fit) it with existing data
4. Predicting the test result
5. Test accuracy of the result(Creation of Confusion matrix)

## Evaluation metrics:

1. **Accuracy score** :  Refers to the proportion of data points that were correctly categorized. Accuracy is an appropriate metric to use when the data is balanced, in other words, when the data has a roughly equal number of positive examples and negative examples. Otherwise, accuracy can be biased.
2. **Recall score**: The proportion of positives the model was able to identify correctly. 
3. **Precision Score**: The proportion of positive predictions that were true positives. 
4. **F1 score**: It’s a harmonic mean of “precision” & “recall”, taking both the metrics into account.
5. **Confusion matrix**: A graphical representation of how accurate a classifier is at predicting the labels for a categorical variable*
   * True negatives: The count of observations that the classifier correctly predicted as False (0). In this case, the classifier will correctly predict the employees who didn't leave.

   * True positives: The count of observations that a classifier correctly predicted as True (1) i.e. the classifier will correctly predict the employees who left.

   * False positives: The count of observations that a classifier incorrectly predicted as True (1) i.e. the classifier will predict employees as left but in reality, who stayed.

   * False negatives: The count of observations that a classifier incorrectly predicted as False (0). In this case, the classifier will incorrectly predict employees as stayed but in reality, who left.

The False negatives may cause the company to spend more resources on an employee who decides to leave. The False positives may cause the company to think an employee will leave and won't put resources on this employee. False negatives will be worse for the company, false positives will be worse for employees.


## Summary of model results
### Logistic Regression
![image](https://github.com/user-attachments/assets/9cfb62cd-bfbc-4ca2-acca-f4b917932c9d)
![image](https://github.com/user-attachments/assets/95ea6641-6755-42f0-9a84-4b8e357e8958)


The logistic regression model achieved precision of 80%, recall of 83%, f1-score of 80% (all weighted averages), and accuracy of 83%, on the test set.

### Tree-based Machine Learning and Random Forest
![image](https://github.com/user-attachments/assets/05fb52e5-9d6c-435e-b485-dc9dc7a5712c)


After conducting feature engineering, the decision tree model achieved AUC of 93.8%, precision of 87.0%, recall of 90.4%, f1-score of 88.7%, and accuracy of 96.2%, on the test set. The random forest modestly outperformed the decision tree model.

# PAC(E) - EXECUTE- INTERPRET MODEL AND SHARE STORY

|![image](https://github.com/user-attachments/assets/1666634b-29eb-4b8a-a5be-bffee1f78972) ![image](https://github.com/user-attachments/assets/ee837883-a988-40ab-89ba-3e1eecb013e0)



## Summary of the analysis:

In this project we've - 
1. Performed Exploratory Data Analysis on the HR_capstone_dataset provided by the HR team of Salifort Motors.
2. Visualized the relations between various variables and found out our predictor variable 'left'.
3. We've created 4 different models whose performance is evaluated by how many employees they've correctly predicted as left and stayed.
4. Among the models, Logistic Regression model performed worst with an f1 score of 0.383.
5. The best performing model is a Random Forest with auc score of 0.964, which is a good evaluation score for a prediction model.
6. From the graph of Feature Importance we can clearly see which feature(variable) influences most the employee retention in the company.  last_evaluation ,number project, tenure andare the top 3 important features for predicting if an employee will leave or not.
7. Compared to different departments, the employees in Sales are most likely to leave the company.

## Recommendations:

* The models and the feature importances extracted from the models confirm that employees at the company are overworked.

* To retain employees, the following recommendations could be presented to the stakeholders:

* Cap the number of projects that employees can work on.
* Consider promoting employees who have been with the company for atleast four years, or conduct further investigation about why four-year tenured employees are so dissatisfied.
* Either reward employees for working longer hours, or don't require them to do so.
* If employees aren't familiar with the company's overtime pay policies, inform them about this. If the expectations around workload and time off aren't explicit, make them clear.
* Hold company-wide and within-team discussions to understand and address the company work culture, across the board and in specific contexts.
* High evaluation scores should not be reserved for employees who work 200+ hours per month. Consider a proportionate scale for rewarding employees who contribute more/put in more effort
* Promoting work-life balance and wellness initiatives


