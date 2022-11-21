# HTTP Method

## 0. HTTP 개요
HTTP(Hyper Text Transfer Protocol)는 인터넷 상에서 발생하는   
클라이언트 ↔ 서버 || 서버 ↔ 서버 사이의 모든 정보 교환 과정에서 지켜야할 약속이다.   
> ❗ Hyper Text란 HTML, 사진, 동영상, 파일, JSON 등 인터넷에서 주고 받을 수 있는 모든 정보를 의미한다.   

인터넷 초기에는 리소스를 요청하는 GET 메서드만을 지원했으나,   
현재는 다양한 메서드를 사용할 수 있을 뿐만 아니라 HTTP 헤더를 설정하는 등 다양한 동작을 수행할 수 있게 됐다.   
웹 상의 서로 다른 프로그램 사이에서의 통신은 HTTP를 기반으로 이루어지며,
HTTP 요청(Request)의 성격을 구분짓기 위해 사용되는 것이 HTTP Method,
HTTP 응답(Response)의 결과를 구분짓기 위해 사용되는 것이 HTTP Status 코드다.

> HTTP Method ➡ 클라이언트(서버)가 서버에게 요청하는 작업의 종류를 구분하는 것   
> HTTP Status Code ➡ 서버가 클라이언트(서버)의 요청(Request)에 대한 응답 결과를 간략히 표현한 것   
>> End-Point ➡ Url + Method의 조합을 통해 유일하게 구별될 수 있는 주소값

---

## 1. HTTP 메서드의 종류

HTTP 메서드 중에서 중요하고 사용 빈도가 높은 메서드는 다음과 같다.

### 1.1 ★ GET

리소스를 조회하는 데에 사용되며, 서버에 전달할 데이터는 query string을 활용한다.
❗ GET 요청에도 Body에 데이터를 담을 수 있지만 권장하지 않는 방식이다.

- Resource의 식별화 => 인터페이스를 통해 리소스를 식별할 수 있어야 한다.
- 일관된 형태 => 각 리소스는 인터페이스 내에서 일관성을 지녀야 한다.
- 자기묘사적 표현 => 각 리소스는 스스로를 통해 충분한 정보를 전달해야 한다.   
- 하이퍼미디어 그 자체 => 클라이언트는 초기 URI만을 통해 동적으로 모든 자원과 다양한 상호작용을 할 수 있어야 한다.
![일관된 인터페이스 설명 자료](/assets/restful-api/1.1-uniform-interpace.png)

### 1.2 ★ POST

Request Body를 통해 전달한 데이터에 대한 처리를 요청할 때 사용한다.
대부분 새로운 리소스를 등록하는 데 사용되며 로그인, 결제 등 새로운 리소스를 생성하지 않는 경우도 있다.
1. 새로운 리소스 생성 요청 ➡ 게시글, 댓글, 회원가입 등
2. 전달한 데이터를 기반으로 특정 동작 수행 ➡ 로그인 등
3. 한정된 Method로 인해 처리하기 어려운 동작 ➡ 주문 상태 변경(주문 취소, 주문 확인 중, 상품 준비 중 등등)
❗ Body에 데이터를 담지 않는다면 POST를 쓸 지에 대해 한 번 더 고민해야 한다.

### 1.3 ★ PUT

무상태란 클라이언트로부터의 요청(request)에 요청 처리를 위한 모든 정보를 담아야 한다는 것을 의미한다.
서버는 서버에 미리 저장해 둔 정보를 통해 요청을 처리해서는 안된다.
이를 위해 클라이언트 어플리케이션(웹 브라우저)는 항상 세션을 유지해야 한다.

### 1.4 ★ DELETE

Cacheable이란 서버로부터의 응답(request)은 암묵적이든 명시적이든 반드시 캐시가능성에 대한 정보를 가져야 한다는 규칙이다.  
만약 응답이 캐쉬 가능한 것이라면, 클라이언트는 응답 데이터를 일정 기간 동안 재사용할 수 있다.
![cacheable 설명 자료](/assets/restful-api/1.4-cacheable.png)

### 1.5 PATCH

계층적 구조는 각 구성 요소의 작용을 제한시킴으로써 전체 구조가 계층적으로 구성될 수 있도록 하는 것을 의미한다.
![계층적 구조 설명 자료](/assets/restful-api/1.5-layered-system.png)

### 1.6 OPTIONS

REST는 클라이언트 사이드에서 코드를 다운받고, 실행하는 것을 허용한다.
![Code on Demand 설명 자료](/assets/restful-api/1.6-code-on-demand.png)

### 1.7 HEAD

---

## 2. Method의 속성

Resource는 REST 구조에서 정보를 추상화한 핵심 요소라고 할 수 있다.  
우리가 이름을 붙여 표현할 수 있는 것은 모두 Resource이며,   
문서, 이미지, 리소스들의 집합 또는 추상적이지 않은 대상 또한 Resource가 될 수 있다. ex) 사람  
리소스는 크게 다음과 같이 3가지로 구성된다.

- 자료 그 자체
- 해당 Resource에 대한 메타 데이터
- 추가적으로 접근하고자 하는 다른 Resource에 대한 하이퍼링크   

> REST API는 서로 연결된 자원들의 집합이라고 할 수 있으며, 이러한 Resouce들의 집합을 REST API의 Resource Model이라고 한다.
>> URI? URL? URN?
>>> URI(Uniform Resource Identifier): 특정 자원을 식별할 수 있도록 하는 일정한 규칙을 가진 모든 식별자   
>>> ★URL(Uniform Resource Locator): 주소 식별자   
>>> URN(Uniform Resource Name): 이름 식별자   

---

## 3. RESTful API 설계를 위한 Tip

### 3.1 URL의 구조를 Collections(복수) -> Singleton(단수)로, Collection -> Sub-collection으로 설계할 것

### 3.2 URL에는 (최대한) 명사만을 활용할 것

### 3.3 Resource를 필터링할 때에는 쿼리 파라미터를 활용할 것

### 3.4 가독성을 위해서는 '-'(하이픈)을 사용할 것('_' X)

### 3.5 URL에는 소문자만 사용할 것   

![RESTful API 설계 팁 설명 자료](/assets/restful-api/3-tip.png)   

---

## 4. Summary

결론적으로 REST란 각종 데이터와 기능들을 Resource로 정의하고,   
Resource에 대한 접근을 일관성 있는 URI를 통해 하도록 하는 구조라고 할 수 있다.  
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

> 추천 자료
>> REST API Tutorial: https://restfulapi.net/  
>> REST Resource Naming Guide: https://restfulapi.net/resource-naming/

> 더 읽어보면 좋을 자료
>> REST의 창시자인 Roy T. Fielding의 포스트: https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven
