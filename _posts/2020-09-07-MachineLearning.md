---
title: Machine Learning
excerpt: Computer Vision


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
  - ComputerVision
tags: "ComputerVision"

---


### Machine Learnigng

<br/>
<br/>

### 1. What is Machine Learing

<br/>

- The computer system use to perform specific task with out sing explicit instructions, relying on pattern and inference instead.


<br/>

![image](/assets/images/computervision/20200907_1.png)

<br/>

- IRIS classification used by machin learning
    - IRIS variety : Setosa VS Versicholor
    - The classification by lenght of petal and sepal


<br/>

![image](/assets/images/computervision/20200907_2.png)

<br/>



![image](/assets/images/computervision/20200907_3.png)

<br/>

- Sort of machine learning 

<br/>

![image](/assets/images/computervision/20200907_4.png)

<br/>

- OpenCV machine learning class

<br/>

![image](/assets/images/computervision/20200907_5.png)

<br/>

![image](/assets/images/computervision/20200907_6.png)

<br/>


- ANN_MLP : Aritificial neural network and multi-layer perceptron can train serveral hidden layer including neural network, expecting the reult for input data.

<br/>

- DTrees : Binary decision trees algorithm, DTrees class play a role in parents class of Rtree class and boost class which are realized random tree algorithm and boosting algorithm 

<br/>

- Boost : Boostring algorithm. The method make good classifier that givet to appropriate weight at the number of weak classifier.

<br/>

- RTrees : Random tree or random forest algorithm. It predict input feature vector using many tree, conducting classification or regression putting togheter the results.

<br/>

- EM : Clustering algorithm using expectation maximaization and gaussian mixture.

<br/>

- KNearest : K-Nearest Neighbors algorithm. It could find train data of K, specifing the sample data class has largest number data.

<br/>

LogisticRegression : binaray classification algorithm

<br/>

NormalBayesClassifier : Regular bayes classifer. It assume the feature vector follow normal distribution. Therefore, Whole data distribution could express gaussian mixtrue model. Normal bayes classifier calculate convariance matrix and average vector of each class from train data and it use to predict.

<br/>

SVM : Support vector machine algorithm. It find focal plane separating
data of two class. Using kernel method could adapt to non linear data classification.

<br/>

- Machine learning algorithm train

<br/>

``` c
cv2.ml_StatModel.train(samples, layout, responses) -> retval
```

<br/>

- samples : train data matrix
- layout : train data set method
- responses : Response matrix for each train data
- retval : If train is sucess, It will print True

<br/>

- Machine learning algorithm predect

<br/>

``` c
cv2.ml_StateModel.predict(samples, result=None, flags=None) -> retval, results
```

<br/>

- samples : the matrix stored input vector to row unit
- results : the matrix stored predict result such as classification or regression for each sample data
- flags : additional flag. default is 0
- retval : It is different depends on algorithm 



