# Project 3: Web APIs & Classification
---

## Subreddit Post Classification

### Problem Statement

The goal of this project is to use NLP to train a classifier to predict from which of 2 subreddits a given post comes from. 2 models will be compared in this project, namely a Naive Bayes classifier and a logistic regression model. The baseline accuracy is essentially the percentage of total posts belonging to the subreddit with more posts out of the 2 chosen subreddits. The model will be deemed to have achieved success upon exceeding the baseline accuracy score. 

The 2 subreddits chosen are Cheap_Meals and EatCheapAndHealthy. As the names of the subreddits suggest, the difference between the 2 subreddits lies in whether a given recipe/ meal is considered to be healthy. The target audience for this project will be people who are concerned about following a healthy diet, and who will want to know if the cheap meal is actually healthy. Practically, a successful model should also return a high sensitivity score, which would mean fewer posts were wrongly predicted to belong to the EatCheapAndHealthy subreddit (i.e. fewer wrong predictions that the food is healthy when it is not).


### Data Collection, Cleaning, EDA

A total of 1436 posts were collected from the 2 subreddits using Reddit's API, comprising 686 posts from the Cheap_Meals subreddit and 750 posts from the EatCheapAndHealthy subreddit. Thought was given to Reddit's server receiving the requests by using Python's `time.sleep()` function to pause the program in between requests (Reddit will give 25 posts per request).

Duplicate subreddit posts were subsequently dropped. The information stored in the DataFrame were namely the subreddit post title, text and subreddit (i.e. name of the subreddit the given post belonged to). As almost 97% of posts from Cheap_Meals subreddit do not contain text, the "text" feature was then dropped. The upper case letters in the subreddit post titles were converted to lower case, and thereafter only lower case letters were kept in the title feature without the punctuations. Lastly, the target column was binarised, in which the Cheap_Meals subreddit was represented by 1 and the EatCheapAndHealthy subreddit was represented by 0.


### Modelling

The baseline accuracy score is 0.522.

The following models were trained:
* Multinomial Bayes Classifier Model with CountVectorizer
* Gaussian Bayes Classifier Model with TF-IDF
* Logistic Regression Model with CountVectorizer
* Logistic Regression Model with TF-IDF


### Findings, Conclusions and Recommendations

Multinomial Bayes Classifier Model with CountVectorizer returned the highest accuracy score of 0.833, accompanied with a sensitivity score of 0.825. The model had no maximum number of features and stopwords were kept for the CountVectorizer.

Gaussian Bayes Classifier Model with TF-IDF returned the highest sensitivity score of 0.848, accompanied with an accuracy score of 0.752.

Despite being cheap, healthy meals appear to be not as well-received/ enjoyed by Redditors. From Sentiment Analysis, EatCheapAndHealthy post titles have a mean negative sentiment score (0.045) that is 3 times that for Cheap_Meals (0.016).

As the text feature of subreddit posts were dropped altogether since majority of posts from the Cheap_Meals subreddits contain photos and no words, image captioning can be explored to generate meaningful words from visual interpretation of the pictures.
