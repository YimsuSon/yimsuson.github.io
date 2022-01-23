---
title: OpenCV Main Function Description
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
  - title: "Category"
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

### Open CV Main Function Description


<br/>
<br/>

### 1.OpenCV Api searching 

<Link>(https://docs.opencv.org/master/)

<br/>

### 2.Load Video file

``` c
cv2.imread(filename, flags=None) -> retval
```

- filename : the name loading video (literal)
- flags : the option flag loading video


|function|description|
|---|---|
|cv2.IMREAD_COLOR|Read as BGR color video <br/> shape = (rows,cols,3) |
|cv2.IMREAD_GRAYSCALE|Read as Gray scale <br/> shape = (rows,cols) |
|cv2.IMREAD_UNCHANGED|Read as original video property <br/> (e.g) transparent file shape = (rows,cols,4) |


- retval : the video data loaded (numpy.ndarray)

### 3.Save Video file

``` c
cv2.imwrite(filename, img, params=None) -> retval
```
- filename : the name to save video (literal)
- img : image data to be saved (numpy.ndarray)
- params : select option to save file ( integer of attribute & value ) <br/> e.g) [cv.IMWRITE_JPEG_QUALITY,90] : specify the compression ratio as 90%

-retval : If save is successful, it is True. If save is  fail, it is False.  



### 4.Open the new window

``` c
cv2.namedWindow(winname, flags=None) -> None
```
- winname : the name of window (literal)
- flag : select the flag of window attibute

|---|---|
|cv2.WINDOW_NORMAL|specify the video size to fit the window size|
|cv2.WINDOW_AUTOSIZE|translate the window size to fit the video size |


### 5.CLose the widdow

``` c
cv2.destroyWindow(winname) -> None
cv2.destroyAllWindows() -> None
```
- winname : the name of window you want to close

** cv2.destroyWindow() just close a window, <br/> cv2.destroyAllWindows() close all window.


### 6.Move the window 

``` c
cv2.moveWindow(winname,x,y) -> None
```

- winname : the name of window
- x,y : the position coordinate to move


### 7.Resize the window

``` c
cv2.resizeWindow(winname,width,height) -> None
```

- winname : the name of window
- width : the horizontal size of window to change
- height : the vertical size of window to change

### 8.Show the window

``` c
cv2.imshow(winname,mat) -> None
```
- winname : the name of window
- mat : the data to show video data (numpy,ndarray)
<br/>
** Note <br/>
    - If the case is unit16, int32,divide the matrix element value by 255 and print them out.
    - If the case is float32, float64,multiply the matrix element value by 255 and print them out.
    - Actually, the image appears on screen only when cv2.waitKey() function is called. 

### 9.Wait Keyboard input
``` c
cv2.waitKey(delay=None) -> retval
```

- delay : the waiting time (e.g) delay <= 0, wait forever.  delfault value is 0
- retval : pressed key value. (if not, the value is -1) 
<br/>
** Note <br/>
    - Main special key code :  27(ESC)  , 13(ENTER), 9(TAB)
    
    - Use ord() function to check the input of specific key
``` c
    while True:
        if cv.waitKey() == ord('q'):
            break
```
