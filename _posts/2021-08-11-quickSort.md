---
title: 5.QuickSort - C++  
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




5.QuickSort - C++ 


<br/>


``` cpp


#include <iostream>

void swap(int *a, int *b) {
    int t = *a;
    *a = *b;
    *b = t;
}
 
void quickSort(int left, int right, int *arr) {
    int pivot = arr[left];
    int less = left;
    int more = right+1;
     
    if (left < right) {
        do {
            do
                less++;
            while (less <= right && arr[less] < pivot);
 
            do
                more--;
            while (more >= left && arr[more] > pivot);
 
            if (less < more)
                swap(&arr[less], &arr[more]);
 
        } while (less < more);
        swap(&arr[left], &arr[more]);
         
        quickSort(left, more - 1,arr);
        quickSort(more + 1, right, arr);
    }
 
}

int main(int argc, const char * argv[]) {
    int arr[] = { 3,2,3,1,5,6,7,8,9,10 };
    int size = sizeof(arr)/sizeof(int);
    
    quickSort(0, size, arr);
    
    for(int x:arr) std::cout << x << " ";
    
}






```

<br/>
<br/>
