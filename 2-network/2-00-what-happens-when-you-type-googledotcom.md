# 브라우저에 google.com을 치면 일어나는 일(작성 중)

브라우저에 google.com을 치고 엔터를 쳤을 때 일어나는 일을 개략적으로 살펴보자.   
최대한 high-level단에 맞춰 간략히 정리하려고 했으며,   
추가로 공부하길 추천하는 제주들은 별도로 정리 정리하였다.   
여기서는 브라우저 검색창에 'google.com'을 문자열 그대로 입력하고 엔터를 친 상황을 기준으로 기술한다. 

---

## 1. URL Parsing
엔터를 치는 순간, 브라우저는 검색창의 문자열을 분석하는 것을 멈추고 입력값이 URL인지, 검색어인지를 결정한다.   
만약 검색어가 아니라면, 브라우저는 Google 페이지에 접속하기 위한 작업을 진행하게 된다.   

## 2. HTTP(port 80)? HTTPS(port 443)?
URL 파싱이 끝난 후 브라우저가 가장 먼저하는 일은 어떤 프로토콜을 이용하여 GET Request를 보낼 지 결정하는 것이다.   
브라우저는 HSTS(HTTP Strict Transport Security)에서 도메인을 검색하고   
검색 결과에 따라 어떤 프로토콜을 통해 요청을 보낼 지 결정한다.
HSTS에서 검색되지 않는다면 Default로 HTTP 프로토콜을 사용하게 된다.
> 인위적으로 HTTP를 통해 요청할 경우
>>![HTTP 요청에 대한 응답](/assets/what-happens/2-http-request-response.png)

## 3. DNS(Domain Name System) Lookup
앞선 과정들을 통해 브라우저는 도메인명, 프로토콜, port 번호를 결정했으므로   
google.com의 웹 서버에 요청을 보내기 위해 IP 주소를 알아내야 한다.   
가장 먼저 브라우저는 자신의 캐시 스토리지를 확인하고,   
만약 없다면 운영체제에 확인을 요청한다.   
만약 운영체제에서도 IP 주소를 가지고 있지 않다면,   
DNS 서버에 요청을 보내기 위해 라우터에 DNS Lookup 요청을 보내게 된다.   
현대의 라우터는 자체적으로 DNS 서버의 기능을 하므로, 자신의 라우트 테이블을 검색해보고   
그래도 없다면 DNS 서버에, DNS 서버에도 없다면 ISP(Internet Service Provider)에 요청해 IP 주소를 응답으로 보내준다.   
(그래도 없다면 재귀적인 탐색을 통해 IP 주소를 얻을 때까지 DNS 서버 리스트에 요청한다.)

## 4. TCP Connection
브라우저는 이제 도메인에 해당하는 IP 주소를 바탕으로 TCP 커넥션을 맺기 위해 3-way handshake를 진행한다.
TCP Connection은
1. TCP/IP 5 Layer(Application -> Physical)
2. 3-way handshake
3. Routing
에 대한 이해가 필수적이지만 각각의 양이 방대하고 중요성이 큰만큼 따로 살펴보기로,,,


## 5. TLS(Transport Layer Security)
TCP 커넥션이 맺어지면 클라이언트와 서버는 안전한 통신을 위해
1. 지원 가능한 암호화 알고리즘 교환
2. 키 교환, 인증
3. 대칭키 암호화 및 메시지 인증
이라는 3단계의 TLS handshake가 추가로 진행된다.(TLS v1.3 기준)
이 과정에서 어떤 버전의 HTTP을 사용할 지, 어떤 압축 방식을 사용할 지에 대한 합의도 이루어진다.

## 6. First GET Request
TLS handshake까지 완료되면 클라이언트는 서버에 첫 GET Request를 보내게 된다.
Google 서버에서는 해당 요청에 대한 응답으로 웹페이지를 렌더링하기 위한 자원들을 보내게 되고,
해당 자원들이 도착함에 따라 브라우저에서는 HTML Parsing을 진행한다.

## 7. HTML Parsing & Rendering
브라우저는 HTML 파일을 읽어들인 후 렌더링에 필요한 CSS, JS, image와 같은 HTML 외 요소에 대한 추가 요청을 진행한다.
첫 번째 GET Request와는 달리, HTTP/2부터 지원하는 Multiple TCP Connection을 통해 한 번에 여러 요청을 보낼 수도 있다. 

## 8. Summary

브라우저에 'google.com'을 입력하고 엔터를 치는 순간부터 웹페이지를 렌더링하는 과정은 크게 7가지로 나눌 수 있다.

1. URL Parsing
2. 프로토콜 결정
3. DNS Lookup(도메인 -> IP 주소)
4. TCP Connection(3-way handshake)
5. TLS(Transport Layer Security)
6. First Get Request
7. HTML Parsing -> Rendering

---

> 참고 자료
>> Hussein Nasser's youtube: https://www.youtube.com/watch?v=dh406O2v_1c&t=57s    
: Video "What happens when you type google.com into your browser and press enter? (Detailed Analysis)"   

> 더 읽어보면 좋을 자료
>> alex's github: https://github.com/alex/what-happens-when   
: 한국어 version: https://github.com/SantonyChoi/what-happens-when-KR   
❗ 해당 문서에서는 TLS handshake를 1.2 버전 기준으로 기술하고 있음을 참고

> 추가로 공부하면 좋을 주제들
>> HTTP vs HTTPS(HyperText Transfer Protocol Secure socket layer)   
>> OSI 7 Layer vs TCP/IP 5 Layer
>> 3-way handshake & 4-way handshake   
>> TCP vs UDP   
>> GET vs POST Method   
>> HTML Rendering   