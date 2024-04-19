# SC1015 Mini-Project

Nanyang Technological University (NTU) \
School of Computer Science and Engineering \
Lab: FCSG \
Group : 1 

### Group Members: 
1. Goh Jun Keat ([@JKniaaa](https://github.com/JKniaaa))
2. Celeste Ho Shir Chee ([@mommypokko](https://github.com/mommypokko))
3. He Qixin ([@qhe012](https://github.com/qhe012))

---
### Project Description:
For our Introduction to Data Science and Artificial Intelligence module (SC1015) Mini Project, we performed analysis on the Data Science Salaries [dataset](https://www.kaggle.com/datasets/zain280/data-science-salaries) from Kaggle.

**Dataset:** [Data Science Salaries](https://www.kaggle.com/datasets/zain280/data-science-salaries)

### Dataset Variables:
`id`: Numeric labels which document the number of respondents in numerical order depending on the submission of survey by respondent.

`work_year`: Numeric labels indicating the year of work when data was collected from the respondent.

`experience_level`: Information about the level of experience required or possessed by individuals in each role. This may include categories like entry-level, mid-level, senior-level, or years of experience in the field.

`employment_type`: Information about the type of employment by the individual. This may include categories like full-time, part-time, contract and freelance.
    
`job_title`: Descriptive labels indicating the specific position or role within the data science field, such as Data Scientist, Data Analyst, Machine Learning Engineer, etc.

`salary`: Numeric values representing the annual or monthly compensation for each position. 
    
`salary_currency`: Descriptive labels which indicate the currency of the `salary`.
    
`salary_in_usd`: Numeric values representing the `salary` in terms of United States Dollars (USD).
    
`employee_residence`: Geographic location where the individual resides, categorized by country.

`remote_ratio`: Numeric labels which indicate the degree of remoteness of the workplace of individuals. 

`company_location`: Geographic location where the job is based, categorized by country

`company_size`: Information about the size of the employing company, often categorized by the number of employees or revenue.

---
### Problem Statements:
**Main problem: Why are some Data Science professionals getting paid more than others?**

*Potential Insights that can be obtained:*
1. Distribution of salaries (USD) of Data Science professionals.
2. The most popular Data Science Job and Job Category.
3. The most popular destinations to work for Data Science professionals.
4. Trend of Job Opportunities for Data Science field.
5. Average employee salary (USD) by year.

---
### Table of Contents:
1. [Data Preparation and Cleaning](#1-Data-Preparation-and-Cleaning)
2. [Exploratory Data Analysis](#2-Exploratory-Data-Analysis)
3. [Data Modelling](#3-Data-Modelling):
   - Binary Classification
   - Random Forest
   - Logistic Regression
4. [Data Driven Insights and Conclusion](#4-Data-Driven-Insights-and-Conclusion)
5. [References](#5-References)

---
### 1. Data Preperation and Cleaning
We cleaned the dataset to help us analyse the data better during Exploratory Data Analysis and Data Modelling.

We did the followig to clean our dataset:
1. **Check dataset for `NULL`, `NaN` and repeated values:** No such values were found.
2. **Remove unnecessary data:** Columns `id`, `salary`, `salary_currency` and `employee_residence` were dropped for better presentation of data.
3. **Rename values in data:** Values in columns `experience_level`, `employment_type`, `remote_ratio` and `company_size` were renamed for better understanding of data values.
4. **Add new columns:** Columns `job_category` and `above_median` added for analysis and modelling purposes. `above_median` is the responding variable for data modelling. \
   a. `job_category`: Descriptive labels indicating the general area of profession based on similarities in type of work. \
   b. `above_median`: Descriptive labels indicating if the salary_in_usd of individuals is above the median salary (USD).


- **Note: Median value used** to determine `above_median` is the median value **before removal of outliers.**
- **Note: Outliers were not removed yet as the removal of outliers at this stage would cause inaccuracies during Exploratory Data Analysis.**

---
### 2. Exploratory Data Analysis
We explored our dataset to answer our problem statements. We were able to obtain some insights other than those related to the main problem.

We found the following for **EDA Part 1:**
1. Used boxplot to visualise the distribution of `salary_in_usd` based on `job_title`: 
2. Used catplot to visualise the most popular `job_title` and `job_category` of each `work_year`. 
3. Used barplot to visualise The top 10 most popular data science related `company_location`. 
4. Used barplot to visualise The trend of job opportunities by `work_year` in data science field. 

**We now remove the outliers to balance the distribution of our dataset better. `10` rows of data were dropped from the dataset.**

For **EDA Part 2:**
1. Used catplot to visualise distribution of `above_median`.
2. Used line graph to visualise the trend of the average `salary_in_usd` by `work_year`. 
3. Visualised distribution of potential predictors for `above_median` in 2 steps: \
    a. Find the distribution of **potential predictors:** \
        &nbsp;&nbsp;&nbsp;&nbsp; i. Potential predictors are `company_location`, `job_title`, `job_category`, `experience_level`, `employment_type`, `remote_ratio` and `company size`. \
        &nbsp;&nbsp;&nbsp;&nbsp; ii. Used catplot and jointplot to visualise distributions. \
        &nbsp;&nbsp;&nbsp;&nbsp; iii. Found that `job_title`, `job_category`, `company_location` and `employment_type` were not suitable predictors. \
    b. Find relationship of **valid predictors** with `salary_in_usd` and `above_median`: \
        &nbsp;&nbsp;&nbsp;&nbsp; i. Valid predictors were `experience_level`, `remote_ratio` and `company size`. \
        &nbsp;&nbsp;&nbsp;&nbsp; ii. Used swarmplot to visualise relationship with `salary_in_usd`. \
        &nbsp;&nbsp;&nbsp;&nbsp; iii. Group the data of predictors based on corresponding value of `above_median`. 

---
### 3. Data Modelling
We now try to find the best model to predict whether employee salary (USD) is `above_median` using predictors `experience_level`, `remote_ratio` and `company size`.

The following was done **before modelling:**
1. Created a **new dataframe** to store the response variable and the predictors.
2. **Encoded the data** in the dataframe appropriately.

Models Attempted:

**1. Binary Classification:**

    a. The dataset was split into Train and Test by ratio of 8:2.
    
    b. Binary Tree model was created with max depth of 4.

    c. Upsampling was done to increase accuracy of prediction.
    
    c. Analysis of Train data:
      - Accuracy: 77.78%
      - False Positive Rate (FPR): 19.44%
      - False Negative Rate (FNR): 25.21%
      
    d. Analysis of Test data:
      - Accuracy: 72.95%
      - False Positive Rate (FPR): 21.15%
      - False Negative Rate (FNR): 31.43%

**2. Random Forest:**


    a. The dataset was split into Train and Test by ratio of 8:2.
    
    b. 300 decision trees with depth 5 (chosen via hyper-paramater tuning using Cross-Validation (CV), using accuracy as the scoring parameter)
    
    c. Analysis of Train data:
      - Accuracy: 75.51%
      - False Positive Rate (FPR): 19.84%
      - False Negative Rate (FNR): 29.49%
      
    d. Analysis of Test data:
      - Accuracy: 81.97%
      - False Positive Rate (FPR): 17.31%
      - False Negative Rate (FNR): 18.57%

**3. Logistic Regression:**

    a. The dataset was split into Train and Test by ratio of 8:2.

    b. After training, the code uses the trained model to make predictions on the testing data using `predict()`.

    c. Analysis of Train data:
      - Accuracy: 73.66%
      - False Positive Rate (FPR): 42.28%
      - False Negative Rate (FNR): 53.75%

    d. Analysis of Test data:
      - Accuracy: 75.41%
      - False Positive Rate (FPR): 44.83%
      - False Negative Rate (FNR): 37.50%
    


---
### 4. Data Driven Insights and Conclusion

**Conclusion:**
- Binary Classification suggests that valid predictors can predict whether salary (USD) of respondent is above median​ salary (USD). However, the model is not highly accurate.
- Random Forest suggests that valid predictors can predict if salary (USD) is above median salary (USD) with decent accuracy and has the lowest false positive and false negative rate.
- Logistic Regression suggests that while valid predictors can predict whether salary (USD) is above median salary (USD), it is not highly accurate. At the same time, this model has the highest false positive rate and false negative rate out of the 3 models. 

- `Random Forest` model is the **more suitable model** to predict whether the salary (USD) of a Data Science Professional is `above median` salary (USD) based on `experience_level`, `remote_ratio` and `company_size` as the model has **higher accuracy**.


**Data Driven Insights:**
- Different Data Science jobs seem to have different ranges of salary (USD).
- The most popular Data Science profession in `2020` and `2021` was `Data Scientist`, while the most popular Data Science profession in `2022` was `Data Engineer`.
- The most popular Data Science job category in `2020` and `2021` was `Data Scientist`, while the most popular Data Science job category in `2022` was `Data Analyst`.
- Most of the Data Science related companies are found in the `USA`.
- There is an increasing number of job opportuinities in the Data Science field from 2020 to 2022.
- There are more employees receiving below median salaries (USD) than those receiving above median salaries (USD).
- The average salary (USD) of Data Science professionals increases far more between `2021` and `2022` compared to between `2020` and `2021`.
- Data Science professionals are becoming **increasingly popular** and **sought after by companies** as time passes.


**What We Learned from this Project:**
- To visualise other useful and interesting insights from the dataset and make inferences from them.
- Handling categorical variables using one-hot encoding for data modelling purposes.
- Logistic Regression
- Ways to observe and justify the more suitable model for modelling based on accuracy.


---
### 5. References
1. [https://stackoverflow.com/questions/57165247/rename-column-values-using-pandas-dataframe](https://stackoverflow.com/questions/57165247/rename-column-values-using-pandas-dataframe)
2. [https://www.dataquest.io/blog/tutorial-add-column-pandas-dataframe-based-on-if-else-condition/](https://www.dataquest.io/blog/tutorial-add-column-pandas-dataframe-based-on-if-else-condition/)
3. [https://www.geeksforgeeks.org/how-to-customize-line-graph-in-jupyter-notebook/](https://www.geeksforgeeks.org/how-to-customize-line-graph-in-jupyter-notebook/)
4. [https://towardsdatascience.com/random-forest-in-python-24d0893d51c0](https://towardsdatascience.com/random-forest-in-python-24d0893d51c0)
5. [https://medium.com/@24littledino/accuracy-in-python-980074154e52](https://medium.com/@24littledino/accuracy-in-python-980074154e52)
6. [https://www.w3schools.com/python/python_ml_logistic_regression.asp](https://www.w3schools.com/python/python_ml_logistic_regression.asp)
7. [https://realpython.com/logistic-regression-python/](https://realpython.com/logistic-regression-python/)













