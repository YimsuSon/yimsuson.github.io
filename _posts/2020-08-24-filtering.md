---
title: 2.Cartoon filter - Image filtering
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

### Image filtering

<br/>
<br/>

### 1. What is image filtering
- Image filtering
    - The task filter the unecessary information and pass the necessary information to image

<br/>

- Frequency domain filtering

![image](/assets/images/computervision/2-frequencydomainfilter.png)

<br/>

- Spatial domain filtering
    - The method directly use the fixel value of video
    - Generally Using the mask operation (mask = kernel = window = template)


- The form and value of mask makes the task to define 
    - Making smoothly image
    - Making sharply image
    - Edge detection
    - Noise reduction

<br/>

- Example spatial domain filtering

![image](/assets/images/computervision/4-20200824.png)

<br/>

- Basic 2D filtering

``` c
cv2.filter2D(src, ddepth, kernel, dst=None, anchor=None, delta=None, borderType=None) -> dst
```

- src : Input video
- ddepth : Data type of output image ex) cv2.CV_8U, cv2.CV_32F
- kernel : Filter mask metrix
- anchor : Position of fix point
- delta : Additional added value
- borderType : Border pixel Expension method
- dst : Output image

<br/>
<br/>


### 2. Blurring

- Mean filter 
    - Specific coordination value of image set the arithmetical average of near fixel values.
    - The scale value change of each pixel decreases and the sharp edge is going to be smooth. so The effect of noise disappears.


![image](/assets/images/computervision/5-20200824.png)

<br/>

- Mean filtering function

``` c
cv2.blur(src, ksize, dst=None, anchor=None, borderType=None) -> dst
```

- src : Input video
- ksize : Mean filter size ( tuple type - (width, height) )
- dst : Output video

<br/>

- Mean filter example

![image](/assets/images/computervision/6-20200824.png)

<br/>
<br/>

### 3. Gaussian filter

- Disadvantage of the bluring using Mean filter
    - From the position of target, Both near pixel and distant pixel use the same weight for calculating the average.
    - The distant pixel could be affected 

<br/>

- 1-Dimension Gaussian function  

![image](/assets/images/computervision/6-20200825.png)

<br/>

- 2-Dimension Gaussian function 

![image](/assets/images/computervision/7-20200825.png)

<br/>

- Gaussian filtering function

``` c
cv2.GaussianBlur(src, ksize, sigmaX, dst=None, sigmaY=None, borderType=None) -> dst
```

- src : Input image
- dst : Output image
- ksize : Gaussian kernel size
- sigmaX : x-directional sigma
- sigmaY : y-directional sigma
- borderType : Edge pixel expension method

<br/>

- Gaussian filter mask example

![image](/assets/images/computervision/8-20200825.png)

<br/>
<br/>


### 4. Sharpening

- Unsharp mask filtering
    - Unsharp image, Being the sharped image use to make sharp image.

<br/>

- Realize unsharp mask filter 

![image](/assets/images/computervision/9-20200825.png)

<br/>


![image](/assets/images/computervision/11-20200825.png)



<br/>
<br/>

### 5. Reduction noise - median filter

- Noise of image
    - The Unexpected form of the signal be added at pixel value of the image.


<br/>


![image](/assets/images/computervision/12-20200825.png)

<br/>

- Sort of noise
    - Gaussian noise
    - Salt & Pepper


![image](/assets/images/computervision/13-20200825.png)

<br/>

- Median filter
    - It replace pixel values  by sorting to median value, where are near center position.
    - It is effect to reduce the Salt & Pepper noise

![image](/assets/images/computervision/14-20200825.png)

<br/>

- Median filter function


``` c
cv2.medianBlur(src, ksize, dst=None) -> dst
```


- src : Input image 
- ksize : Kernel size
- dst : Output image

<br/>

- Median filtering example


![image](/assets/images/computervision/15-20200825.png)

<br/>
<br/>


### 6. Bilateral filter

<br/>

- It's one of edge-preserving noise removal filter
- It have weakness that Median filter and gaussian filter make to average out the pixel value nearby edge.


<br/>

![image](/assets/images/computervision/16-20200826.png)

<br/>

- Normal gaussian filtering : Blurring in the whole image.

<br/>


![image](/assets/images/computervision/17-20200826.png)

<br/>


- Bilateral filter : Burring in the out of edge

<br/>

![image](/assets/images/computervision/18-20200826.png)

- Bilateral filtering function

``` c
cv2.bilateralFilter(src, d, sigmaColor, sigmaSpace, dst=None, borderType=None) -> dst
```

- src : Input image
- d : Distant(Diameter) of pixel
- sigmaColor : Standard deviation in color space
- sigmaSpace : Standard deviation in coordination space
- dst : Output image
- borderType : Edge pixel processing method





