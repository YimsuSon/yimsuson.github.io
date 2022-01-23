---
title: Image Structure
excerpt: 이미지 구조 


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
  - title: "Category"
    nav: sidebar-sample

# 해당 글 목차
toc: true
toc_sticky: true

toc_label: "Ai"
toc_icon: "cog"


## 테그설정
categories:
  - ComputerVision
tags: "ComputerVision"
---






### 1.What is the image?



- The pixel is arraied on 2-dimension matrix which is composed of cross grid 



- Pixel = Basic unit , picture element

<br/>

<br/>

### 2. The expression method of image

<br/>

- grayscale image can show 0 ~ 255 

  

- True color image can show 0 ~ 255^3

  

- Numpy.unit8 could express 1Byte of pixel value ex) ( 255)

- Numpy.ndarray could express 3Byte of pixel value  ex) ( 255.255.255) or tuple



- w x h coordinations is generally used in the image. 



### 3. The size analysis of image data

<br/>

-  Gray scale image : ( w ) x ( h )  Bytes
-  True color image : ( w ) x ( h ) Bytes

<br/>

<br/>



### 4. The feature of file format

<br/>

- BMP : It directly save a file without compression

  ​		 : The file structure is simple, so it can program the file I/O without extra library help

- JPG : It generally saves color images such as photos

  ​		: Lossly compression

  ​	    : It is great compression rate and greatly reduces file size

- GIF : It saves images with 256 colors or less  

  ​	   : Lossless compression

- PNG : Portable Network Graphics

  ​         : Lossless compression