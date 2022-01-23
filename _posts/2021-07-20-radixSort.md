---
title: 6.shellSort - Javascript 
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

7.radixSort - Javascript 


<br/>


``` javascript

const arr = [5,1,3,2,1,4]



var counter = [[]];
var radixLSort = function(array, d) {
  var mod = 10;
  for (var i = 0; i < d; i++, mod *= 10) { // mod는 현재 정렬 중인 자리수를 나타내는 것으로 10부터 해서 100, 1000, ...으로 커집니다.
    for (var j = 0; j < array.length; j++) {
      var bucket = parseInt(array[j] % mod); // 같은 그룹으로 묶일 나머지를 나타내는 부분입니다.
      if (counter[bucket] == null ) {
        counter[bucket] = [];
      }
      counter[bucket].push(array[j]); // 나머지 별로 묶어줍니다.
      console.log('bucket', bucket, counter[bucket]);
    }
    console.log(counter.slice(0));
    var pos = 0;
    for (var j = 0; j < counter.length; j++) { // counter에 저장한 묶음들(나머지 순서로 정렬됨)을 실제 배열에 반영해줍니다.
      var value = null ;
      if (counter[j] != null ) {
        while ((value = counter[j].shift()) != null ) {
          array[pos++] = value;
        }
      }
    }
    console.log(array);
  }
  return array;
}

radixLSort(arr,3)


// 출처 : https://www.zerocho.com/category/Algorithm/post/58007c338475ed00152d6c4c





```

<br/>
<br/>
