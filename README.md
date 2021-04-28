Capstone_3
==============================

# Predicting Future Rates of Chronic Absenteeism in NYC Public Schools

## the problem 

Absenteeism is a huge indicator of student success and also impacts school funding. If students are not in school they cannot learn or graduate. Once students and schools have high chronic absenteeism rates, it is a very difficult and costly problem to remediate. 

Being able to predict a school’s attendance/chronic absenteeism numbers and identify the contributing variables would allow district administrators to proactively intervene with these school’s ahead of time. Saving time, money, and resources, as well as increasing student/school outcomes. We used NYC OpenData’s school-level attendance data from 2013-2019. In New York State Chronic Absenteeism is defined as when a student is absent 18 or more days of the school year.

## the approach

The goal was to predict next year's rates of chronic absenteeism by school, grade, and demographic variable using attendance/school data from NYC's OpenData. [NYC DOE rates of % Chronically Absent across Time](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/ChronicAbsent_overtime.png)

See [Final Report documentation](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/Capstone_3_Final_Report_JFrasca.pdf) for more information on approach.

## the findings
#### select links to see images

- There was variation in rates of Chronic Absenteeism across Demographic Variable, Grade, Borough, and District:
    - [% Chronically Absent by Demographic Variable](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/DemVar_violinplot.png)
    - [% Chronically Absent by Grade](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/Grade_violinplot.png)
    - [Next Year % Chronically Absent by District](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/District_Num_violinplot.png)
    - [Next Year % Chronically Absent by Borough](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/Borough_violinplot.png)
    
- Both classification and regression models were tested. The best performing model was the [Random Forest Regression model.](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/RF_regressor_modelMetrics.png)

- A Decision Tree model was also created to get a very interpretable understanding. The [Decision Tree plot](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/decisionTree_plot.png) shows that the model is simply using ‘%Attendance’,  ‘% Chronically Absent’ & ‘% Chronically Absent - diff from 2 yr avg’  to predict the 3 classes.  This may have some informative value to schools, as it simply shows that if a school or student group within a school is Chronically Absent more than 44.65% of the time this year they will be in ‘High’ group of Chronically Absent next year. Also if they are at or below 44.65% Chronically Absent and above 95.55% attendance they will be in the ‘Low’ group next year and if their attendance is less than 95.55% then they would be in the ‘Medium’ group. 

- Trends in 2019-20 seem not to be comparable with what was witnessed during covid-19 (this is understandable as it was a blackswan event).

- There are schools/districts/boroughs that are doing significantlly better in having low rates of Chronic Absenteeism with the groups that have the highest rates of chronic absenteeism (ie. grades 9-12, PreK & K, Students with Disabilities (SWD), Black &  Hispanic students. They could be studied for best practices to share with others. [See example of top performing schools for SWD barplot here](https://github.com/jjfrasca/Springboard/blob/main/Capstone_3/Capstone_3/reports/figures/README_figures/topSchools_SWD.png)



## further research

There are several ways to go for further research:

- build a model with less features (and only include the most important), as many of the features don’t seem to contribute much.
- **add more features from parent surveys and academic data, to make this data more actionable. This could also help pull apart why the exemplar schools (for high-risk categories) are doing so well.**
- to turn chronic absenteeism from a multi class categorical variable to a binary variable. As we are concerned mostly with whether Chronic Absenteeism is 'High' or not.
- test more models for regression/classification with more hyperparameter tuning.
- test the model’s predictions as real data comes out
- share the findings with NYC DOE (Department of Education)

## Client recommendations

- **Create measurable goals and regularly & publicly report on each school**. They can draw on the splits from the decision tree to determine goals (ie. all demographic groups/grades have below 44.65% chronic absenteeism, all groups have above 95.55% attendance)
- **Look at the success schools who have the lowest rates of chronic absenteeism for the high risk populations (groups that have the highest rates of chronic absenteeism) and study why they are successful. Then share these best practices with other schools.**
- Use the data to target and focus support on:
    - Target At Risk populations (Grades 9-12, PreK & K, Black and Hispanic Students, and Students with Disabilities)
    - Target Lowest Performing Districts/Boroughs/Schools and focus support on them
    - Target ‘Medium’ Chronic Absenteeism groups and move them to ‘Low’ Chronic Absenteeism. Since ‘Medium’ had the most variance there may be more of an opportunity to do this quickly, building momentum and experiencing success to then tackle the ‘High’ Chronic Absenteeism groups.




Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
