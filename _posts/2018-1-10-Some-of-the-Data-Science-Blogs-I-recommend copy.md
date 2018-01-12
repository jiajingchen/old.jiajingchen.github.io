---
layout: post
title: Data Science Interview Questions Series Predictive modeling 2
---


### Q6 What are various ways to predict a binary response variable? Can you compare two of them and tell me when one would be more appropriate? What’s the difference between these? (SVM, Logistic Regression, Naive Bayes, Decision Tree, etc.)

#### Ans:
Yet another frequent asked question! Well, let's list some popular approaches and their pros and cons.
- Logistic Regression
Lots of ways to regularize your model, and you don't have to worry as much about your features being correlated, like you do in Naive Bayes. You also have a nice probabilistic interpretation, unlike decision trees or SVMs, and you can easily update your model to take in new data (using an online gradient descent method), again unlike decision trees or SVMs. Use it if you want a probabilistic framework (e.g., to easily adjust classification thresholds, to say when you're unsure, or to get confidence intervals) or if you expect to receive more training data in the future that you want to be able to quickly incorporate into your model.

- SVM
pros:SVM maximizes margin, so the model is slightly more robust (compared to linear regression). SVM supports kernels, so you can model even non-linear relations.
High accuracy, nice theoretical guarantees regarding overfitting, and with an appropriate kernel they can work well even if your data isn't linearly separable in the base feature space. Especially popular in text classification problems where very high-dimensional spaces are the norm. 

cons: Memory-intensive and kind of annoying to run and tune.

- Decision Tree
Easy to interpret and explain (for some people -- I'm not sure I fall into this camp). Non-parametric, so you don't have to worry about outliers or whether the data is linearly separable (e.g., decision trees easily take care of cases where you have class A at the low end of some feature x, class B in the mid-range of feature x, and A again at the high end).

Their main disadvantage is that they easily overfit, but that's where ensemble methods like random forests (or boosted trees) come in. Plus, random forests are often the winner for lots of problems in classification (usually slightly ahead of SVMs, I believe), they're fast and scalable, and you don't have to worry about tuning a bunch of parameters like you do with SVMs, so they seem to be quite popular these days.

- Random forest

- Naive Bayes

Super simple, you're just doing a bunch of counts. If the NB conditional independence assumption actually holds, a Naive Bayes classifier will converge quicker than discriminative models like logistic regression, so you need less training data. And even if the NB assumption doesn't hold, a NB classifier still often performs surprisingly well in practice

-How large is your training set?

If your training set is small, high bias/low variance classifiers (e.g., Naive Bayes) have an advantage over low bias/high variance classifiers (e.g., kNN or logistic regression), since the latter will overfit. But low bias/high variance classifiers start to win out as your training set grows (they have lower asymptotic error), since high bias classifiers aren't powerful enough to provide accurate models. 

You can also think of this as a generative model vs. discriminative model distinction.

Reference: [Quora](https://www.quora.com/What-are-the-advantages-of-different-classification-algorithms)
### Q7 What is regularization and where might it be helpful? What is an example of using regularization in a model?


#### Ans:

### Q8 Why might it be preferable to include fewer predictors over many?

#### Ans:

### Q9 Given training data on tweets and their retweets, how would you predict the number of retweets of a given tweet after 7 days after only observing 2 days worth of data?

#### Ans:

### Q10 How could you collect and analyze data to use social media to predict the weather?

#### Ans:
More questions and answers to come next...