# Union & Intersection
## Union(|)
- 유니언은 TS에서 타입을 병합할 수 있는 방법 중 하나
- 합집합의 개념
  - 최소 하나의 타입을 만족해야 함
  - 하나의 타입을 만족한다면 다른 타입의 일부 프로퍼티만 추가하는 것이 가능

## Intersection(&)
- 유니언과 달리 모든 타입을 만족해야 한다

## Narrowing
- 유니언 타입에서 더욱 구체적인 타입으로 유추할 수 있도록 하는 것

### Narrowing의 종류
1. Assignment Narrowing
    - 특정 값을 직접 할당해서 타입 유추
2. typeof Narrowing
    - 런타임 시 typeof를 통해 타입을 직접 확인
3. Truthiness Narrowing
    - falsy한 값을 체크하여 타입 유추
4. Equality Narrowing
    - 논리적 연산을 통해 타입 유추
5. in operator Narrowing
    - 특정 타입에만 존재하는 프로퍼티의 존재 유무를 통해 타입 유추
6. instanceof Narrowing
7. Discriminated union Narrowing
    - 타입 선언 시 부여한 공통적인 프로퍼티를 기반으로 타입 유추
8. Exhaustiveness checking
    - switch문 등을 통해 가능한 모든 경우의 수를 확인하여 타입 유추