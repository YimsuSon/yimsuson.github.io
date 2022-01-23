---
title: Arithmetic operation and logic operation of Video
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

### Arithmetic operation and logic operation of Video

<br/>
<br/>

### 1. Addition operation

``` c
dst(x,y) = saturate(src1(x,y)+src2(x,y))
```
- It Add the pixel value that exists on same position between two videos and Set the pixel value of video.
- If the value is more than 255, set the pixel value to 255.

``` c
cv2.add(src1, src2, dst=None, mask=None, dtype=None) -> dst
```

- src1 : (input) first video or schalar
- src2 : (input) second video or schalar
- dst : (output) result video of addition operation
- mask : mask video
- dtype : type of output video 


<br/>

### 2. Weighted sum

``` c
dst(x,y) = saturate(a * src1(x,y) + b * src2(x,y))
```
- Calculating weighted sum about pixel value which exist same position of two video and Setting the pixel value of result video.

- Genarlly, spacifiy a + b = 1  (Maintaing normal birghtness of two input video)

<br/>

### 3. Average operation

``` c
dst(x,y) = 1/2(src1(x,y) + src2(x,y))
```

- Setting the weight with a = b = 0.5

<br/>

Code of weighted sum 
``` c
cv2.addWeighted(src1,alpha,src2,beta,gamma,dst=None,dtype=None) -> dst
```

- src1 : Frist video
- alpha : Weight of first video
- src2 : Second video ( same type & same size with src1)
- beta : Weight of second video
- gamma : Additional added value to result value 
- dst : result vieo of weighted sum
- dtype : type of output video(dst)

<br/>

### 4. Subtraction operation
``` c
dst(x,y) = |src1(x,y) - src2(x,y)
```
- It doesn't be effected from order of input video

<br/>
Code of subtracion operation
``` c
cv2.subtract(src1, src2, dst = None, mask = None, dtype = None ) -> dst
```

- src1 : first video
- src2 : second video
- dst : result video of subtraction operation
- mask : mask video
- dtype : type of output video

### 5. Bit unit operation ( AND, OR. XOR, NOT)

``` c
cv2.bitwise_and(src1, src2, dst = None, mask = None) -> dst
cv2.bitwise_or(src1, src2, dst = None, mask = None) -> dst
cv2.bitwise_xor(src1, src2, dst = None, mask = None) -> dst
cv2.bitwise_not(src1, dst = None, mask = None) -> dst

```

- src1 : first video
- src2 : second video
- dst : result video 
- mask : mask video

