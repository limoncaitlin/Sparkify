# Sparkify

Software requirements:
- Spark
- Python 3.6
- Pyspark.sql
- Pyspark.ml
- Python libraries: datetime, matplotlib, seaborn, numpy, pandas

## Motivation: 
The goal of this project was to use Apache Spark for big data analysis and modeling using the Sparkify dataset provided by Udacity. The project was completed using IBM's Cloud Pak for Data to allow distributed computing using a Spark cluster. The aim was to create a model that can accurately predict when a user will "churn" (end their subscription) to a fictionary music app called Sparkify. Before modeling could commence, several features had to be created.

## Files: 
The entire project is contained within the Sparkify_Notebook_1.ipynb notebook in the repository. The data used was the medium-sized (231 MB) dataset from Udacity entitled medium-sparkify-event-data.json available on the IBM platform.

## Summary of work: 
The data was first cleaned to remove empty user logs that did not contain a user id or session id. The variable "churn" was created by identifying users where the Cancellation Confirmation was listed in the page column. Date and time information was converted to a human readable format. Several features were engineered, including: counts of thumbs up and thumbs down given to songs, counts of friends added, total time spent listening by each user, total number of songs listened to, and time since registration. These features were all input to Logistic Regression, Decision Tree, Random Forest, and Gradient Boost models. Hyperparameters were tuned for the best performing model, Gradient Boost. F1 score was used to evaluate the model as the dataset was not evenly distributed between churners and non-churners and F1's reliance on both precision and recall can better account for this unbalanced dataset.    

## Results summary: 
Four models were evaluated for this project: Logistic Regression, Decision Tree, Random Forest, and Gradient Boost, all from the Pyspark.ml library. The best model was found to be The Gradient Boost model with 10 trees, and parameters of maxDepth = 5, and maxIter = 10. This model had an F1 score of 0.94. The next best models were the Decision Tree and Random Forest models, both of which had F1 scores of 0.89. The Logistic Regression performed the worst, with an F1 score of 0.77. F1 scores were chosen to evaluate the models because the data set was imbalanced, as only 22% of users churned, so the model is trying to predict a somewhat rare event. F1 scores are well suited to this situation because they balance both precision and recall. Also in the Sparkify problem the cost of false positives and false negatives are different, making F1 a better fit. False positives mean that a user is thought to be a churner when they are not. In this case there is a small cost of proactively increasing their engagement and satisfaction with the app. Alternatively, false negatives are more problematic, as you miss the opportunity to prevent churn before it happens by categorizing the user as unlikely to churn. 

The most important features in the winning model were subscription length (labeled lifetime in the feature list), number of friends added, number of thumbs downs given to songs. Users that churned tended to have a shorter subscription length. In other words, once users had used Sparkify long enough they were less likely to churn.  Users that did not churn tended to add more friends as well, suggesting that they were enjoying their Sparkify experience and wanted to share it with their friends. There were proportionally more thumbs down given to song given by users that churned indicating that they may not have enjoyed the music Sparkify was suggesting to them.

## Acknowledgements: 
Thank you to Udacity for the data and project.
