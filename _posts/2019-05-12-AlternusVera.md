---
title: "Fake News Detection (Writing Style)"
date: 2019-05-12
tags: [data science, machine learning]
excerpt: "Data Science, Machine Learning"
mathjax: "true"
---

## Introduction

Fake news is intentionally written to mislead readers, which makes it non-trivial to detect simply based on news content. The content of fake news is rather diverse
in terms of topics, styles and media platforms, and fake news attempts to distort truth with diverse linguistic styles while simultaneously mocking true news. For
example, fake news may cite true evidence within the incorrect context to support a non-factual claim.

Most liars use their language strategically to avoid being caught, in spite of their attempt to control what they are
saying, language “leakage” occurs with certain verbal aspects that are hard to monitor manually such as frequencies and patterns of pronoun, conjunction, and
negative emotion word usage. For detecting these linguistic patterns, it uses shallow and deep syntax analysis which use POS(parts-of-speech) tags.

There are two methods for Fake News Detection. Linguistic features capture the different writing styles and sensational headlines to detect fake news. Linguistic
based features are extracted from the text content in terms of document organizations from different levels, such as characters, words, sentences, and documents.
In order to capture the different aspects of fake news and real news, existing work utilized both common linguistic features and domain-specific linguistic features.
Common linguistic features are often used to represent documents for various tasks in natural language processing. Typical common linguistic features are:
1. **Lexical Features**, including character level and word-level features, such as total words, characters per word,
frequency of large words, and unique words; 
2. **Syntactic Features**, including sentence-level features, such as frequency of function words and phrases or punctuation and parts-of-speech (POS) tagging.

Domain-specific linguistic features, which are specifically aligned to news domain, such as quoted words, external links, number of graphs, and the average length of
graphs, etc. Moreover, other features can be specifically designed to capture the deceptive cues in writing styles to differentiate fake news, such as lying detection features.

## Dataset

I have used 2 datasets for this feature of fake news detection and will use the required attributes of these datasets to train our model.
1. **Real News Dataset:** https://www.kaggle.com/snapcrack/all-the-news/home
2. **Fake News Dataset:** https://www.kaggle.com/mrisdal/fake-news  

The Real News Dataset consists of 3 csv files. After concatenating these files, the dataset have about 15712 data points and 8 columns(id, author, title, text, date,
month, url, News(i.e real or fake)) after preprocessing the data, (i.e) removing duplicates and removing data points which are NULL etc. I store this preprocess
data into a new file real_news.csv

The Fake dataset have about 10900 data points and 8 columns(id, author, title, text, date, month, url, News(i.e real or fake)) after preprocessing the data, (i.e) removing
duplicates and removing data points which are NULL etc. Here,I only take those columns which are common in both the datasets. I store this preprocess
data into a new file fake_news.csv. 

Then concatenate both the datasets into a new file named real_fake_news.csv for further analysis and implementation.

## Implementation Steps

1. **Pre-processing**
Data preprocessing is done to convert the raw data into a required format. Data pre- processing can be done by
various methods like data cleaning, data reduction, data integration etc. In this project, the datasets are collected
from different resources which have different formats and attributes. Hence, the data can be duplicate and
they may contain some attributes which are not useful. So, convert the data into our required format with required attributes which are used to train our model.

![alt]({{ site.url }}{{ site.baseurl }}/images/FakeNews/Preprocess.png)

2. **Data Analysis**
After preprocessing, it is necessary to visualize the dataset to identify the maximum used word or the word
that has high frequency rate. This helps in deciding the vector size with less data loss. Word-cloud is used to
visualize the dataset. It provides more information and insights of texts by analyzing correlations and similarities
between words rather than analyzing texts only by the frequency of words appeared.

![alt]({{ site.url }}{{ site.baseurl }}/images/FakeNews/Data.png)

3. **Generating News Feature Vector**
The most important part of detecting if a given news is fake or not is to convert the news article into a
news vector which contains the important features which are used to determine the nature of the news. There are
several ways to generate feature vector . I have tried different approaches for the same to determine which
method gives the best accuracy. Some of the methods are:
  * Bag of Words:
  Bag of words is a way of representing text in a format which can be easily processed by the machine learning algorithms. BoW is one of the ways of extracting features from text.
  * TF-IDF:
  TF-IDF stands for term frequency-inverse document frequency.TF-IDF is a method used to represent text in a format which can be easily processed by the machine
  learning algorithms. It is a numerical statistic that shows how important a word is to a document in a word corpus. The importance of a word is proportional to the number
  of times the word appears in the document but inversely proportional to the the number of times the word appears in the corpus.
 * Syntactical Analysis:
  Syntactic analysis is the process of analysing a string of symbols in natural language, conforming to the rules of a
  formal grammar. I have generated POS(part-of-speech) tags using the Spacy library. The POS features will be
  encoded as tf-idf values for each for these tags. Further, POS features are strengthen with unigram/bigram features.
  * Semantic Analysis:
  A widely used open-source resource for incorporating semantic information is Empath. Empath is a lexicon of words grouped into semantic categories relevant to
  psychological processes. Empath has 194 semantic categories, some of these semantic classes are emotional tone(positive or negative), anger,
  nervousness.
4. **Classification**
After generating the news feature vector, now I have to classify the vector whether it is fake or real. The aim is to
use the following classification algorithms for the purpose of classification:
  * Naive Bayes:
  Naive bayes is a supervised learning algorithm which is used for classification. It is based on bayes theorem
  assuming that features are independent of each other. It calculates the probability of every class, the class with maximum probability is chosen as the output.
  * Random Forest:
  Random Forests is a bagging type of ensemble model in which the base model for bagging is decision tree. In
  addition to bagging (i.e taking random samples of total data and train those samples independently and then
  take the majority voting of numerous samples of the total dataset to find the output of the total dataset), there is
  feature bagging (i.e column sampling in which not all the columns/features are taken into consideration while
  training but rather random samples of features are considered while training different samples.
  ![alt]({{ site.url }}{{ site.baseurl }}/images/FakeNews/Random.png)
  * Logistic Regression:
  Logistic regression is used to describe data and to explain the relationship between one dependent binary
  variable and one or more nominal, ordinal, interval or ratio-level independent variables.
  * SVM Classifier:
  A Support Vector Machine (SVM) is a discriminative classifier formally defined by a separating hyperplane. In
  other words, given labeled training data, the algorithm outputs an optimal hyperplane which categorizes new
  examples. In two dimensional space this hyperplane is a line dividing a plane in two parts where in each class lay in either side.

## Result

Here, by identifying the different writing styles of the author, I want to predict whether the news is fake or not. 
So, for that I looked for the dataset which has authors, titles/headlines, text/body/content and also that dataset should not be biased. 
For that, I used two different datasets for both real and fake news and concatenate them, so that they will not give a biased prediction. 
I have also performed feature engineering on it and got a good accuracy with it.

[Github](https://github.com/reetika-goel/AlternusVera)
