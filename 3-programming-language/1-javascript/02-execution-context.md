# Execution Context
함수를 실행할 때 필요한 환경정보를 담은 객체

## 1. Call Stack
함수의 실행 순서를 제어하는 자료구조

## 2. Execution Context의 구조
### 1. Variable Environment: 식별자 정보 수집
### 2. Lexical Environment: 각 식별자의 '데이터' 추적
1. environmentRecord: 현재 문맥의 식별자 정보(hoisting)
2. outerEnvironmentReference: 현재 문맥과 관련 있는 외부 환경에 대한 참조(Scope Chain)
### 3. ThisBinding