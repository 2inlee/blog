---
layout: post
title: 자바스크립트에 대해서
subtitle: Feat.Javascript
author: Ino
categories: web
banner:
  # video: https://vjs.zencdn.net/v/oceans.mp4
  image: "https://shorturl.at/oBCQR"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: [web, javascript]
sidebar: []
---
## 1.자바스크립트의 특징
자바스크립트는 HTML, CSS와 함께 웹을 구성하는 요소 중 하나로 웹 브라우저에서 동작하는 유일한 프로그래밍 언어이다.
(Vue,React,Angular 등도 javascript기반으로 만들어진 프레임워크이다.)
> ~python기반의 pyscript도 javascript 기반이다.~
자바스크립트는 기존의 프로그래밍 언어에서 많은 영향을 받았다.
기본 문법은 C, Java와 유사하고 Self에서는 프로토타입 기반 상속을, Scheme에서는 일급 함수의 개념을 차용했다.
> ~ 그래서 매우 근본이 없다.. 필요해서 막 만들었다는게 학계의 정설이다 ~    
자바스크립트는 개발자가 별도의 컴파일 작업을 수행하지 않는 인터프리터 언어(Interpreter language)이다.   

> 그리고 여러 논란이 있지만(?) 자바스크립트는 프토로타입 기반의 객체지향 언어이다.
    
## 2.자바스크립트의 실행환경
모든 브라우저는 자바스크립트를 해석하고 실행할 수 있는 자바스크립트 엔진을 내장하고 있다. 브라우저뿐만 아니라 Node.js도 자바스크립트 엔진을 내장하고 있다. 따라서 자바스크립트는 브라우저와 Node.js 환경에서 실행할 수 있다. 기본적으로 브라우저에서 동작하는 코드는 Node.js 환경에서도 동작한다.

그런데 브라우저와 Node.js는 존재 목적이 다르다. 브라우저는 HTML, CSS, 자바스크립트를 실행하여 웹 페이지를 화면에 렌더링하는 것이 주된 목적이지만, Node.js는 서버 개발 환경을 제공하는 것이 주된 목적이다.

예를 들어 브라우저는 HTML 요소를 선택하거나 조작하는 기능들의 집합인 DOM API를 기본적으로 제공한다. 하지만 서버 개발 환경을 제공하는 것이 주 목적인 Node.js는 클라이언트 사이드 Web API인 DOM API를 제공하지 않는다. 서버에서는 HTML 요소를 다룰 일이 없기 때문이다. 반대로 Node.js에서는 파일을 생성하고 수정할 수 있는 File 시스템을 기본 제공하지만 브라우저는 이를 지원하지 않는다.