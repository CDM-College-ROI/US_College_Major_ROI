# <span style ="color: firebrick">Return on Investment Analysis of US Undergraduate College Majors</span>

![roi_image](roi_image.jpg)

<br>

**Created By:**

<center>

| Chenchen Feng</center> | David Schneemann</center> | Mijail Mariano</center> |
| :----:          | :----:        | :----:           |
| [github.com/Chenchen070](https://github.com/Chenchen070)</center> | [github.com/SchneemannDavid](https://github.com/SchneemannDavid)</center> | [github.com/mijailmariano](https://github.com/mijailmariano)</center> |

</center>


October 2022

*Codeup, Kalpana Cohort*

----
### **Table of Contents**

* [Project Description](#project-description)
* [Project Goal](#project-goal)
* [Process](#process-in-brief)
* [Steps to Reproduce](#steps-to-reproduce)
* [Data Dictionary](#data-dictionary)
* [Exploratory Questions](#exploratory-questions)
  * [What are the most common words in READMEs?](#1-what-are-the-most-common-words-in-readmes)
  * [Does the length of README vary by programming language?](#2-does-the-length-of-the-readme-vary-by-programming-language)
  * [Do different programming languages use a different number of unique words?](#3-do-different-programming-languages-use-a-different-number-of-unique-words)
  * [Are there any words that uniquely identify a programming language?](4-are-there-any-words-that-uniquely-identify-a-programming-language)
* [Modeling](#modeling)
* [Recommendations & Next Steps](#recommendations--next-steps)
* [Project Delivery](https://www.canva.com/design/DAFLfrYbwyA/8DMEYjMXzZQ65GgmgiGtrQ/view?utm_content=DAFLfrYbwyA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
----
### **Project Description**

<br>

The associated benefits or potential costs of attending college today are key topics of conversation for those considering whether to enter college. The realized return on investment of such a decision is difficult to quantify and leaves many prospective students unsure about which college to choose or degree and subsequent career field to pursue. 

This analysis seeks to inform both current and prospective students on the value and expected tradeoffs that decisions such as these can have on their return on investment and the potential financial future graduates can expect to have. 

To accurately predict return on investment, we analyze collected college information criteria (variables) of undergraduate college majors. 

The college data used in this study is from the 2017-2018 and 2018-2019 academic years and is acquired from the US Department of Education College Scorecard. We integrate this data with US Census earnings data from 2019 which is sourced from the University of Minnesota's IPUMS database. 
 
**Initial Dataset:**
Contains 225,000 unique records and 3000+ variables

**Cleaned & Prepared Dataset:**
Contains roughly the same number of initial records but narrows the number of studied variables to ~120 

We apply machine learning clustering techniques to combine and model groups of unique variables. This allowed us to provide greater depth and new insights from these clustered variables and their impact on predicted return on investment.

<br>

### **Project Goal**

<br>

Our goal for this project was to predict a return on investment (ROI) for US college undergraduate majors. We use US Department of Education College Scorecard data to test and identify statistically significant metrics to predict a "cost-to-earnings" ratio of predominant college majors at the 5-, 10-, and 20-year post-undergraduate degree periods.

We explore how potential variables within the data produce certain return on investment ratios and provide insight into why and how these factors contribute to our target ROI variable. With this information and the following recommendations, we intend to provide current and prospective students a greater understanding of the value and trade-offs tied to a given college major and its potential career paths.


----

### **Process: In Brief**

<br>

1. We first acquire and merge the US Department of Education College data with the University of Minnesota IPUM Earnings data.

2. We then filter the initial dataset for solely Bachelor degree records and create a new table for easier data cleaning and preparation. 

3. After calculating and creating the cost-to-earnings ratio/ROI, we assign this variable to all Bachelor degree records. 

4. We then perform the following data cleaning processes on the Bachelor degree data: clean variable names for easier readability, expand on the geographical location variable and map this to all college records, we drop redundant columns in the dataset that captured the same information. 

5. We then study and treat outliers in the dataset. We use a winsorization method to cap outliers at their respective 10th and 90th percentiles.

6. We train and apply an Scikit-learn Iterative Imputer to impute remaining null values in the dataset.

7. We conduct exploratory analysis and statistical testing on the college variables and choose only statistically significant features to move forward into clustering and modeling.

8. We select unique variables to cluster on and conduct statistical testing to measure and determine their relationship.

9. We then model and visually measure cluster predictions from actual observations.

10. In model-stacking, we use a Scikit-learn recursive feature elimination with cross-validation to determine most significant variables to model and predict the target variable.

11. Using a principal component analysis method to transform our datasets, we then generate three (3) linear models and measure their results against the train and validate datasets.

12. After evaluating results, we deploy our best performing PCA-OLS model on the final out-of-sample dataset. 

13. Finally, we analyze our findings and provide recommendations for future analysis and actionable steps.

----

### **Steps to Reproduce**

<br>

**<span style ="color:firebrick">Key Libraries & Modules:</span>**

[![github-shield](https://img.shields.io/badge/GitHub-grey?logo=github&logoColor=white)](https://github.com/MBM-nlp/github_classification_project)
[![jupyter-shield](https://img.shields.io/badge/Jupyter_Notebook-grey?logo=jupyter&logoColor=white)](https://jupyter.org/install)
[![python-shield](https://img.shields.io/badge/Python-grey?&logo=python&logoColor=white)](https://www.python.org/)
[![pandas-shield](https://img.shields.io/badge/Pandas-grey?&logo=pandas&logoColor=white)](https://pandas.pydata.org/docs/getting_started/install.html)
[![numpy-shield](https://img.shields.io/badge/Numpy-grey?&logo=numpy)](https://numpy.org/install/)
[![sklearn-shield](https://img.shields.io/badge/_-grey?logo=scikitlearn&logoColor=white&label=scikit-learn)](https://scikit-learn.org/stable/install.html)


[![matplotlib-shield](https://img.shields.io/badge/Matplotlib-3.5.1-lightgrey)](https://matplotlib.org/stable/users/installing/index.html)
[![seaborn-shield](https://img.shields.io/badge/Seaborn-0.11.2-lightgrey)](https://seaborn.pydata.org/installing.html)


<br>

1. This analysis requires several datasets which are originally acquired from the US Department of Education College Scorecard Platform and Minnesota's IPUMS database. 

* To streamline the reproduction of this analysis, we've chosen to solely provide the cleaned and prepared "undergraduate/Bachelors degree" table. This table can be referenced on the repository landing page as a .csv file. This file is also the initial data when running the final jupyter notebook report. 

* The 'acquire.py' file can be referenced for further table familiarity and the studied variables. 

2. The 'prepare.py' file provides the necessary functions for cleaning, transforming, splitting, and imputing data in the initial dataset. 

3. The 'model.py' file provides the necessary functions used in cluster modeling and predictions. This file also includes several functions to help visualize the model results. 

4. We recommend cloning this repository in its entirety to best reproduce this analysis and the subsequent findings. If there are any challenges in doing so - please contact any of the author of this study for troubleshooting assistance. 



----

### **Data Dictionary**

<br>

| Variable      | Meaning |
| ----------- | ----------- |
|  ACT_score_mid |  Midpoint of the ACT cumulative score |
|  admission_rate |  Rate of Admission by Institution |
|  avg_faculty_salary |  Avg Faculty Salary by Institution |
|  avg_net_price_private |  Average net price for Title IV institutions (Private) |
|  avg_net_price_public |  Average net price for Title IV institutions (Public) |
|  avg_sat_admitted |  Average SAT equivalent score of students admitted |
|  branch_number |  No. of branch campuses |
|  city |  City Location of the Institution |
|  college_name |  Name of the institution |
|  comp_rt_ft_150over_expected_time |  Full-Time completion rate expected at 150% expected time (4 years) |
|  comp_rt_ft_150over_expected_time_** |  Full-Time completion rate by Student Race |
|  deg_percent_awarded_agriculture_operations ** |  Percentage of Degree Awarded at given Insitution, 37 total categories represented |
|  degree_code |  Degrees Coded |
|  degree_name |  Name of Degree represented |
|  enrollment_share_** |  Share of enrollment per Institution, Breakdown of Students by Race |
|  enrollment_share_two_races |  Share of enrollment per Institution, Students of 2 Races |
|  federal_loan_full_time_first_time_undergraduate |  Percentage of full-time, first-time undergraduate students awarded a federal loan |
|  first_time_ft_student_retention |  Retention Rate of Full-Time First Time Students |
|  full_time_net_tuition_revenue |  Net tuition revenue per full-time equivalent student |
|  graduate_number |  No. of graduate level students who are graduating |
|  income_0_30000 |  Family Income Bracket: $0-30000 |
|  income_30001_48000 |  Family Income Bracket: $30001-48000 |
|  income_48001_75000 |  Family Income Bracket: $48001-75000 |
|  income_75001_110000 |  Family Income Bracket: $75001-110,000 |
|  income_over_110000 |  Family Income Bracket: over $110,000 |
|  major_code |  Major Coded |
|  major_name |  Name of Major represented |
|  med_debt_pell_students |  Median Debt of Students awarded Pell Grants |
|  median_debt_completed |  Cumulative Median Debt of Students over entire college career |
|  median_debt_non_first_generation |  Median Debt of Non-First Generation Students |
|  median_debt_non_pell |  Median Debt of Students NOT awarded Pell Grants |
|  non_deg_seeking |  No. of Students with no declared major |
|  off_campus_cost_of_attendace |  Avg cost of attendance living off campus |
|  on_campus_cost_of_attendace |  Avg cost of attendance living on campus |
|  online_only |  Indicates institutions which only provide online learning |
|  pell_grant_full_time_first_time_undergraduate |  Percentage of full-time, first-time undergraduate students awarded a Pell Grant |
|  pred_degree |  Predominant degree awarded for each institution |
|  pred_degree_0and4 |  Code of Predominant degree awarded for each institution |
|  region_ipeds |  Unique US region code |
|  share_entering_students_first_ft |  Full-Time First Time Student share of student population |
|  share_of_part_time |  Part-Time Student share of student population |
|  state_post_code |  2-character State abbreviation |
|  title_IV_eligibility |  Eligibility Type for Student Financial Aid |
|  undergraduate_number_pell_grant_federal_loan |  No. of students using pell grants and federal loans |
|  unit_id_institution |  The unique ID # for each institution |
|  zip_code |  Zip Code of the Institution |

<br>

\* *multiple rows represented, broken down by demographics or 'other' category*


----

### **Exploratory Questions and Hypothesis Testing**

<br>

#### **5 Year Return on Investment**
<br>

**Is there a statistically significant difference among the following examined variables and their potential impact on ROI?**

* Undergraduate college majors
* College share of first-time, full-time entering students
* Public/private/foreign controlled institutions
* Average university faculty salary
* Full-time student tuition revenue
* College US geographical regions
* College admission rates

<br>

#### **Creating and Modeling Clusters**

<br>

1. Is there a statistically significant difference in the share of first-time, full-time entering college students and faculty salaries?

2. Is there a statistically significant difference across college admission rate levels and students with family income bracket 48-75K? 

3. Is there a statistically significant difference in undergraduate majors and university share of part-time students?

4. Is there a statistically significant difference between the levels of admitted SAT scores and the number of undergraduate students with federal pell-grants and loans?

5. Is there a statistically significant difference across US geographical regions and institution full-time tuition revenue?

6. Is there a statistically significant difference between among the institution control types and college admission rates?

-----

### **Cluster Modeling**

<br>

**<u>Tested Linear Algorithms w/Principal Component Dimensionality Reduction</u>**

* Linear Regression (OLS)
* Lasso Lars (Least Angle Regression)
* Tweedie Regression (Generalized Linear Model)


#### **<u>Model Evaluation on RMSE</u>**

<br>

| Model     | Train     | Validate     |
|----       |----       |----          |
| OLS w/PCA | 0.39      | 0.39         |
| GLM w/PCA | 0.39      | 0.40         |
| LassoLars w/PCA | 0.41 | 0.41        |



<u>**``Performance of OLS Linear Regression w/PCA Through Test Dataset``**</u>

| PCA OLS Model | RMSE          |Relative % Difference  |
|----           |----           |----                   |
| Baseline      | 0.41          | -                     |
| Train         | 0.39          | 0.05                  |
| Validate      | 0.39          | 0.0                   |
| Test (final)  | 0.39          | 0.0                   |

----

### **Recommendations & Next Steps**



----

### **Project Delivery**
[Presentation]()
