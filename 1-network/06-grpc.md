# gRPC(gRPC Remote Procedure Call)
- 구글 내부에서 Micro Service들 간 통신을 위해 사용하던 Stubby를 오픈 소스화한 통신 프로토콜
- http/2를 기반으로 작동
- Protobuf compiler(protoc) 외 다양한 플러그인을 통해 어플리케이션 개발에 필요한 클래스를 자동으로 생성할 수 있음
- RPC 프로토콜 중 가장 널리 사용되며, 통신 성능이 비교적 떨어지는 모바일 앱, 복잡하고 통신이 빈번한 MSA 등에 특히 적합

## 1. RPC
- 특정 프로세스에서 다른 프로세스의 함수를 실행하는 Local Call에서 발전해 다른 컴퓨터(서버 등)의 함수를 실행하여 원하는 결과를 얻는 것
  - gRPC, CAP'T PROTO, tRPC 등 다양한 RPC 프로토콜이 존재

## 2. gRPC 장점
### 1) Ecosystem: 다양한 언어와 프레임워크에서 손쉽게 사용 가능
### 2) High Performance - 일반적으로 JSON 대비 5~7배 정도 높은 성능
### 3) Language & Platform Agnostic: 특정 언어와 플랫폼에 종속되지 않음

## 3. Protocol Buffers
- 언어/플랫폼 중립적으로 어떤 데이터를 주고 받을 지 정의하는 일종의 문서
- 정적 타이핑, 구조화된 데이터
- binary encoding format 기반으로 JSON 대비 직렬화/역직렬화 및 전송 속도 개선
- http/2 기반으로 작동하여 1) 멀티플렉싱 2) Server Push 등 다양한 이점 제공
- RPC의 핵심 개념인 Stub은 Protocol Buffer를 기반으로 Marshalling/Unmarshalling을 진행

## 4. gRPC Request & Response
### 1) Request
### 2) Response
- gRPC 응답은 1) 응답헤더 2) length Prefixed Message(Data) 3) Trailer로 구성
- gRPC status code가 존재하며 Application / Server에서 핸들링해야 할 status들이 기존 HTTP Status Code 대비 잘 분리
