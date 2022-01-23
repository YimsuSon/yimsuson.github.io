---
title: 3.ShellSort - C++ 
excerpt: Data structure


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
  - Data structure

tags:
  - Data structure
  - "2021"
  - "2021.08"



---


3.ShellSort - C++ 


<br/>


``` cpp

#include <iostream>

void shellSort(int a[], int size) {
    int i, j, temp;
    int gap = size / 2;
    
    while( gap > 0 ) {
        for( i=gap; i<size; i++ ) {
            temp = a[i];
            j = i;
            while( j>=gap && a[j-gap]>temp ) {
                a[j] = a[j-gap];
                j -= gap;
            }
            a[j] = temp;
        }
        gap /= 2;
    }
}
int main() {
    int arr[] = {9,1,22,4,0,-1,1,22,100,10};
    int size = sizeof(arr)/sizeof(int);
    
    shellSort(arr, size);
    for(int x: arr) std::cout << x << " ";
}


```

<br/>
<br/>




