# Object
## Property Attribute
### Data Property
- 키와 값으로 형성된 실질적 값을 갖고 있는 프로퍼티
### Accessor Property
- 값을 갖고 있지는 않지만 다른 값을 가져오거나 설정할 때 호출되는 함수로 구성된 프로퍼티
  - getter & setter
1. value: 실제 프로퍼티의 값
2. writable: 값의 수정 가능 여부
3. enumerable: 열거 가능 여부(for ... in 등)
4. configurable: 프로퍼티 어트리뷰트의 재정의(삭제, 변경 등) 가능 여부
   - writable이 true인 경우 값 변경과 writable을 변경하는 것은 가능

## Immutable Object
### 1. Extensible
- 새로운 프로퍼티를 추가 가능 여부
  - 삭제는 가능
### 2. Seal
- 프로퍼티 추가/삭제 가능 여부, configurable을 false로 변경

### 3. Freeze
- 읽기 외 모든 기능 불가
  - enumerable 외 writable & configurable을 false로 변경

## Constructor Function
- js에서 class는 함수형