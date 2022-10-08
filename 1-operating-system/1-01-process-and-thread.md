# Process & Thread(작성 중)   
## < 목표 >
### 1. 프로세스와 스레드에 대해 설명할 수 있다.   
### 2. 프로세스와 스레드의 차이점에 대해 설명할 수 있다.
---
운영체제에 있어 가장 중요한 주제 중 하나인 프로세스와 스레드에 대해 살펴보자.   
먼저 프로세스와 스레드가 무엇인지, 이 둘이 어떻게 다른지 살펴보고   
추후에 Processing과 Threading에 대해 추가로 다뤄보고자 한다.   
추가로 공부하면 좋을 주제들은 별도로 정리하였다.   

---

## 1. Process
Process는 '어떤 일 발생해서 완료되기 까지의 과정' 자체를 의미한다.   
여기서 말하는 '어떤 일'은 프로그래밍 언어를 통해 코드로 작성되어 실행 가능한 상태의 프로그램이며,   
이 프로그램이 실행되고 있는 과정을 Process라고 할 수 있다.(Process == a Program in execution)   
최근에는 하나의 프로그램이 여러 Process에 의해 작동되는 경우도 많으므로,   
Process가 실행 중인 Program과 정확히 일치하지 않는다는 것 정도만 알아두자.

### 1.1 Process State
Process가 실행되어 종료될 때까지 Process의 상태는 수시로 변한다.
각각의 Process가 가질 수 있는 상태 목록은 다음과 같다.
- Create: Program이 실행되어 Process 진행을 위해 생성된 상태
- Ready: Process가 스케쥴링에 의해 processor에 할당받길 기다리고 있는 상태
- Running: Program에 정의된 일련의 코드(Instruction)들이 실행되고 있는 상태
- Waiting: Process가 입출력 처리 등 다른 Event가 완료되길 기다리고 있는 상태(Not Ready)
- Terminated: Process의 모든 코드들이 실행되어 종료된 상태

### 1.2 프로세스 제어 블록(Process Control Block)
운영체제는 PCB을 통해 프로세스를 관리한다.
PCB에는
1. 프로세스의 ID(PID) => 특정 프로세스를 식별하는데 사용
2. 프로세스의 상태
3. 프로그램 카운터: 다음 실행 시 실행되어야 할 코드의 주소
4. CPU 스케줄링 관련 정보: 우선순위, 스케줄링 큐의 주소 등
5. 메모리 정보: 프로세스 처리에 필요한 메모리 정보   
6. Accounting Information: 처리 시간, CPU, 메모리 사용량 등
7. I/O 정보: 프로세스 처리에 필요한 입출력 장치에 대한 정보   
등의 정보가 저장되어 있다.

### ✅ Process 관련 용어 정리
1. 멀티 프로그래밍: CPU의 효율을 극대화하기 위해 최대한 많은 시간 동안 프로세스를 처리하는 것
- 초기의 컴퓨터는 작업 도중에 프로세스가 Waiting 상태로 변해도 다른 프로세스를 처리하지 못했다.
- 현대의 컴퓨터는 작업 도중에 프로세스가 Waiting 상태가 되면 기다리지 않고 다음 프로세스를 실행한다.
- 하나의 CPU만으로도 멀티 프로그래밍을 구현할 수 있다. 

2. 시분할 시스템(Time Sharing System)
- 각 프로세서는 한번에 하나의 프로세스만을 처리할 수 있다.
- 타임 퀀텀(Time Quantum)을 정해놓고 사람이 인식하지 못할 정도의 속도로   
여러 프로세스를 번걸아 가며 처리하는 것을 시분할 시스템이라고 한다.
- 스케줄링 알고리즘 중 라운드 로빈(Round Robin) 방식이 이에 해당하며,
하나의 CPU만으로도 시분할 시스템을 구현할 수 있다.

3. 멀티 프로세싱
- 컴퓨터 처리 능력을 향상시키기 위해 2개 이상의 CPU를 통해 여러 프로세스를 병렬적으로 처리하는 것.
- 2000년대 초반, 단일 CPU의 성능 향상이 한계에 다다르자 본격적으로 도입되기 시작했다.

### 1.3 문맥 전환(Context Switch)
문맥 전환은 특정 프로세스가 실행을 중단하고 다른 프로세스가 실행되는 과정에서 발생한다.
비유적으로 표현하면,
1. 첫 번째 프로세스가 PCB를 들고 CPU를 찾아온다.
2. CPU는 PCB를 읽고 어떤 작업을 할 지 확인하고 일정 시간만큼 작업을 수행한다.
3. 시간이 다 되면 CPU는 다음 작업을 위해 PCB를 업데이트하여 프로세스에게 건네준다.
4. 작업이 덜 끝난 프로세스는 대기줄의 마지막에 줄을 선다.
5. 다음 순서의 프로세스가 자신의 PCB를 들고 CPU를 찾아간다.
6. 2~5번이 반복된다.
문맥 전환 과정에서 CPU는 별다른 Instruction을 수행하지 않으므로,
문맥 전환은 온전한 overhead(간접비)라고 할 수 있다.

---

## 2. Thread
Thread는 '실', '꿰다'의 의미를 가진 것에서 알 수 있듯 한 Process 안에 속한 하나의 '실행 단위'이다.
Process는 단 하나의 Thread만을 가질 수도 있고, 여러 Thread로 이루어질 수도 있다.


---
(수정 예정)

> < 인위적으로 HTTP를 통해 요청할 경우 >
>>![HTTP 요청에 대한 응답](/assets/what-happens/2-http-request-response.png)

---

## 3. DNS(Domain Name System) Lookup
(ISP의 DNS 서버에도 없다면 재귀적인 탐색을 통해 IP 주소를 얻을 때까지 DNS 서버 리스트들을 찾아다니며 요청한다.)
![DNS Lookup의 과정](/assets/what-happens/3-dns-lookup.png)   

> < 브라우저 & 운영체제에 의한 DNS Lookup >
>>![HTTP 요청에 대한 응답](/assets/what-happens/2.2-http-request-response.png)

---

## 4. TCP Connection
은 추후 따로 살펴볼 것.   

> < OSI 7 Layer vs TCP/IP vs TCP/IP Updated >   
>> ![TCP/IP 모델](/assets/what-happens/4.1-osi-tcpip-model.png)   
>> 출처: https://www.computernetworkingnotes.com/ccna-study-guide/similarities-and-differences-between-osi-and-tcp-ip-model.html

---

## 5. TLS(Transport Layer Security)
이 과정에서 어떤 버전의 HTTP을 사용할 지, 어떤 압축 방식을 사용할 지에 대한 합의도 이루어진다.
> < 3-way & TLS handshake >
>> ![3-way & TLS handshake 설명 자료](/assets/what-happens/5-tls-handshake.png)   
>> ![AWS TLS 강조 내용](/assets/what-happens/5.1-tls-handshake.png)   


---


---

> HTTP Daemon 서버란?
>> 서버 사이드에서 들어오는 요청을 처리하고 응답을 전송하는 역할을 하는 서버로 대표적으로 nginx가 이에 해당한다.   
>> HTTP Daemon 서버는 요청 <-> 응답 처리 외에도 로드 밸런싱, HTTP 캐싱 등의 역할을 하기도 한다.
>>> < NGINX Architecture >   
>>>![nginx 설명 자료](/assets/what-happens/7.1-what-is-nginx.png)

---


---

## Summary

브라우저에 'google.com'을 입력하고 엔터를 치는 순간부터 웹페이지를 렌더링하는 과정을 크게 8가지로 나누어 살펴보았다.

> < 개발자 도구 ➡ Network ➡ Resource 선택 ➡ Timing 탭 >
>> ![요약 자료](/assets/what-happens/summary.png)   
1. URL Parsing
2. HTTP(port 80)? HTTPS(port 443)? => 프로토콜을 명시하지 않은 경우!
3. DNS Lookup(도메인 -> IP 주소)
4. TCP Connection(3-way handshake)
5. TLS(Transport Layer Security)
6. Client: First Get Request
7. Server: Handling Request
8. HTML Parsing -> Rendering

공부를 해나가면서 살을 붙이고 단계를 더 세분화해 나간다면 네트워크의 이해 수준을 높이는 데 큰 도움이 될 수 있는 주제라고 생각한다 😊

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
>> OSI 7 Layer vs TCP/IP(+TCP/IP Updated)   
>> 3-way handshake & 4-way handshake   
>> SSL & TLS
>> TCP vs UDP   
>> GET vs POST Method   
>> HTML Rendering   