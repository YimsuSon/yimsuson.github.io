---
title: 3.K-means clustering - kNN & K-means algorithm
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
  - Portfolio
tags: "ComputerVision"

---


### kNN algorithm

<br/>
<br/>

### 1. What is kNN - Nearest Neighbor algorithm

<br/>

- It is one of supervise train algorithm for classification or regression that look for train data of K number, where is mostly near by test data in feature space.


<br/>

![image](/assets/images/computervision/20200911_1.png)

<br/>

- NN vs kNN
    - NN : Nearest neighbor (k=1)


<br/>

![image](/assets/images/computervision/20200911_2.png)

<br/>

- KNN algorithm object creation

<br/>

``` c
cv2.ml.KNearest_create() -> retval
```

- retval : cv2.ml_KNearest object

<br/>


- Input data of classification using the KNN algorithm 

<br/>

``` c
cv.ml_KNearest.findNearest(samples, k, results=None, neighborResponses=None, dist=None, flgs=None) -> retval, results, neighborResposnes, dist
```
- samples : Input sample matric with input vector stored by row unit 

<br/>

- KNN algorithm poin classification example


<br/>

![image](/assets/images/computervision/20200911_3.png)

<br/>



### 2. KNN digit recognition

<br/>

- If it is the printed digit to setted font, Template matching is possible


<br/>

![image](/assets/images/computervision/20200911_5.png)

<br/>

- KNN digit recognition processing
    - Making coordination of one point from 400-dimension using pixel value of image 20 x 20
    - KNN algorithm point classification in 400-dimension space


<br/>

![image](/assets/images/computervision/20200911_6.png)

<br/>

- KNN digit recognition flow chart



<br/>

![image](/assets/images/computervision/20200911_7.png)

<br/>




### 2. k-means algorithm

- k-means algorithm
    - Cluster algorithm the given data divides section of k number
            ![image](/assets/images/computervision/20200914_8.png)


- Process
    1. Select random k number center
    2. Select nearest center to every data
    3. Recalculate center to each cluster
    4. Repeat 2~3 process, If center changed
    5. If not, it'll end



<br/>

![image](/assets/images/computervision/20200914_9.png)

<br/>


- Color image segment
    - Express each pixel value of input image to the one point of color space 
    - Perform k-means algorithm in color space
    - Translate each pixel value into representive color of k number

<br/>

![image](/assets/images/computervision/20200914_10.png)

<br/>


- K-mean cluster code

``` c 
cv2.kmeans(data, K, bestLabels, criteria, attempts, flags, centers=None) -> retval, bestLabels, centers
```

- data : train data matrix
- K : cluster number
- bestLabels : cluster set matrix of each sample
- criteria : finish standard
- attempts : repeating number to using another initial label
- flags : initial cent setting method
- centers : matrix for expressing the matrix
- retval : compatness measure  ![image](/assets/images/computervision/20200914_11.png)

<br/>

- k-means algorithm example


<br/>

![image](/assets/images/computervision/20200914_12.png)

<br/>

