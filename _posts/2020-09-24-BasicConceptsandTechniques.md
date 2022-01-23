---
title: 3.Classification, Basic Concepts and Techniques
excerpt: Computer Science


#최상위 사진
header:
  image: /assets/images/foo-bar-identity.jpg
  teaser: /assets/images/foo-bar-identity-th.jpg

gallery:
  - url: /assets/images/unsplash-gallery-image-1.jpg
    image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
  - url: /assets/images/unsplash-gallery-image-2.jpg
    image_path: assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
  - url: /assets/images/unsplash-gallery-image-3.jpg
    image_path: assets/images/unsplash-gallery-image-3-th.jpg
    alt: "placeholder image 3"
    


 #사이드바 설정 
sidebar:
  - title: "Role"
    nav: sidebar-sample

# 해당 글 목차
toc: true
toc_sticky: true

toc_label: "Yimsu's Blog"
toc_icon: "cog"


## 테그설정

categories:
  - DataMining

tags:
  - DataMining
  - "2020"
  - "2020.09"



---

### 1. Classification: Definition

- Given a collection of records (training set )
    - Each record is by characterized by a tuple (x,y), where x is the attribute set and y is the class label
        - x: attribute, predictor, independent variable, input
        - y: class, response, dependent variable, output

- Task:
    - Learn a model that maps each attribute set x into one of the predefined class labels y


### 2. General Framework for Classification

- Classification Techniques
    - Base Classifiers
        - Decision Tree based Methods
        - Rule-based Methods
        - Nearest-neighbor
        - Neural Networks
        - Deep Learning
        - Naïve Bayes and Bayesian Belief Networks
        - Support Vector Machines

    - Ensemble Classifiers
        - Boosting, Bagging, Random Forests


    - Many Algorithms:
        - Hunt’s Algorithm (one of the earliest)
        - CART
        - ID3, C4.5
        - SLIQ,SPRINT


### 3. Decision Tree Classifier 

- 3.1. Basic Algorithm to Build a Decision Tree : Hunt’s Algorithm
    - Let Dt be the set of training records that reach a node t

General Procedure:
    - If Dt contains records that belong the same class yt, then t is a leaf node labeled as yt
    
    - If Dt contains records that belong to more than one class, use an attribute test to split the data into smaller subsets. Recursively apply the procedure to each subset.

Design Issues of Decision Tree Induction
    - How should training records be split?
        - Method for specifying test condition 
            - depending on attribute types
    - Measure for evaluating the goodness of a test condition

How should the splitting procedure stop?
    - Stop splitting if all the records belong to the same class or have identical attribute values
    - Early termination 


- 3.2 Methods for Expressing Test Conditions

    - Depends on attribute types
        - Binary
        - Nominal
        - Ordinal
        - Continuous

    - Depends on number of ways to split
        - 2-way split
        - Multi-way split
            - Use as many partitions as distinct values. 
            - Use as many partitions as distinct values
        - Binary split 
            - Divides values into two subsets
            - Preserve order property among attribute values

Different ways of handling
    - Discretization to form an ordinal categorical attribute
        - Ranges can be found by equal interval bucketing, equal frequency bucketing (percentiles), or clustering.
            - Static – discretize once at the beginning
            - Dynamic – repeat at each node

Binary Decision: (A < v) or (A ≥ v)
    - consider all possible splits and finds the best cut
    - can be more compute intensive


- 3.3 Measures for Selecting an Attribute Test Condition
    - 3.3.1 Measure of Impurity: GINI
    - 3.3.2 Measure of Impurity: Entropy 
    - 3.3.3 Measure of Impurity: Classification Error

How to determine the Best Split

    - Greedy approach: 
        - Nodes with purer class distribution are preferred

    - Need a measure of node impurity:


Measures of Node Impurity

    - Gini Index

        - Maximum  of ￼when records are equally distributed among all classes, implying the least beneficial situation for classification
        - Minimum  of 0 when all records belong to one class, implying the most beneficial situation for classification

    - Entropy




    - Misclassification error


Finding the Best Split

    - Compute impurity measure (P) before splitting
    - Compute impurity measure (M) after splitting
        - Compute impurity measure of each child node
        - M is the weighted impurity of child nodes
    - Choose the attribute test condition that produces the highest gain




Binary Attributes: Computing GINI Index

    - Splits into two partitions (child nodes)
    - Effect of Weighing partitions: 
    - Larger and purer partitions are sought



Categorical Attributes: Computing Gini Index
- For each distinct value, gather counts for each class in the dataset
- Use the count matrix to make decisions




- 3.4 Decision Tree Based Classification




- Advantages:
    - Inexpensive to construct
    - Extremely fast at classifying unknown records
    - Easy to interpret for small-sized trees
    - Robust to noise (especially when methods to avoid overfitting are employed)
    - Can easily handle redundant or irrelevant attributes (unless the attributes are interacting)

Disadvantages: 
    - Space of possible decision trees is exponentially large. Greedy approaches are often unable to find the best tree.
    - Does not take into account interactions between attributes
    - Each decision boundary involves only a single attribute
