---
title: Process Video and Camera
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

### Process Video and Camera

<br/>
<br/>

### 1. cv.2VideoCapture Class

- cv.VideoCapture class could do the task that recieves the frame from cammer or video in OpenCV.

<br/>
<br/>


### 2. Open Cammera

``` c

cv2.VideoCapture(index,apiPreference=None) -> retval

```

- index : camera_id + domain_offset_id (If you open the system basic cammer using the basic method,pass "0" to index. )
- apiPrefence : Specified as prefered cammera processing method.
- retval : cv2.VideoCapture object


``` c
cv2.VideoCapture.open(index,apiPreference=None) -> retval

```
- retval : To success is True, To fail is False


<br/>
<br/>


### 3. open Video, Stop video sequence, Video stream

``` c
cv2.VideoCapture(filename, apiPreference = None) -> retval

```

- filename : Video file name, stop video sequence , video stream URL etc. ex) 'video.avi', 'img_%02d.jpg','protocol://host:prot/scrpt?params|auth'

- apiPreference : Specify as prefered cammera processing method
- retval : cv2.VideoCapture object

``` c
cv2.VideoCapture.open(filename,apiPreference=None) -> retval

```
- retval : To success is True, To fail is False

<br/>
<br/>

### 4. Check the Video capture

``` c

cv2.VideoCaptrue.isOpened() ->> retval
```
- retval : To success is True, To fail is False


<br/>
<br/>

### 5. Recieve the frame

``` c
cv2.VideoCapture.read(image=None) -> retval, image

```
- retval : To success is True, To fail is False
- image : Current frame ( numpy.ndarray)

<br/>
<br/>

### 6. To refer Cammera, Video device property value

``` c
cv2.VideoCapture.get(propID) -> retval
```

- propID : property constant

|---|---|
|CAP_PROP_FRAME_WIDTH|frame horizontal size|
|CAP_PROP_FRAME_HEIGHT|frame vertical size|
|CAP_PROP_FPS|the number of frames per second|
|---|---|

<br/>
<br/>

### 7. cv2.VideoWriter class

- The frames are could saved as video file using cv.VideoWriter class in OpenCV.

- Fourcc(four chracter code) : integer value defining codec of video file, method of compress, color, pixel

|---|---|
|cv2.VideoWriter_fourcc(*'DIVX')|DIVC MPEG-4 codec|
|cv2.VideoWriter_fourcc(*'XIVD')|XCID MPEG-4 codec|
|cv2.VideoWriter_fourcc(*'FMP$')|DDMPEG MPEG-4 codec|
|cv2.VideoWriter_fourcc(*'X264')|G.264/AVC codec|
|cv2.VideoWriter_fourcc(*'MJPG')|Motion-JPEG codec|
|---|---|

<br/>
<br/>

### 8. open the video file for storage

``` c
cv2.VideoWriter(filename, fourcc, fps, frameSize, isColor=None) -> retval

```
- filename : video file name
- fourcc : fourcc ex) cv2.VideoWriter_fourcc(*'DIVX'))
- fps : the number of frame per second ex) 30
- frame size : (width,height)
- isColor : Color video is True 

``` c
cv2.VideoWriter.open(filename, fourcc, fps, frameSie, isColor=None) -> retval
```

<br/>
<br/>

### 9. Check the video file 

``` c
cv2.VideoWriter.isOpend() -> retval
```

- save the frame
``` c
cv2.VideoWriter.write(image) -> None
```

 - image : To save frame (numpy.ndarray)


### 10. save the video for WebCam input 

``` c
 
cap = cv2.VideoCapture(0)
w = round(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
h = round(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

fourcc = cv2.VideoWriter_fourcc(*'DIVX') # *'DIVX' == 'D','I','V','X' 

out = cv2.VideoWriter('output.avi', fourcc, 30, (w, h))

while True:
    ret, frame = cap.read()
    
    inversed = ~frame 
    out.write(inversed)
    
    cv2.imshow('frame', frame) 
    cv2.imshow('inversed', inversed) 
    
    if cv2.waitKey(10) == 27:
        break

```
