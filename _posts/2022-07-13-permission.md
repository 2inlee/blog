---
layout: post
title: 권한의 이해와 설정
subtitle: permission
author: Ino
categories: System
banner:
  # video: https://vjs.zencdn.net/v/oceans.mp4
  image: "https://shorturl.at/oBCQR"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: [linux]
sidebar: []
---

## 권한이란?    
리눅스의 모든 파일과 디렉토리는 권한(permission)을 가지고 있다.         
리눅스의 파일시스템 상에 권한에 대한 정보를 저장하는 부분이 있다.         
퍼미션들은 시스템 상에 존재하는 파일들에 대한 읽기,쓰기,실행에 대한 접근 여부를 결정한다.         
ls -l 명령어로 확인 가능 (첫번째 필드, -rwxr-wr--)        
이러한 퍼미션은 다중 사용자 환경을 제공하는 리눅스 환경에서는 가장 기초적인 접근 통제 방법        

<img src="https://user-images.githubusercontent.com/95608811/178721039-e1d58298-5f8b-4631-9855-2d9f8a9ab85e.png" width="800px">

### 권한 설정 방법
- `chmod [권한] [파일 또는 디렉토리 이름]`      
- `[권한]` : 권한을 입력할 때는 심볼릭 모드와 옥텟(8진수) 모드 2가지 방식을 이용하여 입력 가능하다.     
- `[파일 또는 디렉토리 이름]` : 파일, 디렉토리를 지정할 때는 절대 경로 또는 상대 경로 모두 가능하다.    

#### 간단한 문자로 설정하는 심볼릭 모드

<img src="https://user-images.githubusercontent.com/95608811/178722799-93b80ea6-da07-454b-8348-6bc80a13dce4.png" width="800px">

#### 0~7까지의 숫자를 이용하는 옥텟 모드
<img src="https://user-images.githubusercontent.com/95608811/178723045-a3e07723-7860-4028-aec4-bf861bea8b42.png" width="800px">

> 읽기 쓰기 실행 순서로 각각 4,2,1 이고, 읽기와 쓰기만 있으면 4+2인 6 쓰기와 실행만 있으면 2+1 인 3
이런식으로 옥텟모드를 사용한다.     

### 파일 또는 디렉토리를 생성할 때 권한값을 결정하는 umask
<img src="https://user-images.githubusercontent.com/95608811/178723739-7380eb92-d892-49e7-b496-f97123799e5d.png" width="800px">

- umask 값은 리눅스를 처음 설치할때 022이 기본값으로 세팅되어 있는데, directory는 777, file은 666이
기본 값이라 각자의 권한값에서 umask 값을 뺀(and 연산) 한 값이 각자의 권한값 (옥텟)이 된다.    

