---
title: 1.BinarySearch - C++ 
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


1.BinarySearch - C++ 


<br/>


``` cpp


#include <iostream>

using namespace std;

int main()
{
   // 1~500까지의 배열 형성
   int arr[501];
   for(int i=1;i<501;i++)
      arr[i]=i;

   int target = 62; // 타겟 값
   int left = 0, right = sizeof(arr)/sizeof(int) - 1 ; // left, right 초기화
    cout << sizeof(int) ;
    
    
   // 이분 탐색 수행
   while(left<=right)
   {
      int mid = (left+right)/2 ; // mid 갱신
       //cout << mid <<'\n';
       

      if(mid==target)
      {
         cout<<"Searching Complete! = " << target <<'\n';
         break;
      }
      else if(mid>target)
      {
         right = mid-1;
      }
      else
      {
         left = mid+1;
      }
   }
   return 0;
}




```

<br/>
<br/>
