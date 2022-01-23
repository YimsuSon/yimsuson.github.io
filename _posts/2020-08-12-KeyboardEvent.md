---
title: Handle the keyboard Task
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

### Handle the keyboard Task

<br/>
<br/>

### 1. Waiting fuction of keyboard input

``` c
cv2.waitKey(delay=None) -> retval
```

- delay : Waiting time ex) delay <= 0 is infinite delay. defautl value is 0.
- retval : Putted key (ASCII code). ex) if not key is putted,it's -1.

* Note
    - cv2.waitKey() function opearates when OpenCV window is opened.
    - If you want to check the specific key press, you use the ord() function.
    ``` c
     while True:
        if cv2.waitKey() == ord('q'):
        break
    ```
    *** Main special Key code : 27 (ESC), 13 (ENTER), 9 (TAB)


<br/>
<br/>


### 2. Handle the mouse event

- the function that calls back the mouse event.

``` c
cv2.setMouseCallback(windowName, onMouse, param=None) -> None
```

- windowName : Window name that mouse event handle.
- onMouse : The callback function for handle mouse event.
    - It should follow like that frame
    ``` c
    onMouse(event,x,y,flags,param) -> None
    ```
- param : data that pass to callback funtion


### 3. THe frame that handle mouse event function(callback function)

``` c
onMouse(event,x,y,flags,param) -> None
```

- event : The sort of mouse event. ex) constant starting with cv.EVENT_FLAG

- x : x coordination
- y : y coordination
- flags : The situation when break mouse event ex) constant starting with cv.EVENT_FLAG
- param : The data that is setted from cv2.setMouseCallback() function.



### 4. The method How to check the operation time

- Computer Vision generally handles high capacity data. So We should manage the final result through series of processes checking the operation time.

- TickMeter class could check the operation time in OpenCV

``` c
cv2.TickMeter() -> tm
```

- tm : cv2.TickMeter object
- tm.start() : start time check
- tm.stop() : stop time check
- tm.reset() : initialize time check
- tm.getTimeSec() : return the time check per second
- tm.getTimeMilli() : return the time check per milli second
- tm.getTimeMicro() : return the time check per micro second