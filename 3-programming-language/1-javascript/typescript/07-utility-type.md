# Utility Type
## Partial
- 입력받은 제네릭 타입에 존재하는 프로퍼티만 일부분 또는 전부를 포함하는 타입

## Required
- 입력받은 제네릭 타입에 존재하는 optional 프로퍼티를 모두 required로 변경하는 타입

## Readonly
- 입력받은 제네릭 타입의 모든 프로퍼티를 readonly로 변경
- vanilla js의 Object.freeze()와 비슷하게 동작

## Pick
- 입력받은 제네릭 타입의 일부 프로퍼티만 포함하는 타입

## Omit
- 입력받은 제네릭 타입의 일부 프로퍼티를 제외하는 타입
- Pick 타입의 반대

## Exclude
- 입력받은 제네릭 Union 중 특정 타입을 제외하는 타입

## Extract
- 입력받은 제네릭 Union 중 특정 타입만 포함하는 타입

## NonNullable
- 입력받은 제네릭 Union 중 null과 undefined를 제외한 Union 타입

## Parameters
- 함수의 파라미터를 타입으로 전환하는 데에 사용

## ConstructorParameters
```typescript
type ConstructorParamType = ConstructorParameters<typeof Class>;
```

