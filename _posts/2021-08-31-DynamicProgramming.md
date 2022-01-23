---
title: 12.DynamicProgramming - C++ 
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


12.DynamicProgramming - C++ 


<br/>


``` c++


#include <iostream>

using namespace std;
int f[100]={0};
 
int fib(int n){
    if(n==0) return 0;
    else if(n==1) return 1;
    else if(f[n]) return f[n]; // 메모리제이션
    else{
        f[n]=fib(n-1)+fib(n-2);
        return f[n];
    }
}
 
int main(){
    int N;
    cin>>N;
    cout<<fib(N)<<'\n';
    return 0;
}
 
// 5 입력시 55 결과값



```

<br/>
<br/>


