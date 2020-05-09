# project-3
# README.md - Wine Machine Learning

![Google Slides Presentation](https://docs.google.com/presentation/d/1N-f0Op63flI7O2gbPgGN0Pstkd7OkGQKAus4lXZFlB0/edit?usp=sharing)

![Tableau Public Link](https://public.tableau.com/profile/kenneth.tanaka#!/vizhome/Project3_15887384141130/Sheet1?publish=yes)


## Wine Machine Learning Project

**Background**
The purpose of this project is to predict wine quality given a set of features. The dataset used is Wine Quality Data Set  from from UCI Machine Learning Repository. https://archive.ics.uci.edu/ml/datasets/wine+quality. This data is of red and white Portuguese "Vinho Verde" wines.

We applied the data to several machine learning models; Linear Regression, Logistic Regression, Neural Networks and Random Forest to determine which would provide the highest accuracy and thereby provide the better predictor of quality.

**About the Dataset** 
The are two datasets separated into red wine and white wine CSV files. Due to privacy and logistic issues, only physicochemical (inputs) and quality (output) variables are available. There is no data about grape type, wine brand, price, etc.

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

**Models** 
In all models, we apply a 80%/20% train/test split. In other words, 20% of the dataset is used to test the performance of the model. We tried several models and would use the best one to move forward with our analysis.

Linear Regression - We initially apply the dataset separately. The Linear Regression is not a good model for this dataset (Red MSE: .5861, Red Rsquare: .3722, White MSE: .7178, White Rsquare: 02727). Applying Lasso, Ridge, and Elastic Net all had similar poor results.

Before testing other models, we combined both the red and white wine datasets to the following models and accuracy:
Logistic Regression : 47%
Neural Networks : 56%
Random Forest : 68%

We were able to achieve the highest accuracy using random forest and decided to apply feature engineering to this model to try and achieve a better accuracy score.

**Random Forest Classifier**
We had to consider the unequal number of white and red wines in the dataset, when preprocessing the data. Therefore, we decided trying to take into account normalized data in our model. How did we normalize the data? For all our test we used an 80/20 train/test split and our n_estimators = 100. For an experiment, we took a random sample of 1599 white wines to match the 1599 red wines called `balanced data`. Unfortunately our accuracy score was actually lower (64%) than the `unbalanced data` (4898 white wines, 1599 red wines). Additionally, adding color as a feature to the model for both the unbalanced and balanced data was insignificant to the Random Forest model. Therefore, color does not affect quality scores and improve the accuracy of our models. 

Finally, we decided to further feature engineer by binning quality scores in a number of different ways. Using the `Three Bins` experiment, quality scores range from 3 to 4, 5 to 6, and 7 to 9 and are binned as Terrible (1), Mediocre (2), and Great (3). This result in the highest accuracy at 85%. In the `Four Bins` experiment, the quality scores range from 3 to 4, 5,  6, and 7 to 9 and our scores are Terrible (1), Mediocre (2), Good (3) and Great(4). This resulted in a 68% accuracy. Lastly, `Balanced Bins` used same quality scores as `Three Bins`, however, each bins consisted of the same number of wines matching the terrible(1) bin. This resulted in a 67% accuracy. (Check slides 14-16 in Wine Presentation for more details).


**Conclusion** 
In all, we found that the most important feature for the wine dataset which determines quality is alcohol percentage. Consistently for all our models the alcohol percentage was at least a 12 percent important feature in the Random Forest Classifier. Furthermore, every other feature was almost as important. No feature was less than 7 percent in feature importance of all the 11 features. This means that all our inputs were almost equally important in our models. This posed a challenge when feature engineering because we could not simply drop certain features, since they may be improving the accuracy of quality in some way.