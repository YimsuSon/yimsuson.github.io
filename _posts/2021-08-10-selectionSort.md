---
title: 4.SelectionSort - C++ 
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


4.SelectionSort - C++ 


<br/>


``` cpp


#include <iostream>


//void printArr (int arr[],int size){
//    int i;
//    for (i=0; i<size; i++){
//        std::cout <<  arr[i] << ", ";
//    }
//    std::cout << "\n";
//}

void swap(int *a, int *b){
    int tmp = *a;
    *a = *b;
    *b = tmp;
}

void selectionSort(int arr[], int size){
    int minIndex;
    int i, j;
    for (i = 0; i < size -1;i++){
        minIndex = i;
        for (j = i + 1; j<size; j++){
            if (arr[j] < arr[minIndex]){
                minIndex = j;
            }
        }
        swap(&arr[i], &arr[minIndex]);
    }
}


int main(int argc, const char * argv[]) {
    int arr[] = { 3,2,3,1,5,6,7,8,9,10 };
    int size = sizeof(arr)/sizeof(int);
    
//    printArr(arr, size);
//    selectionSort(arr, size);
//    printArr(arr, size);
    
    selectionSort(arr, size);
    for(int x:arr) std::cout << x << " ";
    
}




```

<br/>
<br/>
