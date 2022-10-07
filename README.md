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
* [Analysis Process](#process-in-brief)
* [Steps to Reproduce](#steps-to-reproduce)
* [Exploratory Questions](#exploratory-questions)
  * [5 Year Return on Investment](#5-year-return-on-investment)
  * [Creating and Modeling Clusters](#creating-and-modeling-clusters)
* [Clusters](#clusters)
* [Modeling](#modeling)
* [Recommendations & Next Steps](#recommendations-next-steps)
* [Data Dictionary](#data-dictionary)
* [Project Delivery](#project-delivery)

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

1. Acquired and merged the US Department of Education College data with the University of Minnesota IPUM Earnings data.

2. Filtered the initial dataset for solely Bachelor degree records and create a new table for easier data cleaning and preparation. 

3. Calculated and created the cost-to-earnings ratio/ROI; assigned this variable to all Bachelor degree records. 

4. Performed the following data cleaning processes on the Bachelor degree data: cleaned variable names for easier readability, expanded on the geographical location variable and mapped this to all college records, we then dropped redundant columns in the dataset that captured the same information. 

5. Analyzed and treated outliers in the dataset. Applied a winsorization method to cap outliers at their respective 10th and 90th percentiles.

6. Trained and applied an Scikit-learn Iterative Imputer to impute remaining null values in the dataset.

7. Conducted exploratory analysis and statistical testing on the college variables and choose only statistically significant features to move forward into clustering and modeling.

8. Selected unique variables to cluster on and conducted statistical testing to measure and determine their combined variable relationship.

9. Modeled and measured cluster predictions from actual observations.

10. In model-stacking, we use a Scikit-learn recursive feature elimination with cross-validation to determine most significant variables for predicting the target variable.

11. Used a principal component analysis method to transform our datasets.

12. Tested three (3) linear algorithms with non-linear PCA transformations and measured their results against the train and validate datasets.

13. Evaluated results and deployed our best performing PCA-OLS model on the final out-of-sample dataset. 

14. Finally, we analyzed our model results and findings and provide recommendations for future analysis and actionable steps.

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

### **Exploratory Questions and Hypothesis Testing**

<br>

#### **5 Year Return on Investment**
<br>

**Is there a statistically significant difference among the following examined variables and students' 5-year return on investment (ROI)?**

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

2. Is there a statistically significant difference across college admission rate levels and students with family income bracket $48-75K? 

3. Is there a statistically significant difference in undergraduate majors and university share of part-time students?

4. Is there a statistically significant difference between the levels of admitted SAT scores and the number of undergraduate students with federal pell-grants and loans?

5. Is there a statistically significant difference across US geographical regions and institution full-time tuition revenue?

6. Is there a statistically significant difference between among the institution control types and college admission rates?

----

#### **Clusters**

* **College Major Cluster** \
\
When undergraduate majors like Archeology, Geology, and Forestry are grouped into higher major classifications like "Environment and Natural Resources" we find there are statistical differences across these majors share of part-time students. When we combine these unique major variables with university share of part-time students, the K-means algorithm can accurately capture these variables with some degree of accuracy.    

* **Admissions Rate Cluster** \
\
College admission rates are often seen as an indicator of their academic competitiveness and the number of applications it may receive and ultimately the applicants they select. We thought that these rates could make for an interesting variable when classified among a spectrum from "above-average-acceptance" to "very-competitive." \
\
Additionally, when tested against colleges' student population with median family incomes of $48-75K in 2019, we identified that there were statistical differences among these groups. 

* **Institution Control Cluster** \
\
This cluster involved pairing institution admission rates and the control of an institution meaning whether they are a private, public, or foreign college. \
\
The K-means algorithm returned the greatest cluster coefficient score at three distinguishing clusters. We believe this was consistent with the imbalance of observations among the four institution control types. We felt that while initially exploring this cluster, the unsupervised K-means algorithm also did a great job at visually predicting and labeling actual observations.

* **College Region Cluster**\
\
We wanted to measure if geographical differences could help us in determining future student 5-year ROI. Across 8 continental US regions and 1 foreign territory region, we found that there was also distinct difference among these region's full-time tuition revenue. When paired together this made-up our college region cluster which we introduced in modeling.

* **First-time Student Cluster** \
\
The basis of the first-time student cluster comes from a national college average of first-time, full-time entering students. We binned colleges into distinct buckets based on where they fell on a feature engineered spectrum of first-time, full-time entering students based on a national average. These new classifications ranged from "below average" to "highest average." \
\
To introduce another unique and statistically significant ROI variable, we looked at these classifications in relation to universities average faculty salaries.

* **SAT Score Clusters** \
\
Like college admission rates, SAT scores required by colleges can span a relative spectrum. For this variable, we used the national average SAT score of ~1050 for US colleges to create distinct classifications. These classes varied by either "average", "above average", "competitive", or "very competitive" and were generated based on a minimum and maximum score found in the dataset. \
\
We measured these variables in relation to colleges' student population with federal loans and/or pell grants. The results of our findings proved that the population size of these students across colleges were statistically different across college's required SAT score. \
\
It's important to also note that on average - universities that required "very competitive" SAT scores also had the highest population of students with either federal loans and/or pell grants. We believe that a future iteration of this study warrants further analysis of this finding and what, if any, additional implications there may be for attending a college that requires a relatively competitive SAT score.

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

### **Project Delivery**

[Presentation: Return on Investment - US College Majors](https://www.canva.com/design/DAFMrth7BRc/tFF8QC2w2Ob0B0N0GgnMSQ/view?utm_content=DAFMrth7BRc&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

[White Paper: "Return on Investment - Analyzing U.S. College Undergraduate Majors"](https://www.canva.com/design/DAFNh1WKWbQ/LxKRaf6aVvW7IMCdi-Uflw/view?utm_content=DAFNh1WKWbQ&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)