# Data Type
## Primitive Type
### 1. Number
### 2. String
### 3. Boolean
### 4. null
- null의 type은 object로, 버그지만 하위호환성을 위해 수정되지 않음
### 5. undefined
### 6. Symbol
- 유일한 값을 생성할 때 사용하며, Symbol 함수를 호출해서 생성

## Reference Type(Object)
### 1. Array
### 2. Function
### 3. RegExp
### 4. Set & WeakSet
### 5. Map & WeakMap

## Hoisting
- 모든 변수의 선언이 코드가 실행되기 이전에 이루어지는 현상
- let과 const도 Hoisting의 대상이 되며, var와 달리 초기화가 되지는 않음
  - var는 Hoisiting 시 선언과 함께 undefined로 초기화가 이루어짐
- var는 함수 레벨 스코프만 생성하고, let & const는 함수 레벨 스코프와 블록 레벨 스코프 모두 생성