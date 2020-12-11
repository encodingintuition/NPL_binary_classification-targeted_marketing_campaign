# Subreddit Classification

Theoretical project: StarWars Corporate would like to have an overwhelming turnout of fans for the Comic Con 2021.  To achieve this, Disney is sending loyalty rewards to their fans on the subbredit StarWars, offering a secret $15 discount off ComicCon 2021 entry fee.  The promotion is only for participants on the StarWars subreddit, therefore corporate want to make sure that only StarWars fans receive this promotions.

## Problem Statment 

To create a model that can classify between two similar subreddit, specifically to correctly classify posts belonging Starwars and StarTek subreddit posts. 

Our primary metric was Accuracy and Precision, to identify which subreddit is StarWars (TP).

## Executive Summary 

We used the PushShift API to scrape 9,000 Startrek and 23,700 StarWars subreddit posts to be used as training data this model.  After exploratory data analysis was done it was realized that because many StarWars subreddits where incompete from being 'deleted' or 'removed' we had to scrape substantially more StarWars posts to have balanced classes.

We ran basic models with Naive Bayes, Logistic Regression, Random Forest, and Adaboost Classifier, each paired with TfidfVectorizer and CountVectorizer.

We created custom stop words, used lemmatization, and used the hyperperamiters within CountVectorizer to gain to improve our accuracy and precision score. 

The best tuned model was Naive Bayes with count vecttorizer, with an accuracy score of .9771 and a precision score of .9906.

## Contents

- 00-reddit_digger.ipynb
- 01-Data_clean-proj_3.ipynb
- 02-basic_modeling-proj_3.ipynb
- 03-nbayesGS_proj_3.ipynb



### NoteBook 00 - Webscrapping 

    A function was created utilizing PushShift API to scrape data from both StarWars and StarTrek subreddits.  Each scrape took 2500 posts of a single subreddit and saved it as a CSV file.  Data was collected to equal out ~ 6,000 posts per class.   

### NoteBook 01 - Data Cleaning and Exploratory Data Analysis

    Data cleaning was done separtly for both subreditts to insure that equal samples of each subredit was used, then the data was concated. 

    During the cleaning of the data it was noticed that many of the reddit posts had a large number of NaN values with in its 'selfText tag'. StarWars reddit had a proportionate number of NaN compared to starwars.

    We also found that a number of selftexts where '[deleted]' or '[removed]' leaving their selftext unusable. We deleted all instences of both '[deleted]' or '[removed]' to insure the our data was the most complete.

    By the time we ran our final models we had collected 23,700, StarWars subReddits and 9,000 Startrek subreddits. Of this original data 5,712 Starwars subReddits and 6,000 startrek subReddits were used to run within our models.

### NoteBook 02 - Basic Modeling 

    Using the metric of accuracy and Precision we trained / tested a base model of Naive Bayes, Logistic Regression, Random Forest and Adaboost classifier models, each paired with TfidfVectorizer and CountVectorizer.

    Using this Rubric we found that Naive Bayes with Count Vectorizer yeilds the highest performence.

##### Baseline Score:
    At random there is a 51% chance that a sample from our data will be a Starwars class.

### NoteBook 02 - Naive Bayes Modeling 

    Naive Bayes:
    The Naive Bayes is a probabilistic algorithm. The features within this model are the words and their frequency. Bayes calculates the probability of each word using its frequency and naive bayes assumes every word is independent of the others. 

    Naive bayes strengths is that is easy to implement, it has a short training time, and it assumes that all attributes(features) are mutually independent.  This idea of mutual independence gives it probabilistic strength but is also a gentle weakness, because it does not parallel the real world were many things are partly or fully interdependet of each other. This is very true for words in a sentence were one word is linked to another because of the very nature the syntax of our language. 

    Combining Data 
    We discovered that when the 'title' & 'subtext' feature from each post was combined a inprovement in accuracy was had. 

    StopWords & Lemmatization
    We compiled the most commonly used words into a DataFrame and examined it to see what words could be added to our standard libary of stop words.  In addition we created a function to add lemmatzation to our countvectorizer.

    Hyper tuning:
    We trained / tested the model through a gridsearch to uncover the best hyper parameters for both the Naive Bayes alogrithm and the Count Vectorizer 


## Conclusion

In conclusion, we discovered the best model for solving our problem statement is Naive Bayes, scoring an accuracy score of .9771 and a precision score of .9906 on our test data. With this model Starwars corporate will confidently know which is a Starwars subbreddit and be able to offer them the secret $15 discount off ComicCon 2021 entry fee.

## Areas of Future Studies

We plan to further tune the hyperparameters within our model and look into using a Neural Networks in place of the Naive Bayes.  We also would like to test this model randomly against other subreddit groups that will also have spectators at ComicCon 2021.



```python

```


```python

```


```python

```
