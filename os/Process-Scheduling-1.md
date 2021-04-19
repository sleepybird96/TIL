### Reference

[Lecture 5. Process Scheduling / 운영체제 강의](https://youtu.be/_gNeoGQx-Tc)

# 프로세스 스케쥴링

프로세스 스케쥴링은 왜해야 하는가?  
우리가 사용하는 시스템은 **다중프로그래밍**이다.  
여러개의 프로세스가 시스템 내 존재하고, 자원을 할당할 프로세스를 선택 해야 한다.  
이러한 할당할 프로세스를 선택하는것을 스케줄링이라고 한다.  
이러한 자원관리에는 두가지 관리방법이 존재한다.

- 시간분할 관리
  - 하나의 자원을 여러 스레드들이 번갈아 가며 사용
  - ex)프로세서(Processor)
  - 프로세스 스케줄링
- 공간 분할 관리
  - 하나의 자원을 분할하여 동시에 사용
  - ex) 메모리

## 스케줄링의 목적

- **시스템의 성능(performance)향상**
- **대표적 시스템 성능 지표(index)**
  - **응답시간** 작업요청으로부터 응답을 받을 때 까지의 시간
  - **작업 처리량** 단위 시간 동안 완료된 작업의 수
  - **자원 활용도** 주어진 시간(Tc) 동안 자원이 활용된 시간(Tr)

**목적**에 맞는 지표를 고려하여 스케줄링 기법을 선택해야 한다.

## 스케줄링 기준

스케줄링의 **기준**이란 스케줄링 기법이 고려하는 **항목**들이다.

### CPU burst vs I/O burst

**프로세스 수행 = cpu사용(연산) + I/O 대기**  
프로그램에 따라 CPU를 많이쓰냐(연산을 많이하냐) I/O를 더 많이하냐로 나뉠 수 있다.  
어디에 더 시간을 많이 쓰느냐는 (CPU burst냐 I/O burst냐) 스케쥴링의 중요한 기준이다

## 스케줄링의 단계

발생하는 빈도 및 할당 자원에 따라 구분한다.

### Long-term Scheduling

긴 시간에 한번씩 일어나는 스케줄링이다.  
**Job scheduling**도 이에 속하는데 시스템에 제출할 작업을 결정한다.  
당연히 그 발생 빈도는 적다.

- 다중프로그래밍 정도(degree)조절
  - 시스템 내에 프로세스 수 조절
- I/O-bounded 와 compute-bounded 프로세스들을** 잘섞어서** 선택해야한다.
  - 우리 컴퓨터에는 cpu와 I/O장치들이 적절히 있는데, 하나에 치중해 있으면,  
    나머지 하나의 리소스는 방치되기 때문. (비효율적)
- 시분할 시스템에서는 **모든 작업을** 시스템에 등록 (Long-term스케줄링이 **덜 중요**)
  - 시간을 나눠서 사용하기때문에 모든 작업을 등록하더라도 스케줄링의 필요성이 떨어진다.

### Mid-term Scheduling

**메모리 할당**과 관련이 있다.  
<a href="https://imgur.com/acT8haj"><img src="https://i.imgur.com/acT8haj.png" title="source: imgur.com" /></a>

위와 같이 suspended ready에서 누구에게 메모리를 할당해 줄지 결정하는것이 mid-term Scheduling이다.  
job scheduling보다 빈번하게 일어난다.

### Short-term Scheduling

<a href="https://imgur.com/xnkKQMS"><img src="https://i.imgur.com/xnkKQMS.png" title="source: imgur.com" /></a>

위와 같이 ready상태에서 running상태로 올리는 역할이 **가장 자주**일어난다.  
그래서 매우 빨라야 한다.

## 스케줄링 정책 (Policy)

스케줄링에서 정책이란 어떠한 작업을 수행하기 위한 **기준이나 방법**으로 생각하자.  
대표적으로 두가지가 있다.

### 선점 (Preemptive)/ 비선점 (Non-preemptive)

**Non-preemptive**  
할당 받을 자원을 스스로 반납 할 때까지 사용하는것이다.  
컨텍스트 스위치가 적게 일어나는 장점이 있지만, 잦은 우선순위가 역전되고,  
평균 응답시간이 증가된다는 단점이 있다.  
**Preemptive**  
타의에 의해 자원을 빼앗길 수 있다.  
예를 들면 할당시간이 종료되거나 우선순위가 높은 프로세스가 등장하면 자원을 뺏긴다.  
컨텍스트 스위치가 자주일어나는 단점을 가진다. 시분할시스템과, real-time system에 적합하다.

### 우선순위 (Priority)

우선순위를 어떻게 정해주는지에 대한 정책이다.  
**정적(Static) 우선순위**  
프로세스 생성시 결정된 우선순위가 유지된다.  
구현이 쉽고 overhead가 적은 장점을 가지지만,  
시스템 환경변화에 대한 대응이 어렵다.  
**동적(Dynamic) 우선순위**  
프로세스의 상태변화에 따라 우선순위가 변경된다.  
구현이 복잡하고 우선순위를 재계산하는 overhead가 크다는 단점을 가지고있지만,  
시스템 환경변화에 유연한 대응이 가능하다는 장점을 가지고있다.

## 기본 스케줄링 알고리즘들

### FCFS (First-Come-First-Service)

