PredictionAssignment
=======================
Practical Machine Learning - Prediction Assignment Writeup

Summary
--------
This document is the final report of the Peer Assessment project from the Practical Machine Learning course, which is a part of the Data Science Specialization. It was written and coded in RStudio, using its knitr functions and published in the html format. The purpose of this analysis is to predict the manner in which the six participants performed the exercises described below and to answer the questions of the associated course quiz. The machine learning algorithm, which uses the classe variable in the training set, is applied to the 20 test cases available in the test data. The predictions are submitted to the Course Project Prediction Quiz for grading.

Introduction
-------------
Devices such as Jawbone Up, Nike FuelBand, and Fitbit can enable collecting a large amount of data about someone’s physical activity. These devices are used by the enthusiasts who take measurements about themselves regularly to improve their health, to find patterns in their behavior, or because they are tech geeks. However, even though these enthusiasts regularly quantify how much of a particular activity they do, they rarely quantify how well they do it. In this project, the goal is to use data from accelerometers on the belt, forearm, arm, and dumbell of six participants. They were asked to perform barbell lifts correctly and incorrectly in five different ways.

More information is available from the following website: http://groupware.les.inf.puc-rio.br/har (see the section on the Weight Lifting Exercise Dataset).

Source of Data
--------------
The data for this project can be found on the following website:

http://groupware.les.inf.puc-rio.br/har.

The training data for this project:

https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv

The test data for this project:

https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv

The full reference is as follows:

Velloso, E.; Bulling, A.; Gellersen, H.; Ugulino, W.; Fuks, H. “Qualitative Activity Recognition of Weight Lifting Exercises. Proceedings of 4th International Conference in Cooperation with SIGCHI (Augmented Human ’13)”. Stuttgart, Germany: ACM SIGCHI, 2013.

Data Loading and Cleaning
-------------------------

Load the required R packages and set a seed.
``` r
library(lattice)
library(ggplot2)
library(caret)
library(rpart)
library(rpart.plot)
library(corrplot)
library(rattle)
library(randomForest)
library(RColorBrewer)
``` 
``` r
set.seed(1813)
``` 
Load the training and test datasets.
``` r
url_train <- "http://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv"
url_quiz  <- "http://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv"
``` 
``` r
data_train <- read.csv(url(url_train), strip.white = TRUE, na.strings = c("NA",""))
data_quiz  <- read.csv(url(url_quiz),  strip.white = TRUE, na.strings = c("NA",""))
``` 
``` r
dim(data_train)
``` 
``` r
## [1] 19622   160
``` 
``` r
dim(data_quiz)
``` 
``` r
## [1]  20 160
```
