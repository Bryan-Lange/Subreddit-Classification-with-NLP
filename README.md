# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Subreddit Classification Project: Web APIs & NLP

**By Bryan Lange**

## Problem Statement :crystal_ball:

Can we use NLP to train classification models that accurately categorize posts from different subreddits? 

## Executive Summary 

The aim of this project is two fold in nature. The first element entails using the Pushshift API and webscraping techniques to gather posts from two different subreddits. Our task is to then use Natural Language Processing tools to train models to accurately predict which subreddit a particular post belongs to. Classification modeling is extremely wide-reaching and impacts fields from banking (fraud vs legit) to medical (malignant vs benign) and many in-between, highlighting its predictive power and versatility.

The chosen two subreddits are:
- **r/talesfromcallcenters** [tfcc](https://www.reddit.com/r/talesfromcallcenters/)
- **r/talesfromretail** [tfr](https://www.reddit.com/r/talesfromretail/)
---
These two were used based on the fact the forums revolve around dealing with dissatisfied customers and should have overlapping vocabulary. Our goal is to train the model to sift through the general terminology and hone in on the unique words that help to accurately classify each post. Even thought the subreddits have mutual themes, hopefully the model is able to distinguish between them given the sheer amount of data is has been trained on.  

### Project Process 
-Data Collection
-Data Cleaning & EDA
-Preprocessing & Modeling
-Evaluation and Conceptual Understanding
-Conclusion and Recommendations

## 1. Gathering the data
-Use get request to scrape subreddit data from Pushshift’s API 
-Pushshift is a big-data storage and analytics project that aggregates Reddit data
-Pass in rendered json data to create dataframe for each subreddit 
-Scraped 4000 unique posts from each subreddit

---

## 2. Data cleaning and pre-processing 
-Used the Natural Language Tool Kit, Regex and other libraries to help clean the data
-Language was vectorized using the Count Vectorizer before being passed into models
-Stop-words were engineered based on word frequency to increase the difficulty for our models


## 3. Fitting the models 
-Utilized Pipelines and Gridsearches to run through a vast amount of models:
    * Logistic Regression
    * Multinomial Naive Bayes
    * Gaussian Naive Bayes

Model  | Best Test Score
------------- | -------------
Logistic Regression  | .94
Multinomial Bayes  | .95
Gaussian Bayes  | .94
  
---

## Model Understanding
Many of the models were slightly overfit due to the high variance given so many features and parameters passed through each model fitting. Overall the models performed well when provided the lengthy text found within the post itself, but did not fare as well when only subjected to limited characters found within the titles. A majority of the models performed best with no stop words used, a max range of 5000 words and a (1,2) n-gram range. Ultimately the Multinomial Bayes model was the most successful at correctly classifying the subreddit posts, but many of the models had similarly high scores. 

## Conclusions
-Utilizing web APIs is crucial for efficient web-scraping 
-The r/talesfromretail and r/talesfromcallcenters can be correctly classified to a high degree of accuracy given sufficient text 
-It is easy to overfit models when hypertuning and grid-searching over pipelines
-The Multinomial Bayes model achieved the highest degree of accuracy overall 

