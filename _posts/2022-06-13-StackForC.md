---
layout: post
title: Stack(스택)for C
subtitle: 알고리즘,C언어,스택
author: Ino
categories: algorithm
banner:
  # video: https://vjs.zencdn.net/v/oceans.mp4
  image: "https://user-images.githubusercontent.com/95608811/169932444-32124c9a-4013-4864-acf7-59a3db654886.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: [C,algorithm]
sidebar: []
---

## 스택의 정의    
- 한쪽 끝(top)에서 삽입과 삭제가 일어나는 선형리스트
LIFO(Last In First Out) 구조    
- 선형리스트의 긑부분에서만 자료의 입력과 출력이 가능하도록 제한된 자료구조
- 마지막 삽입 (Last-In)한 원소는 맨 위에 쌓여 있다가 가장먼저 삭제(First-Out) 된다.   
> 후입선출 구조 (LIFO)      
- 스택을 운영하기 위하여 끝 부분(top)에 대한 정보가 필요함.    

<img src="https://user-images.githubusercontent.com/95608811/173239877-8cfb6ccb-55de-4376-804e-a2efea200fe4.png" width="800px">

> 위 그림처럼 끝 부분(top) 에서만 삽입과 삭제가 일어남.     


## 스택의 연산    
- 현재 스택의 상태를 나타내는 변수 top, 데이터를 담을 배열 stack이 필요하다.    

(1) 삽입    
스택이 full한지 check     
top++, stack[top] = data    
(2) 삭제
스택이 empty인지 check    
데이터 꺼내 사용, top--     


## 수식의 표기법
연산자의 위치에 따라 수식의 표기법을 구분할 수 있다.    

- 전위표기법 : 연산자가 피연산자 앞에 오는 표기법     

- 중위표기법 : 일상 사용하는 방법     

- 후위표기법 : 연산자가 피연산자 뒤에 오는 표기법, 괄호를 사용하지 않아서 컴파일러에서 사용하는 표기법이다.     

### 중위표기식을 후위표기식으로 변환하는 알고리즘     

각 연산자, 피연산자를 하나씩 읽으면서 스택에 저장과 출력이란 2가지 동작을 조합하여 수행함     

- `피연산자` : 항상 출력   
- `연산자` : 아래 과정을 스택에 저장될 때까지 반복    


if((새 연산자의 우선순위 > 스택의 top연산자의 우선순위) or (스택이 비었음))   
->  스택에 저장     
else (top의 연산자를 pop하여 출력)
이후 식을 다 읽었으면 스택에 있는 모든 연산자를 pop 하여 출력     


