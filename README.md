# Predicting Employee Churn

## Overview
Your goals in this project are to analyze the data collected by the HR department and to build a model that predicts whether or not an employee will leave the company.

After conducting feature engineering, the decision tree model achieved AUC of 93.8%, precision of 87.0%, recall of 90.4%, f1-score of 88.7%, and accuracy of 96.2%, on the test set. The random forest modestly outperformed the decision tree model.

### Data Understanding

The dataset that you'll be using in this lab contains 15,000 rows and 10 columns for the variables listed below. 

**Note:** For more information about the data, refer to its source on [Kaggle](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv).

Variable  |Description |
-----|-----|
satisfaction_level|Employee-reported job satisfaction level [0&ndash;1]|
last_evaluation|Score of employee's last performance review [0&ndash;1]|
number_project|Number of projects employee contributes to|
average_monthly_hours|Average number of hours employee worked per month|
time_spend_company|How long the employee has been with the company (years)
Work_accident|Whether or not the employee experienced an accident while at work
left|Whether or not the employee left the company
promotion_last_5years|Whether or not the employee was promoted in the last 5 years
Department|The employee's department
salary|The employee's salary (U.S. dollars)



## Analyze (EDA)
![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/project_hour_boxplot.png) 

1. Employees who left the company fall into two groups: (A) those who worked significantly less than their peers with the same project count, for example who works on 2 project (possibly fired or on their way out), and (B) those who worked much more (likely quit due to overwork).

2. All employees with seven projects left, and those with six projects had very high working hours (~255–295 hours/month). The ideal workload appears to be 3–4 projects, where the leave rate is low.

3. Most employees worked far beyond a standard 166.67-hour work month, indicating general overwork across the company.
<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/satisfaction_hour_scatter.png)

The scatterplot shows a large group working 240–315 hours/month, with extremely low satisfaction (~0). Some employees with normal hours also left, though their satisfaction was only ~0.4, possibly due to workplace pressure.
<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/satisfaction_by_tenure.png)

- Four-year employees who left seem to have an unusually low satisfaction level. It's worth investigating changes to company policy that might have affected people specifically at the four-year mark, if possible. 
- The longest-tenured employees didn't leave. Their satisfaction levels aligned with those of newer employees who stayed.

<br/>
  
![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/salary_by_tenure_hist.png)

The plots above show that long-tenured employees were not disproportionately comprised of higher-paid employees.

<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/monthly_last-evaluation_scatter.png)

The scatterplot indicates two groups of employees who left: overworked employees who performed very well and employees who worked slightly under the nominal monthly average of 166.67 hours with lower evaluation scores.

<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/hours_promotion.png)

- very few employees who worked the most hours were promoted
- all of the employees who left were working the longest hours

<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/status_by_department.png)

There doesn't seem to be any department that differs significantly in its proportion of employees who left to those who stayed

<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/corr_heatmap.png) 

whether an employee leaves is negatively correlated with their satisfaction level.

<br/>

### Insight
Employees are likely leaving due to poor management, overwork, and low satisfaction. Long hours and many projects without rewards contribute to burnout. However, those with 6+ years at the company tend to stay.

<br/>

## Summary of model results

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/decision_tree_plot.png) 

<br/>

![](https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/rf2_confusion_matrix.png)

<p float="left">
  <img src="https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/tree_feature_imp.png" width="48%" />
  <img src="https://github.com/gokhanmutlu/employee_churn_model/blob/main/images/rf2_feature_imp.png" width="48%" />
</p>

The plots above show that in this both model, `last_evaluation`, `number_project`, `tenure`, and `overworked` have the highest importance, in that order. These variables are most helpful in predicting the outcome variable, left, and they are the same as the ones used by the decision tree model.



After conducting feature engineering, the decision tree model achieved AUC of 93.8%, precision of 87.0%, recall of 90.4%, f1-score of 88.7%, and accuracy of 96.2%, on the test set. The random forest modestly outperformed the decision tree model.

To retain employees, the following recommendations could be presented to the stakeholders:

- Cap the number of projects that employees can work on.
- Consider conduct further investigation about why four-year tenured employees are so dissatisfied.
- Either reward employees for working longer hours, or don't require them to do so.

- High evaluation scores should not be reserved for employees who work 200+ hours per month. Consider a proportionate scale for rewarding employees who contribute more/put in more effort.


