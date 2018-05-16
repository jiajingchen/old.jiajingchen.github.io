---
layout: post
title: The Deep Learning Project: Facial Expression Classification, CNN
---

This semester I took BST261: Data Science II, mostly about deep learning in Python. The final project is using CNN in Facial Expression Classification.

### The Data

Our project is from Kaggle competition--[Facial Expression Recognition Challenge] (https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge)
The "fer2013" dataset can be downloaded at the Kaggle website. 
The data consists of 48x48 pixel grayscale images of faces. The faces have been automatically registered so that the face is more or less centered and occupies about the same amount of space in each image. The task is to categorize each face based on the emotion shown in the facial expression in to one of seven categories (0=Angry, 1=Disgust, 2=Fear, 3=Happy, 4=Sad, 5=Surprise, 6=Neutral).

The original training set consists of 28,709 examples. The original test set consists of 3,589 examples. However, due to the limitation of computational resource(we don't want to crash our JupyterHub or our own computer), we are only using a fraction of the original dataset.  The fraction we choose will then be determined by the learning performance and computational time.

### The code
Here is my [Github repo](https://github.com/jiajingchen/Deep-Learning-Project-Facial-Expression-Classification) for this project.

