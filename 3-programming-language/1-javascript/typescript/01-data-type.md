# Data Type
## Basic Types
## 1. any vs unknown
- any와 unknown 모두 어떠한 타입이든 할당할 수 있다는 점에서 동일하게 동작
- any는 다른 변수에 재할당 가능, unknown은 any, unknown 타입 이외의 다른 변수에 재할당 불가

## 2. never
- 어떠한 값도 저장되거나 반환되지 않을 때 사용
- 함수에서 에러를 던지거나 무한 루프 등에 사용