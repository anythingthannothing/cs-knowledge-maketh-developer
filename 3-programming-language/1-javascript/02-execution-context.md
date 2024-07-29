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
- 함수가 호출될 때 동적으로 결정된다
  - 전역에서 호출될 때: window / global
  - 함수 호출 시: window / global
> [!NOTE]
> arrow function은 this 바인딩을 하지 않고 바로 상위 컨텍스트에 있는 this를 가져다 쓴다.
 - 메서드로 호출 시: 호출한 대상 객체가 바인딩
 - callback 호출 시: 기본적으로는 함수내부에서와 동일
> [!NOTE]
> 제어권을 가진 함수가 콜백의 this를 지정해둔 경우도 있다
  - 생성자함수 호출 시: 새로 만들 인스턴스가 this가 된다
