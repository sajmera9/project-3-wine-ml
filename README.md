# project-3
# README.md - Wine Machine Learning

![Google Slides Presentation](https://docs.google.com/presentation/d/1N-f0Op63flI7O2gbPgGN0Pstkd7OkGQKAus4lXZFlB0/edit?usp=sharing)

![Tableau Public Link](https://public.tableau.com/profile/kenneth.tanaka#!/vizhome/Project3_15887384141130/Sheet1?publish=yes)


## Wine Machine Learning Project

**Background**
The purpose of this project is to predict wine quality given a set of features. The dataset used is Wine Quality Data Set  from from UCI Machine Learning Repository. https://archive.ics.uci.edu/ml/datasets/wine+quality. This data is of red and white Portuguese "Vinho Verde" wines.

We applied the data to several machine learning models; Linear Regression, Logistic Regression, Neural Networks and Random Forest to determine which would provide the highest accuracy and thereby provide the better predictor of quality.

**About the Dataset** 
The are two datasets separated into red wine and white wine CSV files. Due to privacy and logistic issues, only physicochemical (inputs) and quality (output) variables are available. There is no data about grape type, wine brand, price, etc.)

There are eleven input variables:
1.Fixed Fixed Acidity
2.Volatile Acidity
3.Citric Acid
4.Residual Sugar 
5.Chlorides 
6.Free Sulfur Dioxide 
7.Total Sulfur Dioxide
8.Density
9.pH
10.Sulphates
11.Alcohol

There is one output variable:
1.Quality (score between 0 and 10)

**Exploratory Data**
We immediately notice the dataset between red and white wines are not balanced:
    Red wine (1,599 datapoints)
    White wine (4,898 datapoints)

We create a heatmap to view correlation among all the variables. Only a few had a strong positive or negative correlation.

While quality is scored between 0 and 10, a histogram reveals the scores are unbalanced.
    Red wine quality scores range from 3 thru 8.
    White wine quality scores range from 3 thru 9.
There are no wines given a quality a 0, 1, 2, and 10. Most wines were scored 5 or 6.

**Models** - Ken
In all models, we apply a 80%/20% train/test split. In other words, 20% of the dataset is used to test the performance of the model. We tried several models and would use the best one to move forward with our analysis.

Linear Regression - We initially apply the dataset separately. The Linear Regression is not a good model for this dataset (Red MSE: .5861, Red Rsquare: .3722, White MSE: .7178, White Rsquare: 02727). Applying Lasso, Ridge, and Elastic Net all had similar results.

Before testing other models, we combined both the red and white wine datasets to the following models and accuracy:
Logistic Regression : 47%
Neural Networks : 56%
Random Forest : 68%

We were able to achieve the highest accuracy using random forest. Next we applied feature engineering to random forest to try and achieve a higher accuracy.





**Random Forest Classifier** - Satvik 



**Conclusion** - Satvik 