---
title: "Predict Suicidal Ideation Based on Tweets"
date: 2018-11-28
tags: [deep learning, data science]
excerpt: "Deep Learning, Data Science"
mathjax: "true"
---

## Introduction

Identifying people with suicidal tendencies through social networks is a real social issue and an emerging research area with major challenges. The key challenge of suicide prevention is understanding and
detecting the complex risk factors and warning signs that may precipitate in the event. This project presents an approach to understand suicidal ideation and cluster people with similar sentiment and
location, with the goal of early detection via supervised and unsupervised learning.
The data is obtained using online user-generated content. This project demonstrates various classification and clustering techniques. Following are some of the techniques implemented: Decision
tree, Random forest, Deep Learning, CNN etc.

## Architecture

![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/ArchD.png)

## Dataset

* Sentiment Classification (Positive - Negative)
  *250,000 rows tweets 
  *Features: User ID, Date, Username, Date, Time,  Tweets,  Sentiment
* Suicidal Ideation Classification(Suicide - Non Suicide Post)
  *2000 rows Suicide twitter post
  *Feature - Tweets, Target Label
* Clustering 
  *Features - Tweets, Latitude, Longitude, Sentiment, Suicide Label  

## Text Mining Process

![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/TextMining.png)
Text Mining is the task of extracting meaningful information from text. The preprocessing step consists of the following tasks:
* **Data Cleaning** – Identifying invalid data, removing null values from the records etc.
* **Tokenization** - The task of breaking a character sequence up into pieces (words/phrases) called
   tokens and removing characters like punctuations.
* **Filtering** - Removal of some of the words. Like stop-words removal. Ex: me, they, them
* **Lemmatization** - Grouping together the various inflected forms of a word so they can be
analyzed as a single item. Ex: running -&gt; run
* **Stemming** - Stemming methods aim at obtaining stem (root) of derived words.
* **Vector Space Model** - Converting documents into numeric vectors. Used in various text mining
algorithms and IR systems for efficient analysis of large collection of documents.

## Classification

The Twitter dataset is obtained from Kaggle, which is used as the training set for the different models trained. The dataset is imported and cleaned, using various data cleaning methods. This is followed by the data preprocessing phase. Once the data is ready, it is split into Train-Test sets. These sets are used to train various models and obtain the test results for the same. The different performance measure for each model is captured and are compared to identify the best model. The models are validated using the k-fold validation.
**Classification (Sentiment - Positive/Negative)**

![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/C-1.png)
![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/C-2.png)
![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/C-3.png)

**Classification (Suicidal Post or Not)**

![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/S-1.png)
![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/S-2.png)
![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/S-3.png)

## Word-Clouds

![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/Pos.png)
![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/Neg.png)

## Data collection and Model Prediction

The live streaming data is collected from twitter using the Twitter API.  The desired fields like UserId, Username, Tweet, User location, Place full name, country code and Place Co-ordinates. This dataset is first cleaned and preprocessed. Then it is passed to the 2 trained models from the classification phase and the predictions are captured. This new dataset with the predictions is used for the clustering.

## Clustering

The dataset is first cleaned. The latitude and longitude are extracted from the place co-ordinates. The records labelled with negative and potential suicidal are extracted and clustering is performed using the latitude and longitude for the models. The models cluster users with similar sentiments, thus predicting the sentiment of the users from the different locations and also helps to identify users with suicidal intentions and thus help can be provided to them.
Clustering algorithms:
* **K-Means**
* **DB – Scan**
![alt]({{ site.url }}{{ site.baseurl }}/images/TwitterSentiment/DB-SCAN.png)

[Github](https://github.com/reetika-goel)








