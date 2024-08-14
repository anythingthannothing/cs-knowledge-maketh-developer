# Function
## Function Signature
함수 시그니처를 type 또는 interface를 통해 선언 가능
```ts
interface IAdd {
    (x: number, y: number): number;
}

const add: IAdd = (x, y) => x + y;
```

## Overloading
함수 또는 메서드의 이름은 같지만 시그니처(파라미터의 형태)는 다른 함수/메서드를 중복으로 선언 

## Statement vs Expression

## Type Predicate
