# Decorator
## Class Decorator

## Method Decorator
```typescript
function MethodDecorator(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    // propertyKey는 메서드의 이름
    // descriptor는 value와 속성값에 대한 정보
}
```

## Accessor Decorator
- getter와 setter의 조작
- signature는 Method Decorator와 동일

## Property Decorator
```typescript
function PropertyDecorator(target: any, propertyKey: string) {
    
}
```

## Parameter Decorator
```typescript
function ParameterDecorator(target: any, propertyKey: string, paramIndex: number) {
    
}
```