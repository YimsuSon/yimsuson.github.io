---
title: Controll Brightness of Video
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

### Controll Brightness of Video

<br/>
<br/>

### 1. Point processing
- The operation sets the coordination pixel value of the output video from the translated coordination pixel value of the input video.


![image](/assets/images/computervision/1-Brightness.png)

- The pixel value of result video should be in specific range(ex- gray scale).

### 2. What is controll brightness?
- The operation makes video more light or dark.


![image](/assets/images/computervision/2-formula.png)

### 3. Addition computation to controll brightness of video

``` c
cv2.add(src1,src2, dst=None, mask=None, dtype=None) -> dst
```

- src1 : (input) first video or scala.
- src2 : (input) second video or scala.
- dst : (output) the result video of addition computaion.
- mask : Mask Video
- dtype : The type of output video ex) cv2.CV_8U etc
*** Note
    - The scalar is tuple that is composed of one real value or four real vale.
    



