---
title: 2.프로그래머스 lv3 - 하노이의 탑 스위프트
excerpt: Algorithm


#최상위 사진
header:
  image: /assets/images/foo-bar-identity.jpg
  teaser: /assets/images/foo-bar-identity-th.jpg

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
  - "2021.01"



---

### 1.프로그래머스 lv3 - 하노이의 탑

<br/>
<br/>

문제 : 하노이의 탑

<br/>
<br/>

diagrams.net 에서 처음 그려본 기념으로 올려보는 포스트.
<br/>

1 번 막대, 2번 막대, 3번 막대를 그린뒤
<br/>
A,B,C 3개의 원반을 그린다.
<br/>
코드를 실행한 후 log 의 설명을 따라가본 뒤
<br/>
순서도를 보면 하노이의 탑을 좀 더 쉽게 이해할수있다 
<br/>

![image](/assets/images/computervision/tower.png)

<br/>



```swift

var n = 3

func solution(_ n:Int) -> [[Int]] {
    var hanoiArray: [[Int]] = []
    
        func hanoi(_ n: Int, _ from: Int, _ by: Int, _ to: Int) -> [[Int]] {
            
            if n == 1 {
                print("\(from)번 막대에 있는 첫번째 원반을 \(to)번 막대로 이동 ( 이 원판은 다음 이동될때 \(by)번 막대에 쌓인것 마킹)-1 실제이동 ")
                hanoiArray.append([from,to]) // 원반이동
                
            } else {
                
                hanoi(n-1, from,to,by)
                print("\(from)번 막대에 있는 \(n-1) 번 원반을 \(to)번 막대로 이동 ( 이 원판은 다음 이동될때 \(by)번 막대에 쌓인것 마킹)-2 실제이동 ")
                hanoiArray.append([from,to]) // 원반이동
            
                hanoi(n-1, by,from,to)
                print("return \n")
            }
        return hanoiArray
        }

    return hanoi(n,1,2,3)
}

solution(n)



```