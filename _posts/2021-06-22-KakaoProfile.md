---
title: 2.Auto Layout - Kakao Profile
excerpt: iOS


#최상위 사진
header:
  #image: /assets/images/moon3.png
  teaser: /assets/images/moon3-th.png

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
  - iOS

tags:
  - iOS_Basic
  - "2021"
  - "2021.06"



---


### 0. Kakao Profile 



<br/>

![image](/assets/images/20210622_profile.png)

<br/>



#### iOS의 Layout 구성방식
- 1. Frame based layout 
- 2. Autoresizing
- 3. Auto Layout

<br/>

### 1. Frame based Layout

<br/>

![image](/assets/images/20210622_frame.png)

<br/>

<br/>

### 2. Auto resizing 

<br/>

![image](/assets/images/20210622_autoresize.png)

<br/>

<br/>

### 3. Auto Layout 

- Auto Layout attributes 

<br/>

![image](/assets/images/20210622_auto1.png)

<br/>


- Instrinsic content size 
    - 고유의 컨텐츠 사이즈 ( 슬라이더 버튼 텍스트 등이 가지고 있는 최소한의 사이즈) 



 
<br/>

![image](/assets/images/20210622_chcr.png)

<br/>


- Content Hugging : 우선순위가 높은것의 최대크기 제한
- Content Compression Resistance : 우선순위가 높은것의 최소크기 제한 



<br/>

![image](/assets/images/20210622_prior.png)

<br/>

- Priority 
    - 1 에서 1000 사이의 값을 가짐
    - 1000 : 필수조건 , 750 : hight , 250 : low 





