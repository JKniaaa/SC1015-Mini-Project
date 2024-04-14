# SC1015-Mini-Project

School of Computer Science and Engineering \
Nanyang Technological University (NTU) \
Lab: FCSG \
Group : 1 

### Group Members: 
1. Goh Jun Keat ([@JKniaaa](https://github.com/JKniaaa))
2. Celeste Ho Shir Chee 
3. He QiXin 

---
### Project Description:
For our Introduction to Data Science and Artificial Intelligence module (SC1015) Mini Project, we performed analysis on the Data Science Salaries [dataset](https://www.kaggle.com/datasets/zain280/data-science-salaries) from Kaggle.

---
### Problem Statements:
**Main problem: Are most Data Science professionals getting paid above the median salary?**

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
   - Placeholder
   - Placeholder
4. [Data Driven Insights and Conclusion](#4-Data-Driven-Insights-and-Conclusion)
5. [References](#5-References)

---
### 1. Data Preperation and Cleaning
We cleaned the dataset to help us analyse the data better during Exploratory Data Analysis and Data Modelling.

We did the followig to clean our dataset:
1. **Check dataset for `NULL`, `NaN` and repeated values:** No such values were found.
2. **Remove unnecessary data:** Columns `id`, `salary`, `salary_currency` and `employee_residence` were dropped for better presentation of data.
3. **Rename values in data:** Values in columns `experience_level`, `employment_type`, `remote_ratio` and `company_size` were renamed for better understanding of data values.
4. **Add new columns:** Columns `job_category` and `above_median` added for analysis and modelling purposes. `above_median` is the responding variable for data modelling.

**Note: Outliers were not removed yet as the removal of outliers at this stage would cause inaccuracies during Exploratory Data Analysis.**

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
2. Used lineplot to visualise the trend of the average `salary_in_usd` by `work_year`. 
3. Visualised distribution of potential predictors for `above_median` in 2 steps: \
    a. Find the distribution of **potential predictors:**
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

Models attempted: \
**1. Binary Classification:**

    a. The dataset was split into Train and Test by ratio of 7:3.
    
    b. Binary Tree model was created with max depth of 4.
    
    c. Analysis of Train data:
      - Accuracy: 76.50%
      - False Positive Rate (FPR): 16.19%
      - False Negative Rate (FNR): 30.92%
      
    d. Analysis of Test data:
      - Accuracy: 75.00%
      - False Positive Rate (FPR): 21.28%
      - False Negative Rate (FNR): 29.07%

**2. Binary Classification:**


**3. Binary Classification:**




---
### 4. Data Driven Insights and Conclusion

**Conclusion:**


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
- Ways to observe and justify the most suitable model for modelling based on accuracy.

---
### 5. References












