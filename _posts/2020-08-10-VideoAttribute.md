---
title: Attribute of Video and reference pixel value
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


### Attribute of Video and reference pixel value

<br/>
<br/>

### 1. Open CV express the video data to use numpy.ndarray

|-|
|-|
|import cv2 <br/> img1 = cv2.imread('cat.bmp',cv2.IMREAD_GRAYSCALE) <br/> img2 = cv2.imread('cat.bmp',cv2.IMREAD_COLOR)|

- ndim : the number of dimension. = len(img.shape)
- shape : the size of each dimension. * Grayscale = (h,w), Colorscale = (h,w,3)
- size : Total number of elements
- dytp : Data type of elements. ex) Video data is uint8

<br/>
<br/>

### 2. OpenCV data type and Numpy data type

|-|-|-|
|cv.CV_8U|numpy.unint8|8-bit unsigned integer|
|cv.CV_16S|numpy.int16|16-bit signed integer|
|cv.CV_32F|numpy.float32|32-bit floating point|

- Grayscale Video : cv2.CV_8UC1 -> numpy.uint8, shape = (h,w)
- Colorscale Video : cv2.CV_8UC1 -> numpy.uint8, shape = (h,w,3)

<br/>
<br/>

### 3. Mask Operation and ROI

- ROI
    - Region of Interest
    - Specific region that could special operation in the video.

- Mask Operation 
    - OpenCV support ROI operaion to some of function when it do the mask Video should be converted.
    - Generally, Mask video is used through the binary image ,which is composed of 0 or 255.


- Pixel value copy function supporting mask operation.

``` c
cv2.copyTo(src,maks,dst=None) -> dst
```

- src : input video
- mask : mask video
- sdt : output layer



