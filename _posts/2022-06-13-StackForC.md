---
layout: post
title: Stack(스택)for C
subtitle: 알고리즘,C언어,스택
author: Ino
categories: algorithm
banner:
  # video: https://vjs.zencdn.net/v/oceans.mp4
  image: "https://user-images.githubusercontent.com/95608811/291508517-1966009e-4c10-4089-a793-f3f778f31809.png"
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

즉, 정리하자면    
1. 피연산자를 만나면 그대로 출력한다    
2. 스택이 비어있을 때 만나는 연산자는 무조건 스택에 add한다   
3. 지금 처리하려는 연산자가 스택의 top의 연산자 보다 우선순위가 높으면 스택에 add한다. 아니면 스택의 연산자를 delete하여 출력한다.    
표기식을 끝까지 다 읽으면 스택의 연산자를 delete하여 출력한다.

괄호 규칙 추가

1. 왼쪽 괄호는 스택에 들어올 때는 무조건 add 되도록하고, 일단 스택에 들어오면 우선순위가 가장 낮아져서 다음 들어오려는 연산자를 add한다.    
2. 오른쪽 괄호는 왼쪽 괄호가 나올 때까지 스택 안의 모든 연산자를 출력한다.


### 후위표기식의 장점
- 괄호가 없으므로 고려할 사항이 적음    

중위표기식에서는 연산자의 우선순위 때문에 왼쪽에서 오른쪽으로 연산이 진해되지 않고 괄호를 가지고 있기때문에 컴파일러는 중위표기식에서 후위표기식으로 변경해서 사용한다.     

### 수식 표기방식의 변경 (괄호가 없을때)
<img src="https://user-images.githubusercontent.com/95608811/173298178-0753d0e0-11d0-4d25-b262-c6176579aeae.png" width="800px">

### 수식 표기방식의 변경 (괄호가 있을때)
<img src="https://user-images.githubusercontent.com/95608811/173298522-0f500c74-173a-4841-918a-e8ca325940f7.png" width="800px">

* 괄호가 있을때는 오른쪽 괄호는 왼쪽 괄호가 나올 때까지 스택 안의 모든 연산자를 출력하면 된다.    

#### 수식 표기방식의 변경 (괄호가 있을때) 예제
<img src="https://user-images.githubusercontent.com/95608811/173299850-7dc29a00-5e6f-465c-85f2-2a59582d6f96.png" width="800px">

<img src="https://user-images.githubusercontent.com/95608811/173299961-b8be8565-5436-4de2-bcb2-540d5b6cf285.png" width="800px">

<img src="https://user-images.githubusercontent.com/95608811/173300070-c3f78bf4-b45d-4f50-a169-54193525f704.png" width="800px">

## 후위표기식의 계산 함수


```C
int cal(void){
  char symbol;
  int op1,op2,n = 0;
  int top=-1;
  symbol = pexpr[n++];
  
  while(symbol != '\0'){
    if(is_operator(symbol)){
      op2 = delete_stack();
      op1 = delete_stack();
      switch(symbol){
        case '+':add_stack(op1+op2);
          break;
        case '-':add_stack(op1-op2);
          break;
        case '*':add_stack(op1*op2);
          break;
        case '/':add_stack(op1/op2);
          break;
      }
    }
    else
      add_stack(symbol-'0');
    symbol = pexpr[n++];
  }
return delete_stack();
}
```

