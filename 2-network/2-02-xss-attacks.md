# XSS(Cross Site Scripting) Attacks

## < 목표 >
### 1. XSS 취약점에 대해 설명할 수 있다.
### 2. XSS 취약점에 대한 방어수단에 대해 설명할 수 있다.   
---

XSS 취약점은 10대 웹 애플리케이션 보안 취약점 목록에 포함되어 있을 정도로 발생 빈도가 높다.   
웹 초창기부터 점점 고도화되어, 아직까지도 완벽한 보안이 불가능한 XSS에 대해 알아보자.

## 1. XSS(Cross-Site Scripting)
XSS는 대표적인 웹 보안 취약점 중 하나로,   
악의적인 사용자가 공격하려는 사이트에 악성 스크립트를 주입하는 것을 의미한다.   
XSS를 통해 다른 페이지로 리다이렉트시키거나, 쿠키 등을 탈취하여 세션 하이재킹 공격을 할 수도 있다.   
대표적인 공격 방식으로는
1. Reflected XSS: 쿼리 스트링을 사용할 때 발생하는 취약점을 이용한 공격 기법
> https://example.com/search?term=\<script>alert('이 사이트는 보안이 취약하네요^^')\</script>
2. Stored XSS: 악성 스크립트를 서버에 저장한 후 서비스를 제공하는 정상 페이지에 노출시키도록 하는 공격 기법
> < Stored XSS 예시 >
>>![Stored XSS 예시](/assets/xss/stored-xss.png)   
3. DOM XSS: HTML 태그의 이벤트 속성(onclick 등)에 스크립트를 주입하여 실행시키는 공격 기법
> \<h1 onload="alert('대충 쿠키를 전송하는 코드')>당신의 쿠키는 내가 가져간다.\</h1>
등이 있다.

## 2. 트위터 XSS 취약점 공격 사례
트위터에서 운영하던 소셜 미디어 어플리케이션인 트윗덱에 로그인할 경우,   
자동으로 리트윗과 Alert을 띄우는 XSS 취약점 공격이 있었다.
> < 2014년 Twitter XSS 취약점 공격 >
>>![트위터 사례](/assets/xss/twitter.jpg)   

## 3. XSS 방어를 위해서는...
1. innerHTML의 사용을 최대한 자제한다.
➡ XSS 코드가 실행되는 것을 방지할 수 있다.
2. 쿠키 설정 시 'HttpOnly' 옵션을 활성화한다.
➡ 브라우저에서 쿠키에 접근할 수 없기에 탈취도 불가능하다.
3. 응답 헤더의 'Content-Security-Policy'를 설정한다.
➡ 외부로부터 주입된 악성 스크립트의 실행을 막을 수 있다.
4. LocalStorage에는 세션 ID와 같은 민감한 정보를 저장하지 않는다.
➡ LocalStroage는 쿠키에 비해 보안에 취약하다!
5. XSS에 사용되는 특수문자를 치환하여 저장한다.   
와 같은 가이드 라인이 있지만 보안 전문가가 아닌 이상,   
다양한 보안 관련 라이브러리를 활용해 최대한 많은 안전장치를 마련하는 편이 낫다.   
보안에는 끝이 없기에,,,

---

## Summary
XSS 취약점 공격은 가장 널리 알려진 보안 문제로 원리는 간단하지만   
공격기법이 점차 다양해지며 아직까지도 완전한 방어가 어려운 공격 기법이다.   
가장 대표적인 공격 기법으로 1) Reflected XSS 2) Stored XSS 3) DOM XSS이 있으며,   
이를 예방하기 위해서는 사용자로부터의 입력을 그대로 출력하는 것에 주의해야 한다.

---

> 참고 자료
>> [Blog] NordVPN: https://nordvpn.com/ko/blog/xss-attack/      
>> [Youtube] PwnFunction: https://www.youtube.com/watch?v=EoaDgUgS6QA 

> 추가로 공부하면 좋을 주제들
>> CSRF(Cross-Site Request Forgery)
