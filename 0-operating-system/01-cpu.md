# CPU(Central Processing Unit)

## CPU의 구조

### 1. ALU(Arithmetic Logic Unit): 연산을 담당

### 2. 제어장치: 제어 신호를 발생시키고 명령어를 해석

### 3. 레지스터: CPU 내부의 작은 임시저장장치
- 프로그램의 명령어와 데이터가 실행 전후로 저장되는 장치
- CPU 내부에는 다양한 레지스터들이 있고, 각기 다른 역할을 가짐
  - 프로그램 카운터: 메모리에서 가져올 명령어의 주소를 저장
  - 명령어 레지스터: 해석할 명령어를 저장(제어장치가 해석)
  - 메모리 주소 레지스터: 메모리의 주소를 저장
  - 메모리 버퍼 레지스터: 메모리와 주고받을 값을 저장
  - 플래그 레지스터: 연산 결과 또는 CPU 상태에 대한 부가적인 정보
  - 범용 레지스터: 다양한 상황에서 자유롭게 사용
  - 스택 포인터: 스택의 최상단의 주소를 저장
  - 베이스 레지스터: 변위 주소 지정 방식에 사용되며 기준 주소를 저장
    - 프로그램의 가장 작은 물리 주소(프로그램의 첫 물리 주소)를 저장

## Core & Thread
### 1. Core
- 현대의 CPU에는 '명령어를 실행하는 부품'이 여러 개 존재
- '명령어를 실행하는 부품'이 Core
- 여러 개의 코어를 포함하고 있는 CPU가 멀티코어 프로세서
> [!NOTE]
> CPU의 성능이 코어 수에 비례하여 높아지는 것은 아님

### 2. Thread
- 실행 흐름의 단위
- 하드웨어 스레드: 하나의 코어가 동시에 처리하는 명령어 단위
  - 멀티 스레드 CPU(프로세서): 하나의 코어가 여러 개의 스레드를 가짐
  - 논리 프로세서라고도 지칭
- 소프트웨어 스레드: 하나의 프로그램에서 독립적으로 실행되는 단위
> [!NOTE]
> 하나의 코어만으로도 여러 개의 소프트웨어 스레드를 구현할 수 있다

## 명령어 병렬 처리
### 1. 명령어 파이프라이닝
### 2. 비순차적 명령어 처리

## 명령어 집합
- CPU가 이해할 수 있는 명령어들의 모음 -> CPU의 언어
### CISC(Complex Instruction Set Computer)
- 복잡하고 다양한 명령어를 활용
- 가변 길이 명령어를 활용
- 상대적으로 적은 수의 명령어로도 프로그램을 실행 가능
- 명령어 파이프라이닝에 불리함(여러 클럭 주기가 필요)
### RISC(Reduced Instruction Set Computer)
- 명령어의 종류가 적고, 짧고 규격화된 명령어를 사용
- 고정 길이 명령어를 활용
- 메모리 접근 최소화(load, store), 레지스터를 적극적으로 활용
- 명령어 파이프라이닝에 유리하나, 컴파일 시 명령어의 수가 더 많아짐

