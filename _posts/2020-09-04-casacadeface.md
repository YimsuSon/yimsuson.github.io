---
title: 5.Pedestrian Detection - Cascade classifier
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


### Cascade classifier

<br/>
<br/>

### 1. Casacde classifier : face detection

<br/>

- Viola - Jones face detection 
    - It could train positive image(face image)  and negative image(normal image) and detect accuratly face area.
    - Different point with before methods is that Haar-like feature, robust classifier function based on AdaBoost, rapid operation speed through cascade method are used.

<br/>

- Haar-like feature
    - Using the set of filter of rectangle form
    - Extracting the result value pixel value is minused from black rectangle area to whole white rectangle area.


<br/>

![image](/assets/images/computervision/20200904_1.png)

<br/>

- Cascade classifier
    - Although There is one or two face in normal image, other area is almost non-face area.
    - Conducting Mutistage inspection to skip Non-face are.


<br/>

![image](/assets/images/computervision/20200904_2.png)

<br/>


- CascadeClassifier code

<br/>

``` c
cv2.CascadeClassifier.detectMultiScale(image, scaleFactor=None, minNeighbors=None, flags=None, minSize=None, maxSize=None) -> result
```

- image : input image
- scaleFactor : image shrinkage ratio. default is 1.1
- minNeighbors: Specifying how many neighbor rectangle is detected to set to fianal detection area.
- flags : not use
- minSize : min object size
- maxSize : max object size
- result : numpy.ndarray put in rectangle information of detected object such as (x,y,w,h)


<br/>

![image](/assets/images/computervision/20200904_3.png)

<br/>

### 2. Hisgogram of Oriented Gradients (Hog)

- Hog
    - Using oriented gradient of image as feature vector
    - It's widely used to pedstrian detection mehod at CVPR conference in 2005



<br/>

![image](/assets/images/computervision/20200904_4.png)

<br/>

- The code Loading pre-learn clssifier coefficient for making HOG descriptor object or detecting pedestrian.

<br/>

``` c
cv2.HOGDescriptor() -> <CascadeClassifier object>
```
```
cv2.HOGDescriptor_getDefaultPeopleDetector() -> retval
```

- retval : pre-trained feature vector

<br/>

- Enrolling SVM classifier coefficient

<br/>

``` c
cv2.HOGDescriptor.setSVMDetector(svmdetector) -> None
```
<br/>

- svmdetector : coefficient for linear SVM classifier 

<br/>

- HOG multiscale object detection code

<br/>

``` c
cv2.HOGDescriptor.detectMultiScale(img, hitThreshold=None, winStride=None, padding=None, scale=None, finalThreshold=None, useMeanshiftGrouping=None) -> foundLocations, foundWeights
```
<br/>

- img : input image
- hitTreshold : Threshold for distance of between feature vector and SVM classifer plane
- winStride : Moving size of shall window
- padding : Padding size
- scale : Size ration of search window
- finalThreshold : Threshold for detection determination
- useMeanshiftGrouping : The method superimposed window combine
- foundLocations : Rectangle area information
- foundWeights : Confidence for rectangle area

<br/>

- HOG pedestrian detection result example



<br/>

![image](/assets/images/computervision/20200904_5.png)

<br/>
