# Closure
- A Closure is the combination of a function bundled together(enclosed) with references to its surrounding state(the lexical environment).
- 내부함수와 외부함수의 lexicalEnvironment의 조합
  - 내부함수의 outerEnvironmentReference + 외부함수의 environmentRecord
- 외부함수에서 선언한 변수를 내부함수 B에서 참조할 경우에 발생하는 특별한 현상
- 외부함수에서 선언한 변수를 참조하는 내부함수를 외부함수 외부에서 참조할 경우 외부함수가 종료된 이후에도 내부함수에서 참조하는 외부함수의 변수가 GC의 대상이 되지 않는 현상
- 클로저를 통해 지역변수를 함수가 종료된 이후에도 다른 대상에 의해 참조될 수 있게 할 수 있음
- 클로저는 외부로부터 내부의 변수를 보호하는 캡슐화의 역할을 하기도 함