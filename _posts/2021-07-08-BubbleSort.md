---
title: 1. Bubble Sort - Javascript 
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


1. Bubble Sort - Javascript 


<br/>


``` javascript

const arr2 = [1,3,3,4,1,2];



var bubbleSort = function(array) {
  var length = array.length;
  var i, j;

  const swap = (arr,idx1,idx2) => 
       ( [ arr[idx1], arr[idx2] ] = [ arr[idx2],arr[idx1] ]);

  for (i = 0; i < length - 1; i++) { // 순차적으로 비교하기 위한 반복문
    for (j = 0; j < (length - 1) - i; j++) { // 끝까지 돌았을 때 다시 처음부터 비교하기 위한 반복문
      if (array[j] > array[j + 1]) swap(array,j,j+1)
      //  { 
      //   // 두 수를 비교하여 앞 수가 뒷 수보다 크면
      //   temp = array[j]; // 두 수를 서로 바꿔준다
      //   array[j] = array[j + 1];
      //   array[j + 1] = temp;
      // }
    }
  }
  return array;
};

////   bubbleSort([5,2,8]);
//  bubbleSort(arr2);
//  console.log(arr2)



```

<br/>
<br/>
