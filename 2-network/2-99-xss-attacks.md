# XSS(Cross Site Scripting) Attacks(작성 중)

## < 목표 >
### 1. XSS 취약점에 대해 설명할 수 있다.
### 2. XSS 취약점에 대한 방어수단에 대해 설명할 수 있다.   
---

## 1. XSS(Cross-Site Scripting)
XSS는 대표적인 웹 보안 취약점 중 하나로,   
악의적인 사용자가 공격하려는 사이트에 악성 스크립트를 주입하는 것을 의미한다.   
XSS를 통해 다른 페이지로 리다이렉트시키거나, 쿠키 등을 탈취하여 세션 하이재킹 공격을 할 수도 있다.   
대표적인 공격 방식으로는
1. Reflected XSS: 쿼리 스트링을 사용할 때 발생하는 취약점을 이용한 공격 기법
2. Stored XSS: 악성 스크립트를 서버에 저장한 후 서비스를 제공하는 정상 페이지에 노출시키도록 하는 공격 기법
3. DOM XSS: HTML 태그의 이벤트 속성(onclick 등)에 스크립트를 주입하여 실행시키는 공격 기법
등이 있다.

## 2. 트위터 XSS 취약점 공격 사례
트위터에서 운영하던 소셜 미디어 어플리케이션인 트윗덱에 로그인할 경우,   
자동으로 리트윗과 Alert을 띄우는 XSS 취약점 공격이 있었다.
> < 2014년 Twitter XSS 취약점 공격 >
>>![트위터 사례](/assets/xss/twitter.jpg)   

## 3. XSS 방어를 위해서는...
1. innerHTML의 사용을 최대한 자제한다.
2. 쿠키 설정 시 'HttpOnly' 옵션을 활성화한다.
3. 응답 헤더의 'Content-Security-Policy'를 설정한다.
4. LocalStorage에는 세션 ID와 같은 민감한 정보를 저장하지 않는다.
5. XSS에 사용되는 특수문자를 치환하여 저장한다.
와 같은 가이드 라인이 있지만 보안 전문가가 아닌 이상,   
DOMPurify, Helmet 같은 라이브러리 등을 활용하는 편이 낫다.

---

## Summary
전체적인 내용 요약보다는 프로세스와 스레드를 비교하고 마치려고 한다.   
**프로세스는 운영체제로부터 자원을 할당받아 PCB를 통해 관리되는 "작업 단위"이고,**   
**스레드는 프로세스가 할당받은 자원을 이용하여 CPU에 의해 처리되는 "실행 단위"이다.**   
프로세스는 스레드 없이는 아무런 동작을 할 수 없고,   
스레드는 프로세스 없이는 생성될 수 없기에 둘은 불가분의 관계라고 볼 수 있다.   
프로세스는 실행 과정에서 1) 프로세서, 2) 주소 공간, 3) 메모리 등의 자원을 할당받아야 한다.   
따라서 여러 스레드로 나누는 것이 시스템 자원을 보다 효율적으로 관리할 수 있는 방법이다.   
뿐만 아니라 프로세스 간의 통신은 IPC(Inter-Process Communication)를 통해 이루어지는데   
이보다는 서로 자원을 공유하는 스레드를 활용하는 것이 여러 작업들 간의 통신 부담을 줄일 수 있다.   
멀티 스레딩은 나름의 장점이 있긴 하지만,   
자원 공유로 인한 동기화 문제에 더 많은 노력이 요구되며   
한 스레드의 장애로 인해 전체 스레드가 영향을 받을 수 있다는 이슈도 존재한다.

---

> 참고 자료
>> [Youtube] Hussein Nasser: https://www.youtube.com/watch?v=pD6C1-zSxIM   
>> [Youtube] PwnFunction: https://www.youtube.com/watch?v=EoaDgUgS6QA 

> 추가로 공부하면 좋을 주제들
>> Scheduling Algorithms   
>> Synchronous vs Asynchronous   
>> Blocking vs Non-blocking   
>> Critical Section
