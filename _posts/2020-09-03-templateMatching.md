---
title: TemplateMatching
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


### Template Matching

<br/>
<br/>

### 1. Template Matching

<br/>

- The method finds the matching part with template image in input image.
- Template : Small image to find the object. Patch


<br/>

![image](/assets/images/computervision/20200903_1.png)

<br/>

- Template matching code

<br/>

``` c
cv2.matchTemplate(image, temp1, method, result=None, mask=None) -> result
```

<br/>

- image : Input image. 8bit or 32 bit
- templ : template image
- method : comparision method
- result : comparision result matirx

<br/>

- Template matching method




<br/>

![image](/assets/images/computervision/20200903_2.png)


![image](/assets/images/computervision/20200903_3.png)


<br/>


- Templat matching example




<br/>

![image](/assets/images/computervision/20200903_4.png)


![image](/assets/images/computervision/20200903_5.png)


<br/>


### 2, Number recognition of typeface

- Recognition 
    - Classifying a detected object into different categories
    - Selecting similar class in the several class




<br/>

![image](/assets/images/computervision/20200903_6.png)

<br/>


- Generating number template image 
    - Saving the number image written by 'Consolas' font to digit0.bmp ~ digit9.bmp
    - Nomalization to 100 x 150 size of each number image


<br/>

![image](/assets/images/computervision/20200903_8.png)

<br/>

- Number recognition process


<br/>

![image](/assets/images/computervision/20200903_9.png)

<br/>

- Number recognition example



<br/>

![image](/assets/images/computervision/20200903_10.png)

<br/>
