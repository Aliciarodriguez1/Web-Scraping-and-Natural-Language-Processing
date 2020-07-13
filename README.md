Web APIs & NLP Classifier
Problem Statement

To get two web APIs from Reddit.com and train them by using NLP to make a binary classification and predict which post is from each subreddit.

Executive Summary

Overview

Reddit is a social news community, web content and discussion website in which subscribers share their content such as links, posts, images, etc. Subscribers join and add their comments in their posts of interest which are well organized by subject, subreddits or categories, for example: ecommerce, stocks, fashion and other diverse topics. There are 330 million Reddit subscribers, and the main % comes from USA.

Content

-Data Collection

-Data Cleaning

-Exploratory Data Analysis

-Pre-processing

-Modeling

-Evaluation of the Model

-Conclusions and recommendations

Research

The subreddits that were chosen for this project are "Streaming" and "Startups". The first subreddit "Streaming" has 16,899 members and it's for people who are interested in and active in streaming. The second subreddit is "Startup" focus; it has 425,988 members and its content is for those who want to discuss startup problems and solutions.

After deciding which topics to analyze, the web APIs had to be requested so the data can be obtained, as well as checking the status code = 200 that gives you the green light for using each subreddit. By having the data, JSON was used to pass it to a dictionary format so it can be transfer into its respective dataframe. The streaming dataframe had an initial shape of 2666 rows and 9 columns, on the other hand the startup dataframe had a shape of 2066 rows and 9 columns to begin with.

Data cleaning began by removing the duplicated authors to have well distributed posts and different points of views wanted to be analyzed. After doing that the new number of rows for streaming were: 1409 and for startup:1314, and then the 2 dataframes were combined. This being done, different items were removed like: punctuations, html items, stop words and apply lower case to all of the words. As a binary classification topic 0 was given to the streaming subreddit and 1 for the startup subreddit.

Our subreddits started with a baseline score of streaming: 0.51 startup: 0.48(We will have this as reference)

For the models, the lemmatokenizer was applied, applying different hyperparameters to do a Gridsearch in a pipeline: 1)Vectorizer -Linear Regression 2)TFIDF - Linear Regression
3)Count Vectorizer - Multinomial Naive Bayes
4)TFIDF - Gaussian Naive Bayes

and the following parameters were consider:

Max Features: 100, 250, 500, 1000 Stop words: None, English N grams: (1,1), (1,2)

Results were analyzed for each best model combining them with the cross validations; as a resulty the best model was the Count Vectorizer - Multinomial Naive Bayes with an accuracy score of: train set = 0.952 test set = 0.939

and the confusion matrix showed the following:

             predict_negative  predict_positive
actual negative 444 21 actual positive 33 401

catalogizing 33 as type II: False negative and 21 as type I False positive.

The following confusion matrix metrics were obtained:

Accuracy: 0.948

Misclassification: 0.052

Sensitivity: 0.936

Specificity: 0.959 | Precision: 0.956

Conclusions and Next Steps

-The best model was the countvectorizer with Multibibonial fron Naive Bayes

-Explore different models like Random Forest.

-Analyze the words that appear the most in each subreddit and see the opportunities to focus or research on to elaborate strategies.

-Check the words with the coefficients per subreddit to discover unique words and differentiators.
