---
title: 4.Model Overfitting
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

### 1.Model Overfitting
    - Reason for Model Overfitting

        - Limited Training Size

        - High Model Complexity

            - Multiple Comparison Procedure

    - Classification Errors

        - Training errors (apparent errors)
            - Errors committed on the training set

        - Test errors
            - Errors committed on the test set

        - Generalization errors
            - Expected error of a model over random selection of records from same distribution


    - Effect of Multiple Comparison Procedure
        - Consider the task of predicting whether stock market will rise/fall in the next 10 trading days

        - Random guessing:
            - P(correct) = 0.5

        - Make 10 random guesses in a row:

    - Approach:
        - Get 50 analysts
        - Each analyst makes 10 random guesses
        - Choose the analyst that makes the most number of correct predictions

    - Probability that at least one analyst makes at least 8 correct predictions

    - Many algorithms employ the following greedy strategy:
        - Initial model: M
        - Alternative model: M’ = M ∪ γ,   where γ is a component to be added to the model (e.g., a test condition of a decision tree)
        - Keep M’ if improvement, Δ(M,M’) > α

    - Often times, γ is chosen from a set of alternative components, Γ = {γ1, γ2, …, γk}

    - If many alternatives are available, one may inadvertently add irrelevant components to the model, resulting in model overfitting


    - Notes on Overfitting

        - Overfitting results in decision trees that are more complex than necessary

        - Training error does not provide a good estimate of how well the tree will perform on previously unseen records

        - Need ways for estimating generalization errors


### 2.Model Selection
- Using Validation Set
    - Performed during model building

    - Purpose is to ensure that model is not overly complex (to avoid overfitting)

    - Need to estimate generalization error
        - Using Validation Set
        - Incorporating Model Complexity
        - Estimating Statistical Bounds

    - Using Validation Set

        - Divide training data into two parts:
            - Training set: 
                - use for model building
            - Validation set: 
                - use for estimating generalization error
                - Note: validation set is not the same as test set

            - Drawback:
                - Less data available for training


- Incorporating Model Complexity
    - Rationale: Occam’s Razor
        - Given two models of similar generalization errors,  one should prefer the simpler model over the more complex model

        - A complex model has a greater chance of being fitted accidentally

        - Therefore, one should include model complexity when evaluating a model

        - Gen. Error(Model) = Train. Error(Model, Train. Data) + x Complexity(Model)


- Estimating Statistical Bounding
        - Pessimistic Error Estimate of decision tree T with k leaf nodes


- Model Selection for Decision Trees

    - Pre-Pruning (Early Stopping Rule)
        - Stop the algorithm before it becomes a fully-grown tree
        - Typical stopping conditions for a node:
            - Stop if all instances belong to the same class
            - Stop if all the attribute values are the same
        - More restrictive conditions:
            - Stop if number of instances is less than some user-specified threshold
            - Stop if class distribution of instances are independent of the available features (e.g., using χ 2 test)
            - Stop if expanding the current node does not improve impurity    measures (e.g., Gini or information gain).
            - Stop if estimated generalization error falls below certain threshold

    - Post-pruning
        - Grow decision tree to its entirety
        - Subtree replacement
            - Trim the nodes of the decision tree in a bottom-up fashion
            - If generalization error improves after trimming, replace sub-tree by a leaf node 
            - Class label of leaf node is determined from majority class of instances in the sub-tree
        - Subtree raising
            - Replace subtree with most frequently used branch


### 3.Model  Evaluation 


- Purpose: 
    - To estimate performance of classifier on previously unseen data (test set)

- Holdout
    - Reserve k% for training and (100-k)% for testing 
    - Random subsampling: repeated holdout
- Cross validation
    - Partition data into k disjoint subsets
    - k-fold: train on k-1 partitions, test on the remaining one
    - Leave-one-out:   k=n


- Variations on Cross-validation

    - Repeated cross-validation
        - Perform cross-validation a number of times
        - Gives an estimate of the variance of the generalization error
    - Stratified cross-validation
        - Guarantee the same percentage of class labels in training and test
        - Important when classes are imbalanced and the sample is small
    - Use nested cross-validation approach for model selection and evaluation

