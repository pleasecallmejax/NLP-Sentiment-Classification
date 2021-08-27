# NLP Twitter Sentiment Classification
*a Flatiron Project by Jax*

<img src=https://climatematters.blogs.uni-hamburg.de/wp-content/uploads/2015/12/Fig-2_Plot_Wordcloud_uniqueUsers.jpeg height="500" width="1000">

## Table of Contents

### Repository Structure
### Overview
### Business Problem
### Data Info/Cleaning
### Analysis & Recommendations


### A Project Overview

This repository is an Natural Language Processing in the form of Tweets about sentiment towards climate change classification model capable of predicting whether a tweet is written with positive, neutral, or negative sentiment. The goal of our model is to have a high F1 score, due to imbalance classes, so we know that our predictions are meaningful. By using different machine learning techniques, we are capable of interpreting the customers’ feelings toward our clients’ products, making our model a useful tool for companies interested in allocating their resources to better serve their customers.

### Business Problem

We are the research and development team at Gihu Reasearch, a marketing firm that advises manufacturers on their marketing strategy to appeal to climate change supporters via Twitter. We are making a proposal to the executives of our company about how our Machine Learning model should be implemented to help the social media analysts at Nebula Analytics perform their job more efficiently and effectively.

### The Data

The dataset is sourced from CrowdFlower, via data.world which had over 5,800 tweets. It originally consisted of four columns. The first column simply being an id number, assigning a numeric value to each record. The second was tweet_text, which encapsulated the raw tweets referring to various sentiments. The information in this column was heavily cleaned in the data pre-processing stage. Next, was the existence column which were {Yes : positive}, {No : negative}, or {N/A : neither}, that were labeled systematically by individuals and uploaded to the dataset.It served as the label column in which the customer’s sentiment – negative, positive or neutral, was interpreted and logged. Finally existence_confidence which was a float that represented the data-collectors confidence in the tweet being climate change related. It didn't really serve that much use to my project.

Now onto EDA,text preprocessing is important for NLP tasks. Transforming text from raw sentences and phrases, into a form that the model can extract information from, consists of many steps and actions. I of course I checked for null values, and outliers(long tweets, dtypes). Secondly I built a function to easily parse through and clean tweets of embedded text like mentions, retweets, links, videos, and hashtags/punctuation. Tokenizing, which is turning strings into a list of words Lower casing all letters in the dataset. Then removing stop words that do not add meaning to a sentence while finally lemmatizing words to their root. Finally I label encoded the three target classes.


### Analysis and Recommendations

I first tested a naive bayes and random forests calssifier and due to our large target class imbalance, set them to use the stratified strategy with gridsearch. I created a pipeline using those two models, a tfidf vectorizer and added a smote for our target class imbalance. I then ran a grid search on that pipeline to find our best parameters. The hyperparameter tuning was used to maximize the F1 scores of the model. Once the best parameters were identified, from there we were able to keep the parameters constant while focusing solely on an individual parameter and adjusting it with use of a function to maximize my precision/recall metrics from cmy lassification_report. This method saved time by affording me the ability to bypass conducting a new grid search with every experimentation I ran on the parameter tuning at the micro-level. Once it was determined that we had the best hyper-parameter, the process was repeated on all applicable parameter settings.