우리나라 말로 쉽게 풀면 선착순 알고리즘이다

- **Non-preemptive scheduling**
- **스케줄링 기준(Citeria)**
  - 도착시간
  - 먼저 도착한 프로세스를 먼저 처리
- **자원을 효율적으로 사용 가능**
  - 스케쥴링에 대한 오버헤드가 적다. 들어오는대로 던져주면되기 때문
- **Batch system에 적합, interactive system에 부적합**
- **단점**
  - Convoy effect
    - 하나의 수행시간이 긴 프로세스에 의해 다른프로세스들이 긴시간을 갖게됨
  - 긴 평균 응답시간

<a href="https://imgur.com/mNGw3fI"><img src="https://i.imgur.com/mNGw3fI.png" title="source: imgur.com" /></a>

위 그림과 같이 각 프로세스가 도착하는대로 프로세서가 처리하고 프로세스들이 나가게된다.

### 라운드 로빈 (RR)

FCFS의 대기시간 대비 TT의 한계를 극복하기위한 방법이다.

- **Preemptive scheduling**
- **스케줄링 기준(Criteria)**
  - **도착 시간**(ready queue기준)
  - 먼저 도착한 프로세스를 먼저 처리
- **자원 사용 제한시간(time quantum)**이 있음
  - 프로세스는 할당된 시간이 지나면 자원 반납
  - 특정 프로세스의 자원 독점(monopoly) 방지
  - Context switch overhead가 큼
- 대화형, 시분할 시스템에 적합

<a href="https://imgur.com/7LuKwNW"><img src="https://i.imgur.com/7LuKwNW.png" title="source: imgur.com" /></a>

위와같이 프로세서가 할당된 시간이 끝나면 나와서 다시 **맨 뒤에** 줄을 선다.

### SPN (Shortest-Process-Next)

Burst time이 작은 프로세스들이, 나는 이 일 끝내고 금방 나갈 수 있는데,  
앞의 Burst time이 큰 프로세스들에 막혀서 빨리 처리를 못하는 한계를 극복하기 위한 방법이다.

- **Non-preemptive scheduling**
- **스케줄링 기준**
  - 실행시간(burst time 기준)
  - burst time 가장 작은 프로세스 순으로 처리  
    ex) 소량 전용 계산대

**장점**

- 평균 대기시간 최소화
- 시스템 내 프로세스 수 최소화
  - 스케줄링 부하 감소, 메모리 절약 -> 시스템 효율 향상
- 많은 프로세스들에게 빠른 응답시간 제공

**단점**

- Starvation(무한대기) 현상 발생
  - BT가 긴 프로세스는 자원을 할당 받지 못 할 수 있음
    - Aging등으로 해결
  - 정확한 실행시간을 알 수 없음
    - 실행시간 예측 기법이 필요

### SRTN (Shortest Remaining Time Next)

- **SPN의 변형**
- **Preemptive scheduling**

**장점**

- SPN의 장점 극대화

**단점**

- 프로세스 생성시, 총 실행시간 예측이 필요함
- 잔여 실행을 계속 추적해야함

구현 및 사용이 비현실적이다.

### HRRN (High-Response-Ratio-Next)

- **SPN의 변형**
  - SPN + Aging concepts, Non-preemptive scheduling
- **Aging concepts**
  - 프로세스의 대기 시간(WT)을 고려하여 기회를 제공
- **스케줄링 기준**
  - Response ratio 가 높은 프로세스 우선
- **Response ratio?**
  - (WT + BT)/ BT
  - 실행 시간 예측 기법 필요(overhead)

### MLQ (Multi-level Queue)

말그대로 여러개의 큐를 두는것이다.

- \*\*작업 (or 우선순위)별 별도의 ready queue를 가짐
  - 최초 배정된 큐를 벗어나지 못함
  - 각각의 큐는 자신만의 스케줄링 기법 사용
- 큐 사이에는 우선순위 기반의 스케줄링 사용

**장점**

- 중요한 애들은 빨리 처리해줄 수 있다.

**단점**

- 여러개의 큐 관리 등 스케줄링 Overhead 발생
- 우선순위가 낮은 큐는 무한대기 현상 발생

### MFQ (Multi-level Feedback Queue)

- **프로세스의 Queue간 이동이 허용된 MLQ**
- **Feedback을 통해 우선순위 조정**
  - 현재까지의 프로세서 사용 정보(패턴) 활용

**특성**

- Dynamic priority
- Preemptive scheduling
- Favor short burst-time processes
- Favor I/O vounded processes
- Imprive adaptability

프로세스에 대한 사전정보 없이 SPN, SRTN, HRRN 기법의 효과를 볼 수 있다.

**단점**

- 설계 및 구현이 복잡하다, 스케줄링 Overhead가 크다
- starvation 문제

**변형**

- 각 준비 큐마다 시간 할당량을 다르게 배정
  - 프로세스의 특성에 맞는 형태로 시스템 운영 가능
- 입출력 위주 프로세스들을 상위 단계의 큐로 이동, 우선 순위 높임
  - 프로세스가 block될 때 상위의 준비 큐로 진입하게 함
  - 시스템 전체의 평균 응답 시간 줄임, 입출력 작업 분산 시킴
- 대기 시간이 지정된 시간을 초과한 프로세스들을 상위 큐로 이동
  - 에이징(aging)기법
