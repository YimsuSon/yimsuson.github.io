---
title: 2.Selection Sort - Javascript 
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



<br/>


``` javascript

const arr2 = [1,3,3,4,1,2];




var selectionSort = arr => {
    const len = arr.length;
    const swap = (arr,idx1,idx2)=>
    ([arr[idx1],arr[idx2]] = [arr[idx2],arr[idx1]]);

    for (let i = 0 ; i < len; i++){
        let idxOfMin = i;
        for(let j = i+1; j<len;j++){
            if(arr[j]<arr[idxOfMin]) idxOfMin=j;
        }
        if(idxOfMin!==i) swap(arr,idxOfMin,i);
    }
    return arr;
}

selectionSort(arr2)
console.log(arr2)



```

<br/>
<br/>
