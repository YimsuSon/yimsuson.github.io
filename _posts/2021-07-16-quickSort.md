---
title: 4.quickSort - Javascript 
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



4.quickSort - Javascript 


<br/>


``` javascript
const arr = [3,2,1,4]

function quickSort(items){
    return quickSortHelper(items,0,items.length-1)
}

function quickSortHelper(items,left,right) {
    var index;
    if( items.length > 1 ){
        index = partition(items,left,right);
        if(left < index -1){
            quickSortHelper(items,left,index-1);
        }
        if(left < right){
            quickSortHelper(items,index,right);
        }
    }
    return items;
}

function partition(array,left,right){
    var pivot = array[ Math.floor( (right+left)/2 ) ];
    while( left <= right ){
        while( pivot > array[left]){
            left++;
        }
        while( pivot < array[right]){
            right--;
        }
        if( left <= right ){
            var temp = array[left];
            array[left] = array[right];
            array[right] = temp;
            left++;
            right--;
        }
    }
    return left;
}


quickSort(arr)
console.log(arr)



```

<br/>
<br/>
