---
title: "Cuda 와 cuDNN 설치"
excerpt: "Cuda 와 cuDNN 설치, tensorflowgpu와 pytorch호환버전"


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

toc_label: "Cuda,Tensorflow-gpu,Pytorch "
toc_icon: "cog"


## 테그설정
tags: "blog"
categories:
  - Ai
---

# Cuda 10.0, cuDNN, tensorflow-gpu, python 설치 및 호환버전

---

---

Cuda 와 cuDNN 설치기


<br/>

<br/>  

적용 버전 = Window10, NVIDIA GeForce GTX 1080



1. 윈도우 10 재설치
2. 그래픽카드 설치
3. Visual Code 2017 설치
4. Anaconda 2020-02 설치
5. Cuda 10.0 설치
6. CuDNN 7.6.0 설치


<br/>

<br/>  
<br/>

<br/>  



### 1. 윈도우 10 재설치

- {:.}
- USB에 윈도우이미지를 넣고 del 키 또는 F2 를 눌러 바이오스 화면으로 진입
- 화면에서 F8을 눌러 디스크를 선택하여 재설치를 진행한다
- 모든 파티션을 다 삭제
<br/>

<br/>  





### 2. 그래픽 카드 설치

- 3dp chip 또는 Nvidia 공식홈페이지에 접속하여 그래픽드라이버 설치프로그램을 다운받는다

<br/>

<br/>  


### 3. Visual Code 2017 설치

- 구글에서 visual Code 2017 을 검색 후 설치한다
- C++을 설치하는 패키지를 선택하여 설치를 진행한다 ( cuda 설치시 요구하기 때문에 미리 설치)

<br/>

<br/>  


### 4. Anaconda  설치

- 구글에서 anaconda download 를 검색하여 2020 버전을 다운받는다
- next를 누르면 설치를 진행하다 Path 부분의 체크박스를 클릭하여 설치한다

*2020 년 버전의 경우 업데이트가 되어있으므로 prompt에서 따로 업데이트를 해줄경우 충돌이 발생한다

<br/>

<br/>  


### 5. Cuda 10.0 설치

- 구글에서 cuda를 검색하여 다운로드 받는다 이때 10.1 버전을 설치시 호환이 되지않으므로 10.0을 설치한다

<br/>

<br/>  


### 6. cuDNN 설치 ###

- 구글에서 cuDNN 7.6.0 을 다운받은 후 압축을 해제한다
- Programfile -> Nvidia GPU Cumputing ToolKit -> Cuda -> 10.0 을 열어보면 bin,includ lib 폴더들이있다. 압축을 해제한 폴더안의 파일을 동일한 폴더의 파일에 덮어쓰기를 한다


---
   
<br/>

<br/>  

여기까지가 기본적인 cuda 와 cuDNN의 설치과정이다

다음으로 추가적으로 tensorflow-gpu의 설치를 코드들을 정리한다
<br/>

<br/>  



```c

conda activate tf2.0-gpu

conda install ipykernel jupyter

python -m ipykernel install --user --name tf2.0-gpu --display-name "tf-gpu"

pip install tensor flow-gpu==2.2.0

conda install pytorch==1.1.0 torchvision==0.3.0 cudatoolkit=10.0 -c pytorch   

```
<br/>

<br/>  


아나콘다 프롬프를 실행후 tf2.0-gpu라는 이름의 가상환경을 만듭니다

이름을 잊은 경우 conda info --envs 를 통해 알수있습니다

가상환경이 설치된 환경에서 tf 2.2.0을 설치해줍니다

cuda10.0과 맞는 pytorch 를 설치해줍니다. 





설치후 윈도우의 시작버튼을 누르면 jupyter notebook (tf2.0-gpu)라는 앱이 뜹니다 

단축메뉴에 추가하고 사용하는것을 추천드립니다.



 







