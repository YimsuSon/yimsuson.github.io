---
title: Specific color area extraction
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

### Specific color area extraction

<br/>
<br/>

### 1. Detection matrix elements in specific range
``` c
cv2.inRange(src,lowerb,upperb,dst=None) -> dst
```

- src : input matrix
- lowerb : lower bound matrix or scalar
- upperb : upper bound matrix or scalar
- dst : mask video of same size as input video

<br/>

### 2. Histogram backprojection

- The method that check how much the histogram model given by each pixel of video matchs.

1) Calculate specific color histogram from standart video and mask video.
2) Select the pixel corresponded to specific color histogram that calculated pre-acuired color.

``` c
cv2.calcBackProject(images,channels,hist,ranges, scale, dst=None) -> dst
```

- images : input video list
- channels : channels number list to use backprojection calculate
- hist : input histogram (numpy. ndarray)
- ranges : list composisted to max value and min value from each dimension histogram
- scale : additionally multiple value to output backproject matrix
- dst : output backprojection video