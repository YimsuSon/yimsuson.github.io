---
title: 5.mergeSort - Javascript  
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


5.mergeSort - Javascript 


<br/>


``` javascript

const arr = [5,1,3,2,1,4]


function merge(left, right) {
    let result = [];
    while (left.length && right.length) { // ___.length가 true일 때 === 배열 안에 값이 남아있을 때
        if (left[0] <= right[0]) { 
        result.push(left.shift()); // shift() 메서드는 배열에서 첫 번째 요소를 제거하고, 제거된 요소를 반환합니다.
        } else {
        result.push(right.shift()); 
        }
    }
    while (left.length) result.push(left.shift()); 
    while (right.length) result.push(right.shift());
    return result;
};


const mergeSort = function(array) {
    if (array.length < 2) return array; 
    let pivot = Math.floor(array.length / 2); //쪼개기
    let left = array.slice(0, pivot); 
    let right = array.slice(pivot, array.length); 
    return merge(mergeSort(left), mergeSort(right)); // 재귀
  }



console.log(mergeSort(arr));



```

<br/>
<br/>

