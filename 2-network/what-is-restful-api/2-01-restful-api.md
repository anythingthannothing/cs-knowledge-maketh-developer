# 'REST'ful API란 무엇일까?

REST는 '**RE**presentational **S**tate **T**ransfer'의 축약어로, 분산형 미디어 시스템에 대한 스타일 가이드라고 할 수 있다.  
다른 여러 구조들의 스타일 가이드와 마찬가지로 REST 또한 가이드라인과 제약조건들을 가지고 있으며  
**RESTful**하다는 것은 결국 이러한 가이드 라인을 잘 준수한다는 것을 의미한다.

> RESTful API: REST 구조의 스타일 가이드를 준수하는 웹 API 또는 웹 서비스!
>
> > API(Application Programming Interface) => 컴퓨터끼리 의사소통하기 위한 방법!

---

## 1. REST의 스타일 가이드

REST의 스타일 가이드 라인은 총 6가지가 존재한다.

### 1.1 일관된 인터페이스

API에 통일된 규칙을 적용함으로써 전체적인 시스템을 단순화하고, 상호작용을 더욱 명시적으로 보여주어야 한다.

- Resource의 식별화 => 인터페이스를 통해 리소스를 식별할 수 있어야 한다.
- 일관된 형태 => 각 리소스는 인터페이스 내에서 일관성을 지녀야 한다.
- 자기묘사적 표현 => 각 리소스는 스스로를 통해 충분한 정보를 전달해야 한다.   
- 하이퍼미디어 그 자체 => 클라이언트는 초기 URI만을 통해 동적으로 모든 자원과 다양한 상호작용을 할 수 있어야 한다.
![best versus worst practice](/assets/1.1-uniform-interpace.png)

### 1.2 Client <-> Server의 분리

서버와 클라이언트를 분리(관심사의 분리)시킴으로써 클라이언트와 서버가 각각 독립적으로 진화해나갈 수 있도록 해야 한다  
클라이언트는 유저 인터페이스에,  
서버는 데이터 관리에 각각 관심사를 분리하여  
유저 인터페이스를 기반으로 다양한 디바이스 및 플랫폼에 대응할 수 있고  
서버의 구성요소 또한 단순화하여 확장성을 높일 수 있다.  
이처럼 클라이언트와 서버를 분리하여 클라이언트와 서버가 각각 진화해 나가는 과정에서 서로에 대해 영향을 끼치지 않도록 해야 한다

### 1.3 무상태(Stateless)

무상태란 클라이언트로부터의 요청(request)에 요청 처리를 위한 모든 정보를 담아야 한다는 것을 의미한다.
서버는 서버에 미리 저장해 둔 정보를 통해 요청을 처리해서는 안된다.
이를 위해 클라이언트 어플리케이션(웹 브라우저)는 항상 세션을 유지해야 한다

### 1.4 캐싱 여부(Cacheable)

Cacheable이란 서버로부터의 응답(request)은 암묵적이든 명시적이든 반드시 캐시가능성에 대한 정보를 가져야 한다는 규칙이다.  
만약 응답이 캐쉬 가능한 것이라면, 클라이언트는 응답 데이터를 일정 기간 동안 재사용할 수 있다.
![cacheable](/assets/1.4-cacheable.png)

### 1.5 계층적 구조(Layered System)

계층적 구조는 각 구성 요소의 작용을 제한시킴으로써 전체 구조가 계층적으로 구성될 수 있도록 하는 것을 의미한다

### 1.6 Code on Demand(Optional)

REST는 클라이언트 사이드에서 코드를 다운받고, 실행하는 것을 허용한다.

---

## 2. Resource는 무엇일까?

Resource는 REST 구조에서 정보를 추상화한 핵심 요소라고 할 수 있다.  
우리가 이름을 붙여 표현할 수 있는 것은 모두 Resource이며,  
문서, 이미지, 리소스들의 집합 또는 추상적이지 않은 대상 또한 Resource가 될 수 있다 ex) 사람  
리소스는 크게 3가지로 구성되며,

- 자료 그 자체
- 해당 Resource에 대한 메타 데이터
- 추가적으로 접근하고자 하는 다른 Resource에 대한 하이퍼링크
  > REST API는 서로 연결된 자원들의 집합이라고 할 수 있으며, 이러한 Resouce들의 집합을 REST API의 Resource Model이라고 한다.

---

## 3. RESTful API 설계를 위한 Tip

### 3.1 URL의 구조를 Collections(복수) -> Singleton(단수)로, Collection -> Sub-collection으로 설계할 것

### 3.2 URL에는 (최대한) 명사만을 활용할 것

### 3.3 Resource를 필터링할 때에는 쿼리 파라미터를 활용할 것

### 3.4 가독성을 위해서는 '-'(하이픈)을 사용할 것('\_' X)

---

## 4. Summary

결론적으로 REST란 각종 데이터와 기능들을 Resource로 정의하고, Resource에 대한 접근을 URI를 통해 하도록 하는 구조라고 할 수 있다.  
RESTful한 API를 위해서는 다음과 같은 6가지의 가이드 라인을 준수해야 한다.

1. 일관된 인터페이스
2. 클라이언트 <-> 서버의 분리
3. 무상태(Stateless)
4. 캐시 가능성
5. 계층적 구조
6. Code on Demand(Optional)

각 Resource는 단순하고, 제대로 설계된 방식을 기반으로 클라이언트 <-> 서버 사이에서 작동해야 하며,  
표준화된 인터페이스와 프로토콜 위에서 Resource가 교환되어야 한다.
각 Resource의 메타 데이터는 1) 캐싱 2) 에러 감지 3) 컨텐츠 협상 4) 인증 5) 권한 관리를 위해 사용되며,  
클라이언트와 서버 사이의 상호작용은 무상태로 이루어져야 한다.  
RESTful API란 결국 어플리케이션을 단순하고, 가볍고, 빠르게 만드는 것이 목적이라고 할 수 있다.

> 참고 자료
>
> > REST API Tutorial: https://restfulapi.net/  
> > REST의 창시자인 Roy T. Fielding의 포스트: https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven

> 더 읽어보면 좋을 자료
>
> > REST Resource Naming Guide: https://restfulapi.net/resource-naming/
