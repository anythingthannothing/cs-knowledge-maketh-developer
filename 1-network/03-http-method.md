# HTTP Method

## 목표
### 1. HTTP의 주요 메서드들에 대해 설명할 수 있다.
### 2. HTTP 메서드들이 가진 속성에 대해 설명할 수 있다.
### 3. RESTful API 설계 방식에 대해 설명할 수 있다.

---
<br>

## 0. HTTP 개요
HTTP(Hyper Text Transfer Protocol)는 인터넷 상에서 발생하는   
클라이언트 ↔ 서버 || 서버 ↔ 서버 사이의 모든 정보 교환 과정에서 지켜야할 약속이다.   
이러한 과정에서 클라이언트와 서버는 **HTTP 메시지**를 통해 데이터를 주고 받으며,   
요청(Request)은 클라이언트가 요청하는 내용을,   
응답(Response)은 서버가 클라이언트의 요청에 대한 처리 결과를 담은 메시지라고 할 수 있다.   
> ❗ Hyper Text란 HTML, 사진, 동영상, 파일, JSON 등 인터넷에서 주고 받을 수 있는 모든 정보를 의미한다.   

인터넷 초기에는 리소스를 요청하는 GET 메서드만을 지원했으나,   
현재는 다양한 메서드를 사용할 수 있을 뿐만 아니라 HTTP 헤더를 설정하는 등 다양한 동작을 수행할 수 있게 됐다.   
웹 상의 서로 다른 프로그램 사이에서의 통신은 HTTP를 기반으로 이루어지며,   
HTTP 요청의 성격을 구분짓기 위해 사용되는 것이 HTTP Method,   
HTTP 응답의 결과를 구분짓기 위해 사용되는 것이 HTTP Status 코드다.

> HTTP Method ➡ 클라이언트(서버)가 서버에게 요청하는 작업의 종류를 구분하는 것   
> HTTP Status Code ➡ 서버가 클라이언트(서버)의 요청(Request)에 대한 응답 결과를 간략히 표현한 것   
>> End-Point ➡ Url + Method의 조합을 통해 유일하게 구별될 수 있는 주소값

---
<br>

## 1. HTTP 메서드의 종류

HTTP 메서드 중에서 중요하고 사용 빈도가 높은 메서드는 다음과 같다.

### 1.1 ★ GET(READ)

리소스를 조회하는 데에 사용되며, 서버에 전달할 데이터는 query string을 활용한다.   
카테고리별 상품 조회, 페이지, 검색어 등 주로 필터링을 위해 쿼리문을 이용한다.   
❗ GET 요청에도 Body에 데이터를 담을 수 있지만 권장하지 않는 방식이다.

### 1.2 ★ POST(CREATE)

Request Body를 통해 전달한 데이터에 대한 처리를 요청할 때 사용한다.   
대부분 새로운 리소스를 등록하는 데 사용되며 로그인, 결제 등 새로운 리소스를 생성하지 않는 경우도 있다.   
1. 새로운 리소스 생성 요청 ➡ 게시글, 댓글, 회원가입 등   
2. 전달한 데이터를 기반으로 특정 동작 수행 ➡ 로그인 등   
3. 한정된 Method로 인해 처리하기 어려운 동작 ➡ 주문 상태 변경(주문 취소, 주문 확인 중, 상품 준비 중 등등)   
❗ Body에 데이터를 담지 않는다면 POST를 쓸 지에 대해 한 번 더 고민해야 한다.   

### 1.3 ★ PUT(UPDATE)

PUT은 POST와 달리 클라이언트가 리소스의 위치를 사전에 알고 있는 상태에서 요청한다는 것이 가장 큰 차이점이다.   
PUT의 본질적인 쓰임은 1) 리소스가 있으면 **완전히** 대체 2) 리소스가 없으면 생성(like POST)하는 것인데,   
리소스의 일부분만 수정하더라도 PUT 메서드를 사용하는 게 사실상 표준(?)으로 자리잡은 것 같다.   
PUT과 비슷하지만 쓰임이 조금 다른 PATCH는 후술한다.

### 1.4 ★ DELETE(DELETE)

리소스를 삭제시키는 요청을 할 때 사용되는 메서드다.   
GET과 마찬가지로 Body에 데이터를 담지 않고, Url에 정보를 담도록 하자(Params)

### 1.5 PATCH(+α)

PUT과 달리 리소스의 일정 부분만 변경할 때 사용되도록 설계된 것이 바로 PATCH(덧붙이다) 메서드다.   
이는 HTTP에서 정한 '약속'일 뿐이므로, 큰 공감대가 형성되지 않는 한 일반적으로 사용되는 PUT을 쓰는 편이 나을 것.   
다만, 앞선 4가지 메서드로 충분히 구현이 힘든 API가 있다면 PATCH를 적극적으로 활용하자.   
EX) Soft Delete / 공개 ↔ 비공개 토글 / 상태 변경

### 1.6 OPTIONS(Pre-fligth)

웹 브라우저는 Cross-Origin 요청을 보내기에 앞서 요청 가능한 메서드 등을 확인(통신 옵션 확인)하기 위해   
'Pre-flight'라는 요청을 보내는데, 이때 활용되는 것이 OPTIONS 메서드다.   
Pre-flight는 웹 브라우저가 보안을 위해 보내는 요청으로,   
'CORS'와 관련된 이슈이므로 추가로 공부해 보도록 하자.

### 1.7 HEAD(No Body)
유사 GET 요청으로, 유일한 차이점은 응답에 Body를 포함하지 않는다는 것이다.   
일반적인 GET 요청과 동일한 헤더를 응답받기 때문에,   
1) 서버 상태 확인(Ping)   
2) 응답 헤더의 'Content-Length' 확인 목적으로 사용할 수 있다.   

![GET versus HEAD](/assets/http-method/getvshead.png)   

---
<br>

## 2. Method의 속성

### 2.1 안전성(Safe)
요청의 대상이 되는 리소스를 변경하지 않는다는 것을 의미한다.   
달리 말하자면, **어떠한 Side Effects(부수 효과)도 일으키지 않는다.**

### 2.2 멱등성(Idempotent)
동일한 요청에 대해서는 동일한 결과를 반환한다는 것을 의미한다.   
이 때 요청 자체가 아닌 외부적인 요인에 의해 결괏값이 달라지는 것은 고려하지 않는다.
> Idempotent한 것   
>> f(f(x)) == f(x), 1 + 1, 구글 Home 화면 GET 요청   

> Idempotent하지 않은 것   
>> f(f(x)) != f(x), x + 1, 회원가입 요청(성공 -> ID 중복으로 인한 실패), 결제(내가 시킨 치킨이 두 번 결제 된다면,,,)

### 2.3 캐시 가능성(Cacheable)
응답의 결과를 캐시할 수 있는 지를 결정하는 속성이다.   
HTML, CSS, JS와 같은 정적 파일에 대한 GET 요청은 캐시할 수 있지만,   
서버에서 동적으로 처리해야 하는 요청은 캐시를 활용하기 어렵다.(가능은 하다,,,)

![주요 HTTP 메서드들의 속성들](/assets/http-method/http-properties.png)   

---
<br>

## 3. RESTful API 예시
![RESTful API 설계 예시](/assets/http-method/restful-api-example.png)   

---

## 4. Summary

HTTP 메서드는 클라이언트가 서버에게 보내는 요청의 성격을 구분짓는 역할을 한다.   
HTTP 메서드는 Control URI(ex /api/users/create, delete 등)를 최소화하고,   
RESTful API를 설계하는 데에 있어서도 필수적인 요소다.   
하지만 Convention, Protocol이라는 것이 늘 그렇듯   
규칙을 완벽히 준수하는 것보다 통일성을 지키는 것이 더 중요하다.

> 추천 자료
>> MDN HTTP Methods: https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods  