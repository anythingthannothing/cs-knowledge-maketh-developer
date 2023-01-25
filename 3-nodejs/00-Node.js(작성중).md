# Node.js
## < 목표 >
### 1. Node.js의 개요에 대해 설명할 수 있다.

---

**Node.js is an open-source, cross-platform JavaScript runtime environment.**   
**Node.js는 Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임입니다.**   
한↔영 번역의 느낌이 조금 다른 것 같지만, 공식 문서를 보며 노드JS를 공부해 보자.   

---

## 1. Node.js
### 1.1 JavaScript Runtime, V8, cross-platform?
JS는 정적이었던 웹페이지에 사용자와의 상호작용을 가능하도록 하기 위해 개발된 언어다.   
자연스럽게 JS는 브라우저에서만 실행되었으며 그 목적에 맞게 제한된 기능만을 가지고 있었다.   
웹 브라우저는 JavaScript가 실행되는 환경, 즉 유일한 JavaScript Runtime이었던 것.   
그런 JS를 브라우저 외부(cross-platform ➡ Windows, Linux, MacOS)에서도 사용할 수 있도록   
1. Google에서 개발한 JavaScript Runtime인 V8 엔진이라는 오픈 소스와,   
2. libuv라는 오픈 소스 라이브러리를 기반으로 동작하는 Runtime이 Node.js다.   

Node.js는 개발자가 작성한 JS 코드를 해석하고 실행하는 역할을 하며,   
C언어로 작성된 libuv 모듈을 사용하기 위해 V8 엔진의 도움을 받아 브라우저의 JS에서는 불가능한 동작을 수행한다.

### 1.2 싱글 스레드
Node.js 기반의 어플리케이션은 실행될 때 하나의 스레드를 생성한다.
해당 스레드 안에는 특정 시점에 어떤 코드를 실행할 지를 결정하는 '이벤트 루프'가 존재한다.
이벤트 루프는 처리 시간이 긴 작업(crypto 모듈 등)을 스레드 풀에 위임하여 처리한다.
스레드 풀은 기본적으로 4개의 스레드로 구성되어 있으며,
스레드 풀이 위임받아 처리하는 작업은 완료되기 전까지 pending 상태로 남아 있다.
이벤트 루프의 콜 스택이 모두 비워지면 스레드 풀의 작업을 마저 진행한다.

---

## 2. Node.js는 싱글 스레드

### 2.1 소주제1

### 2.2 소주제2

---

## 3. 대주제3

### 3.1 소주제1

### 3.2 소주제2


---