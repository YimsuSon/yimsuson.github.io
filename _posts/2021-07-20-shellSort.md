---
title: 6.shellSort - Javascript 
excerpt: Algorithm


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
  - Algorithm

tags:
  - Algorithm
  - "2021"
  - "2021.07"



---


6.shellSort - Javascript 


<br/>


``` javascript

const arr = [5,1,3,2,1,4]



function shellSort(arr) {
    let gap = Math.floor(arr.length / 2);
  
    while (gap > 0) {
      for (let i = 0; i < arr.length - gap; i++) {
        let currentIndex = i;
        let gapShiftedIndex = i + gap;
  
        while (currentIndex >= 0) {
          if (arr[gapShiftedIndex] <= arr[currentIndex]) {
            const temp = arr[currentIndex];
            arr[currentIndex] = arr[gapShiftedIndex];
            arr[gapShiftedIndex] = temp;
          }
  
          gapShiftedIndex = currentIndex;
          currentIndex -= gap;
        }
      }
      gap = Math.floor(gap / 2);
    }
    return arr;
  }

  shellSort(arr);
  console.log(arr)



```

<br/>
<br/>
