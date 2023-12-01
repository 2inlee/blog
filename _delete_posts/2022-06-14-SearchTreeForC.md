---
layout: post
title: Search Tree(트리탐색)for C
subtitle: 알고리즘,C언어,트리
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
## 트리검색   
탐색을 하기에 가장 적합하고 많이 사용하는 구조가 트리구조이다. 특히 프로그램의 논리는 if 조건문의 참이나 거짓 두 갈래의 선택이 있는 이진구조이므로 이를 반영하여 문제 분석과 설계 단계에서 자연스럽게 이진트리가 자주 사용된다.     

이진탐색트리는 공백이 가능한 이진 트리로 공백이 아니면 다음의 성질을 만족한다.    

1. 모든 원소는 key를 갖는다.    
2. 공백이 아닌 왼쪽 서브트리의 key들은 그의 루트의 key보다 작아야한다.
3. 공백이 아닌 오른쪽 서브트리의 key들은 그의 루트의 key보다 커야한다.
4. 왼쪽과 오른쪽 서브트리도 또한 이진 탐색 트리이다 (재귀적정의)


``