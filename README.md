# Sparkify

Software requirements:
- Spark
- Python 3.6
- Pyspark.sql
- Pyspark.ml
- Python libraries: datetime, matplotlib, seaborn, numpy, pandas

Motivation: The goal of this project was to use Apache Spark for big data analysis and modeling using the Sparkify dataset provided by Udacity. The project was completed using IBM's Cloud Pak for Data to allow distributed computing using a Spark cluster. The aim was to create a model that can accurately predict when a user will "churn" (end their subscription) to a fictionary music app called Sparkify. Before modeling could commence, several features had to be created.

Files: The entire project is contained within the Sparkify_Notebook_1.ipynb notebook in the repository. The data used was the medium-sized (231 MB) dataset from Udacity entitled medium-sparkify-event-data.json available on the IBM platform.

Results summary: Four models were evaluated for this project: Logistic Regression, Decision Tree, Random Forest, and Gradient Boost, all from the Pyspark.ml library. The best model was found to be The Gradient Boost model with 10 trees, and parameters of maxDepth = 5, and maxIter = 10. This model had an F1 score of 0.94. The next best models were the Decision Tree and Random Forest models, both of which had F1 scores of 0.89. The Logistic Regression performed the worst, with an F1 score of 0.77. 

The most important features in the winning model were subscription length (labeled lifetime in the feature list), number of friends added, number of thumbs downs given to songs. Users that churned tended to have a shorter subscription length. In other words, once users had used Sparkify long enough they were less likely to churn.  Users that did not churn tended to add more friends as well, suggesting that they were enjoying their Sparkify experience and wanted to share it with their friends. There were proportionally more thumbs down given to song given by users that churned indicating that they may not have enjoyed the music Sparkify was suggesting to them.

Acknowledgements: Thank you to https://www.udacity.com/ for the project and data. 
