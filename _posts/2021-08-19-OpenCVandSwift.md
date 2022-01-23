---
title: 3.The method about how to use OpenCV in Xcode
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
  - iOS
  - "2021"
  - "2021.08"



---








1. opencv2.framwork 압축파일을 opencv.org 에서 다운받는다
2. 프로젝트를 swift로 만든다 
3. 압축해제한 폴더를 프로젝트에 복사한다
4. Cocoa Touch Class 에서 NSObject로 OpenCVWrapper를 만든다 
5. .m 파일을 엔터를 눌러 .mm으로 변환해주면 c++ 형식을 읽는다
6. PrefixHeader.pch파일을 만들고 아래의 코드를 추가한다

<br/>
<br/>



``` swift

#ifdef __cplusplus
#include <opencv2/opencv.hpp>
#endif

```

<br/>
<br/>


'opencv2/opencv.hpp' file not found 
에러를 만나고 

여기서부터 경로설정을해준다 

7. Target >> Build Settings 에서 Apple Clang - Language >> Prefix Header 에 $(SRCROOT)/PrefixHeader.pch 를  추가한다
8. arget >> Build Settings 에서 Search Paths >> Framework Search Paths 에 압축해제한 폴더의 *** 상위폴더*** 까지 경로를 입력해준다 ( 제대로 입력해도 에러가 발생하는 버그를 발견, 추가경로를 입력하고 컴파일 했다가 다시 제대로 경로를 입력하니 해결됨 ) 


<br/>
<br/>






이미지를 회색으로 변환해주는 코드들

<br/>
<br/>


OpenCVWrapper.h 

<br/>


``` cpp

#import <Foundation/Foundation.h>
#import <UIKit/UIKit.h>

NS_ASSUME_NONNULL_BEGIN

@interface OpenCVWrapper : NSObject

+(UIImage *) makeGrayImage:(UIImage *) image;


@end

NS_ASSUME_NONNULL_END


```

<br/>
<br/>




OpenCVWrapper.mm

<br/>



``` cpp



#import "OpenCVWrapper.h"

#import <opencv2/opencv.hpp>
#import <opencv2/imgcodecs/ios.h>


@implementation OpenCVWrapper

+(UIImage *) makeGrayImage:(UIImage *)image{
    cv::Mat imageMat;
    UIImageToMat(image, imageMat);
    
    if(imageMat.channels() == 1)
        return image;
    
    cv::Mat grayMat;
    cv::cvtColor(imageMat, grayMat, cv::COLOR_RGB2GRAY);
    return MatToUIImage(grayMat);
    
    
}



@end


```

<br/>
<br/>



프로젝트명-Bridging-Header.h


<br/>

``` cpp


#include "OpenCVWrapper.h"


```




<br/>
<br/>


