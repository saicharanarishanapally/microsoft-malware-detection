# microsoft malware detection


## Business/Real-world Problem
###  What is Malware?

The term malware is a contraction of malicious software. Put simply, malware is any piece of software that was written with the intent of doing harm to data, devices or to people.
Source: https://www.avg.com/en/signal/what-is-malware

## Problem Statement

In the past few years, the malware industry has grown very rapidly that, the syndicates invest heavily in technologies to evade traditional protection, forcing the anti-malware groups/communities to build more robust softwares to detect and terminate these attacks. The major part of protecting a computer system from a malware attack is to identify whether a given piece of file/software is a malware.
## Source/Useful Links

Microsoft has been very active in building anti-malware products over the years and it runs it’s anti-malware utilities over 150 million computers around the world. This generates tens of millions of daily data points to be analyzed as potential malware. In order to be effective in analyzing and classifying such large amounts of data, we need to be able to group them into groups and identify their respective families.

This dataset provided by Microsoft contains about 9 classes of malware. ,

Source: https://www.kaggle.com/c/malware-classification
## Real-world/Business objectives and constraints.

    Minimize multi-class error.
    Multi-class probability estimates.
    Malware detection should not take hours and block the user's computer. It should fininsh in a few seconds or a minute.

# Machine Learning Problem
##  Data
### 2Data Overview
Source : https://www.kaggle.com/c/malware-classification/data
For every malware, we have two files

    .asm file (read more: https://www.reviversoft.com/file-extensions/asm)
    .bytes file (the raw data contains the hexadecimal representation of the file's binary content, without the PE header)

Total train dataset consist of 200GB data out of which 50Gb of data is .bytes files and 150GB of data is .asm files:
Lots of Data for a single-box/computer.
There are total 10,868 .bytes files and 10,868 asm files total 21,736 files
There are 9 types of malwares (9 classes) in our give data
Types of Malware:

    Ramnit
    Lollipop
    Kelihos_ver3
    Vundo
    Simda
    Tracur
    Kelihos_ver1
    Obfuscator.ACY
    Gatak


## Mapping the real-world problem to an ML problem
### Type of Machine Learning Problem

There are nine different classes of malware that we need to classify a given a data point => Multi class classification problem
###  Performance Metric

Source: https://www.kaggle.com/c/malware-classification#evaluation

Metric(s):

    Multi class log-loss
    Confusion matrix

###  Machine Learing Objectives and Constraints

Objective: Predict the probability of each data-point belonging to each of the nine classes.

Constraints:

    Class probabilities are needed.
    Penalize the errors in class probabilites => Metric is Log-loss.
    Some Latency constraints.

## Train and Test Dataset

Split the dataset randomly into three parts train, cross validation and test with 64%,16%, 20% of data respectively

# Exploratory Data Analysis
##  Distribution of malware classes in whole data set 

## Feature extraction
### File size of byte files as a feature
###  box plots of file size (.byte files) feature
### feature extraction from byte files 
### Multivariate Analysis 
Train Test split

# Machine Learning Models
##  Machine Leaning Models on bytes files
###  Random Model
### K Nearest Neighbour Classification
### Logistic Regression
### Random Forest Classifier 

###  XgBoost Classification

### XgBoost Classification with best hyper parameters using RandomSearch

##  Modeling with .asm files

There are 10868 files of asm 
All the files make up about 150 GB
The asm files contains :
1. Address
2. Segments
3. Opcodes
4. Registers
5. function calls
6. APIs
With the help of parallel processing we extracted all the features.In parallel we can use all the cores that are present in our computer.


Here we extracted 52 features from all the asm files which are important.

We read the top solutions and handpicked the features from those papers/videos/blogs. 
 Refer:https://www.kaggle.com/c/malware-classification/discussion

### Feature extraction from asm files

To extract the unigram features from the .asm files we need to process ~150GB of data
Note: Below two cells will take lot of time (over 48 hours to complete)
We will provide you the output file of these two cells, which you can directly use it
### Univariate analysis on asm file features
### Multivariate Analysis on .asm file features 
## Train and test split

##  Machine Learning models on features of .asm files
###  K-Nearest Neigbors
### Logistic Regression 
###  Random Forest Classifier
###  XgBoost Classifier
###  Xgboost Classifier with best hyperparameters
###  Multivariate Analysis on final fearures
###  Train and Test split
###  Random Forest Classifier on final features
###  XgBoost Classifier on final features
### 4 XgBoost Classifier on final features with best hyper parameters using Random search
### N-Gram(2-Gram, 3-Gram, 4-Gram) Opcode Vectorization
### Image Feature Extraction From ASM Files
### First 200 Image Pixels
### Important Feature Selection Using Random Forest
### Important Feature Selection Using Random Forest
### Important Feature Among Opcode BI-Gram,3-Gram,4-Gram
### Important Feature Among Byte Bi-Gram

# Advanced features
Adding 300 bytebigram,200 opcode bigram,200 opcode trigram,200 opcode tetragram ,first 200 image pixels
Machine Learning Models on ASM Features + Byte Features + Advanced Features
## Comparision between all models 
|MODEL                      |         FEATURES                      |          |
|---------------------------|---------------------------------------|----------|
|           random          |               Byte files              |   2.45   |
|           knn             |               Byte files              |   0.48   |
|    Logistic Regression    |               Byte files              |   0.52   |
| Random Forest Classifier  |               Byte files              |   0.06   |
|   XgBoost Classification  |               Byte files              |   0.07   |
|                           |                                       |          |
|                           |                                       |          |
|            knn            |                asmfiles               |   0.21   |
|    Logistic Regression    |                asmfiles               |   0.38   |
| Random Forest Classifier  |                asmfiles               |   0.03   |
|   XgBoost Classification  |                asmfiles               |   0.04   |
|                           |                                       |          |
|                           |                                       |          |
| Random Forest Classifier  |          Byte files+asmfiles          |   0.04   |
|   XgBoost Classification  |          Byte files+asmfiles          |   0.02   |
|                           |                                       |          |
|                           |                                       |          |
|    Logistic Regression    | Byte files+asmfiles+advanced features |   1.12   |
|   XgBoost Classification  | Byte files+asmfiles+advanced features |   0.01   |
