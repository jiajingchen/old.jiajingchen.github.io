---
layout: post
title: Data Science Interview Questions Series Predictive modeling 1
---

Let's crack the data science interview together! Recently I found this amazing [120 Data Science Interview Questions](http://www.datasciencequestions.com) written by [William Chen](http://www.wzchen.com) and other data scientists. 

I shared it with some of my data science friends and classmates. We decided to first do all the problem set on our own and then discuss it together. Here is some of the answers I have for those questions. I also refer to other source like Google, Quora, Stack Overflow, etc.

Some useful link by the way:
- Here is the ["official" answers](https://datascienceinterview.quora.com/Answers-1) by the book author, but only part of the questions exposed. 
- [Here, The DS Interview](https://www.thedsinterview.com) is another interesting website about data science interview and how to prepare it. I like the UI design and kind of the game play behind it.

All right, let's get started with predictive modeling first!
------
### Q1 (Given a Dataset) Analyze this dataset and give me a model that can predict this response variable.

#### Ans:
This depends on the given dataset and the question behind the dataset. Generally, we need to clarify the type of prediction we want to implement. For supervised learning, we need to define whether it is a regression or classification problem.

### Q2 What could be some issues if the distribution of the test data is signicantly different than the distribution of the training data? 
#### Ans:

This is known as dataset shift.  [here](https://mitpress.mit.edu/books/dataset-shift-machine-learning) is a book and [slide](http://iwann.ugr.es/2011/pdf/InvitedTalk-FHerrera-IWANN11.pdf) about it.
Here are some reasons of dataset shift as follows:
- Covariate shift: 
training and test input follow different distributions, but functional relation remains unchanged.
- Sample selection bias: 
the training examples have been obtained through a biased method, such as non-uniform selection.
- Non-stationary environments: 
Training environment is different from the test one, whether it's due to a temporal or a spatial change. One typical scenario is adversarial classification problems, such as spam filtering and network intrusion detection.

The result of dataset shift is overfitting and producing high variance in the testing data.

Reference: [Quora](https://www.quora.com/What-could-be-some-issues-if-the-distribution-of-the-test-data-is-significantly-different-than-the-distribution-of-the-training-data)

### Q3 What are some ways I can make my model more robust to outliers? 
#### Ans:
- Minimize absolute error as cost function 
use minimizing absolute deviations (MAD) of errors instead of Minimizing square errors (MSE), becasue MAD is more robust to outliers while MSE are more sensitive and pulled towards the outliers. See Q4 for more details.
- Regularization, choosing L1 norm (lasso regression) instead of L2 norm (ridge regression)
- Use a model that's resistant to outliers. e.g. Tree-based methods.
Tree-based models are generally not as affected by outliers, while regression-based models are. If you're performing a statistical test, try a non-parametric test instead of a parametric one.


Reference: [Quora](https://www.quora.com/What-are-methods-to-make-a-predictive-model-more-robust-to-outliers)

### Q4 What are some differences you would expect in a model that minimizes squared error, versus a model that minimizes absolute error? In which cases would each error metric be appropriate?

#### Ans:

Both mean squared error (MSE) and absolute deviations (MAD) are used in predictive modeling. MSE has nice mathematical properties which makes it easier to compute the gradient. However, MAE requires more complicated tools such as linear programming to compute the gradient. Because of the square, large errors have relatively greater influence on MSE than do the smaller error. 
Minimizing square errors (MSE) is not the same as minimizing absolute deviations (MAD) of errors. MSE provides the **mean response** of $y$ conditioned on $x$, while MAD provides the **median response** of $y$ conditioned on $x$.

Now especially when considering the estimation of regressions (e.g. OLS), different penalty functions will yield different results. Using the linearly proportional penalty function, the regression will assign less weight to outliers than when using the squared proportional penalty function. The Median Absolute Deviation (MAD) is therefore known to be a more robust estimator. In general, it is therefore the case that a robust estimator fits most of the data points well but **ignores outliers**. A least squares prevents large errors better, and fit, in comparison, is **pulled more towards the outliers**. If you have a data set with an extreme outlier due to a data acquisition error, minimizing squared error will pull the fit towards the extreme outlier much more than minimizing absolute error. That being said, it's usually better to use squared error.

Here is a visualization for comparison:(from Reference)

![_config.yml]({{ site.baseurl }}/images/post/msemad.png)

reference: [Stack Exchange](https://stats.stackexchange.com/questions/147001/is-minimizing-squared-error-equivalent-to-minimizing-absolute-error-why-squared),[Quora](https://www.quora.com/What-is-the-difference-between-squared-error-and-absolute-error)

### Q5 What error metric would you use to evaluate how good a binary classifier is? What if the classes are imbalanced? What if there are more than 2 groups?

#### Note: This is a very common and important question about the performance of a classifier or predictor. In fact I was asked about this question nearly every time when it was a technical interview and we were talking about machine learning and prediction.

#### Ans:

There are several measure we can evaluate a classifier and some are used under special scenario like imbalanced data or more than 2 group problem. Let's look at some general measure first:


- What error metric would you use to evaluate how good a binary classifier is?
**Accuracy**


**AUC**
[ROC curve](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)

**F score**
In statistical analysis of binary classification, the [F score](https://en.wikipedia.org/wiki/F1_score) (also F-score or F-measure) is a measure of a test's accuracy. It considers both the precision p and the recall r of the test to compute the score: p is the number of correct positive results divided by the number of all positive results returned by the classifier, and r is the number of correct positive results divided by the number of all relevant samples. Relevant is equivalent to actually having the disease. The F1 score is the harmonic average of the precision and recall, where an F1 score reaches its best value at 1 (perfect precision and recall) and worst at 0.


- What if the classes are imbalanced?

Precision-Recall instead of ROC curve.

 If you are again dealing with an unbalanced dataset, you have two options for averaging: macro-averaging and micro-averaging. Micro-averaged F will give you a sense of how well you do on the large classes, while the macro-average will give you a sense for the small classes. See chapter 13 of [Introduction to Information Retrieval](https://nlp.stanford.edu/IR-book/) for details.
 
- What if there are more than 2 groups?

If you are dealing with multiclass classification, one standard thing you could do is calculate the F-score per class and then average the results.

Reference: [Evaluation metrics for binary classification](http://www.sergulaydore.com/evaluation-metrics-for-binary-classification/), Quora

More questions and answers to come next...