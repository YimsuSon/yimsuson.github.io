---
title: AWS 파이토치 서버 만들기
excerpt: AWS, Pytorch, Flask Server


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


# 1. AWS 프리티어 계정으로 EC2 생성

Elastic Block Store -> 볼륨 -> 작업 -> 볼륨 수정

25 GB로 수정


# 2. SSH키를 사용하여 터미널 접속

lsblk

sudo growpart /dev/xvda 1 

lsblk

sudo resize2fs /dev/xvda1

df -h

 

# 3. Jupyter Notebook 설치


``` c


sudo apt-get update


# Python package 설치
sudo apt-get install python3-pip

# Jupyter notebook을 설치
sudo pip3 install notebook

# Notebook에 비밀번호를 설정
python3

from notebook.auth import passwd
passwd(algorithm='sha1')



# sha1:dsfjqowjfpo   <- hash값 가지고 있기
exit()

# Jupyter 환경설정
jupyter notebook --generate-config


# vim으로 환경설정 파일 수정
vim /home/ubuntu/.jupyter/jupyter_notebook_config.py

# a누르고 파일 제일 하단에 다음 추가 후 esc -> :wq!
c = get_config()
c.NotebookApp.password = u'{아까 설정했던 hash값}'
c.NotebookApp.ip = '{현재 ec2의  ip값}'
c.NotebookApp.notebook_dir = '/' 




# jupyter notebook root권한으로 실행
sudo jupyter notebook --allow-root


# ec2 인스턴스의 인바운드 규칙 편집
8888 추가 하여 포트열기

# 퍼블릭 ip4주소로 접속
ip:8888

# jupyter notebook이 항상 돌아가도록 설정
ctrl-z
bg
disown -h





## 인증서 적용(https)
# 8888포트로 돌아가고 있는 process를 확인
sudo netstat -nap | grep 8888


#kill 명령어로 종료
sudo kill -9 19827

cd /home/ubuntu
pwd
mkdir ssl
cd ssl

# 인증서 유효기간은 365일 
# rsa 알고리즘을 적용한 key
# 개인키(private key)는 cert.key 
# 공개키(public key)는 cert.pem 

sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout "cert.key" -out "cert.pem" -batch



# jupyter notebook 환경설정 파일을 다시 열어서 수정
vim /home/ubuntu/.jupyter/jupyter_notebook_config.py


c.NotebookApp.certfile = u'/home/ubuntu/ssl/cert.pem'
c.NotebookApp.keyfile = u'/home/ubuntu/ssl/cert.key' ( ‘ 작은따음표 ‘ )


# 다시 jupyter notebook을 실행
sudo jupyter-notebook --allow-root




## 서버가 종료된 후 재부팅 되어서도 jupyter notebook 관련 명령어들이 자동으로 실행될 수 있도록, 서버시스템으로 등록
ctrl-c

# jupyter-notebook 실행파일의 위치 검색
which jupyter-notebook


# 서비스 파일을 작성
sudo vim /etc/systemd/system/jupyter.service


[Unit]
Description=Jupyter Notebook Server

[Service]
Type=simple 
User=ubuntu 



ExecStart=/usr/bin/sudo /usr/local/bin/jupyter-notebook --allow-root --config=/home/ubuntu/.jupyter/jupyter_notebook_config.py


[Install]
WantedBy=multi-user.target



# jupyter-notebook을 실행
sudo systemctl daemon-reload


# jupyter를 사용가능한 모드로 생성
sudo systemctl enable jupyter

# jupyter를 이제 항상 실행상태 만듬
sudo systemctl start jupyter

# 확인
sudo systemctl status jupyter


# 사파리에서 퍼블릭 IPv4로 접속

```



# 4. 도커 컨테이너 설치


``` c

sudo apt install software-properties-common

curl -fsSl https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" ( “ 큰따옴표 )

sudo apt update

apt-cache policy docker-ce

sudo apt install docker-ce

sudo docker pull hello-world

sudo docker run hello-world



```



# 5. 파이토치 서버

``` c

git clone https://github.com/YimsuSon/Torchdocker2.git

cd Torchdocker2/

sudo docker build -t test6 .

sudo docker run -d -it -p 0.0.0.0:5000:5000/tcp test11

```



