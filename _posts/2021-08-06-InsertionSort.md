---
title: 2.InsertionSort - C++ 
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


2.InsertionSort - C++ 


<br/>


``` cpp



#include <iostream>

void printArr (int arr[],int size){
    int i;
    for (i=0; i<size; i++){
        std::cout <<  arr[i] << ", ";
    }
    std::cout << "\n";
}

void insertionSort(int arr[], int size) {
    int i, j,key;
    for (i = 1; i < size; i++) {
        key = arr[i];
        j = i - 1;
        while (j >= 0&&arr[j]>key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}



int main(int argc, const char * argv[]) {
    int size = 10;
    int arr[10] = { 3,2,3,1,5,6,7,8,9,10 };
    
    printArr(arr, size);
    insertionSort(arr, size);
    printArr(arr, size);
   
    
}



```

<br/>
<br/>