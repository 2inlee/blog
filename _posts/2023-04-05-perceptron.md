---
layout: post
title: 인공신경망과 퍼셉트론
subtitle: feat.분류/회귀
author: Ino
categories: ai
banner:
  image: "https://user-images.githubusercontent.com/95608811/291508517-1966009e-4c10-4089-a793-f3f778f31809.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: [ai]
sidebar: []
---

## 퍼셉트론과 신경망
* * *

퍼셉트론은 신경망의 기본 구성요소입니다.    
신경망(Neural Net)의 기본 구조를 보면 보통 아래와 같이 그립니다.    

<img src="https://user-images.githubusercontent.com/95608811/229966707-cea3fd99-1930-406b-b8a8-70a33e52b74f.png" width="800px">
이 중 파란색으로 동그라미 친 부분, 신경망의 구성요소를 `퍼셉트론`이라고 합니다.   
> 다른 말로는 Dense(밀집) 혹은 노드(Node) 라고도 부릅니다.    


## 퍼셉트론의 구성요소
* * *
위 그림의 신경망에서 하나의 퍼셉트론을 확대해서 보면,

<img src="https://user-images.githubusercontent.com/95608811/229966745-2b1c6bbe-0a89-4718-a437-9ce6c2d56d7c.png" width="800px">

그림과 같이 퍼셉트론은 `입력(inputs)`, `가중치(Connection Weight)`, `바이어스(bias)`, `합 연산(Sum)`, `활성 함수(Activation Function)`로 구성되어 있습니다.   
오느날 인공신경망에서 이용하는 퍼셉트론은 선형 분류기로 이는 입력과 가중치들의 곱을 모두 더한 뒤 활성 함수를 적용해서 그 값이 0보다 크면 1, 0보다 작으면 -1을 출력하는 구조이다.    


<img src="https://user-images.githubusercontent.com/95608811/176060497-7cb6bb9e-1493-4ac0-8209-48fb38ade3da.png" width="800px">

- 그래서 입력을 넣고 입력에 대한 결과를 출력하였을때 원하는 값이 나오도록 가중치를 조절한다.    
`학습`이라는게 결국 그 가중치값을 가장 많은 입력에 대해 가장 근접한 `가중치`를 찾는 과정이라고 볼 수 있다.

## 신경망으로 풀 수 있는 문제들
* * *
활성화 함수, 네트워크 구조 변경을 통해 문제를 풀 수 있습니다.   
대표적인 문제로는 `분류(Classification)`와 `회귀(Regression)`로 나눌 수 있습니다.   

### 분류(Classification)
실생활에서 AI가 적용되는 많은 분야는 분류문제를 해결한 것이 많습니다.   
그 예로는 개와 고양이를 분류하는 문제 또는 물체를 Detection 하였을 때, 어떤 물체인 지 분류하는 문제 등    
실생활에서 많은 부분에 사용되고 있습니다.   

<img src="https://user-images.githubusercontent.com/95608811/229966775-a3bc8443-2914-4fab-87a6-bc04c0f34589.png" width="800px">

위 사진과 같이 분류해야 하는 `class의 갯수` 만큼 `Output layer`의 퍼셉트론 개수가 정해지게 된다.    

### 회귀(Regression)
분류를 제외한 다른 문제는 회귀(Regression)문제에 해당합니다.    
공부한 시간(x)을 가지고 합격확률(y)를 예측하거나, 키(x)를 가지고 몸무게(y)를 예측하는 등 분류하는 것이 아니라 확률 또는 값과 같은 숫자를 맞추는 문제라고 생각하면 됩니다.   

<img src="https://user-images.githubusercontent.com/95608811/229966792-2ed7e419-001b-47a1-8ace-602987da7dbc.png" width="800px">

위와 같은 간단한 예시에서는 보통 Output layer의 퍼셉트론 개수를 하나로 두는 경우가 많습니다.    
이런 문제에 대해서 마지막 퍼셉트론의 활성화 함수를 정할 때, 활성함수를 문제에 맞게끔 설정해야 합니다.   
0~1 사이의 확률을 가리키는 문제에서는 시그모이어함수, 다채로운 값을 가질 수 있을땐 ReLU 등    
활성함수에 대해서는 다음 포스팅에서 다루겠습니다.   
