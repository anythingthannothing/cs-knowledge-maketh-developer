# Data Type
## Basic Types
## 1. any vs unknown
- any와 unknown 모두 어떠한 타입이든 할당할 수 있다는 점에서 동일하게 동작
- any는 다른 변수에 재할당 가능, unkonwn은 any, unknown 타입 이외의 다른 변수에 재할당 불가

## 2. never
- 어떠한 값도 저장되거나 반환되지 않을 때 사용

## type vs interface
- interface는 type의 한계를 보완하기 위해 나중에 추가된 기능
- type과 interface는 각각의 역할이 존재하며 서로를 완전히 대체하지는 못함
- type에는 원시값을 할당할 수 있으나 interface는 원시값 할당 불가능