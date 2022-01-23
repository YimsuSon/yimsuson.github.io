---
title: 1.Scanner - Geometric transformation
excerpt: ComputerVision


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

### Image filtering

<br/>
<br/>

### 1. Transformation of image and shear transition
- Meaning of geometric transformation
    - The task to change the whole image by altering arrangement of pixel composing image.
    - ex) Image registration, removal of geometric distortion, etc.
<br/>


![image](/assets/images/computervision/1-20200827.png)
<br/>

- Translation transformation
  - The transformation moving the image as specific size to horizontal or vertical direction.
  - It have to set the translation displacement of x-axis and y-axis 

<br/>

![image](/assets/images/computervision/2-20200827.png)

<br/>

- Affine transformation function

``` c

cv2.warpAffine(src, M, dsize, dst=None, flags=None, borderMode=None, borderValue=None) -> dst

```

- src : Input image
- M : 2 x 3 affine metrix
- dsize : Result image size
- dst : Output image
- flags : Interpolation type
- borderMode : Edge pixel expension method
- borderValue : default value is 0

<br/>

- Example of translation transformation of the image

![image](/assets/images/computervision/3-20200827.png)

<br/>


- Shear transformation 
  - It have to set each x-axis and y-axis.

<br/>
<br/>


### 2. Shrinkage and enlargement of image
<br/>


- Scale transformation
  - The transformation that size of image make larger or smaller than original image.
  - Specifying the scale factor of x-axis and y-axis

<br/>

![image](/assets/images/computervision/20200831_1.png)

<br/>

- Scale transformation code

```
cv2.resize(src, dsize, dst=None, fx=None, fy=None, interpolation=None) -> dst
```
- src : Input image
- dsize : Output image size
- dst : Out image
- fx,fy : scale factor of x,y direction
- interpolation : decide interpolation

<br/>

- Scale transformation example


<br/>

![image](/assets/images/computervision/20200831_2.png)

<br/>

- Scale transformaion precaution
  - When scale transformation be applied to image, Detail of image disappear
   - After Filtering smoothly input image, It apply to step by step shirinkage.
   - cv2.INTER_AREA flag is used in cv2.resize() function of OpenCV




<br/>

![image](/assets/images/computervision/20200831_3.png)

<br/>
<br/>

### 3. Image pyramid

<Br/>

- Image pyramid
  - Image sets of various resolution for one of image
  - Generally, It's consist of shrinkage size using Gaussian blurring & Down sampleing

<br/>


![image](/assets/images/computervision/20200901_1.png)

<br/>

- Image pyramid downsampling code

<br/>

``` c
cv2.pyrDown(src, dst=None, dstsize=None, borderType=None) -> dst
```

- src : Input image
- dst : Output image
- dstsize : Output image size
- borderType : Edge pixel expansion method
*** note 
  - Firstly, It's applied to Gaussian filter of 5x5 size. Then, Small size of image is made from delete even number of column and row.

<br/>

- Image pyramid upsmapling code

``` c
cv.pyrUp(src, dst=None, dstsize=None, borderType=None) -> dst
```

- src : Input image
- dst : Output image
- dstsize : Output image size
- borderType : Edge pixel expansion method

<br/>

- Image pyramid example 


<br/>


![image](/assets/images/computervision/20200901_2.png)

<br/>
<Br/>

### 4. Rotaion of image

<br/>

- Rotation transformation
  - Transformating image to rotate by specific angle


<br/>


![image](/assets/images/computervision/20200901_3.png)

<br/>

- Rotation transformation code

<br/>

``` c
cv2.getRotationMatrix2D(center, angle, scale) -> retval
```
<br/>
- center : Rotational center coordination
- angle : Rotaion degree
- scale : Additional magnification ratio
- retval : 2 X 3 Affine transformation matrix


<br/>


![image](/assets/images/computervision/20200901_4.png)

<br/>
<br/>

### 5. Affine Tansform and Perspective Transform

- Diffrent point between affine transform and perspectiv transform

<br/>

![image](/assets/images/computervision/20200901_5.png)

<br/>


![image](/assets/images/computervision/20200901_6.png)

<br/>

- To get affine transform matrix

<br/>

``` c
cv2.getAffineTransfrom(src, dst) -> retval
```
<br>

- src : Three point of original coordinate
- dst : Three point of result coordinate
- retval : 2 x 3 perspective transform matrix

<br/>

``` c
cv2.getPerspectiveTransfrom(src, dst) -> retval
```
<br>

- src : Four point of original coordinate
- dst : Four point of result coordinate
- retval : 3 x 3 perspective transform matrix

<br/>

- Perspective transform example

<br/>


![image](/assets/images/computervision/20200901_7.png)


<br/>
<br/>

### 6. Remapping

<br/>

- Remapping 
  - Normal process specific position pixel of image rearranes to other position

<br/>

![image](/assets/images/computervision/20200901_8.png)

<br/>

![image](/assets/images/computervision/20200901_9.png)

<br/>

- Remapping could express various trasformation with affine transform, perspective transform 

<br>

- Remapping code

<br>

``` c
cv2.remap(src, map1, map2, interpolation, dst=None, borderMode=None, borderValue=None) -> dst
```
<br/>

- src : Input image
- map1 : x-coordination of input image
- map2 : y-coordination of output image
- interpolation : Interpolation
- dst : Output image
- borderMode : Edge pixel expansion method
- borderValue : Constant value

<br/>

- Remapping example using trigonometic function


<br/>

![image](/assets/images/computervision/20200901_10.png)

<br/>