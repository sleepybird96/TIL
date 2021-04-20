### Reference

[Lecture 6. Process Synchronization and Mutual Exclusion - Introduction / 운영체제 강의](https://youtu.be/wdaf2gy83uU)

# 프로세스 동기화 & 상호배제

## Process Synchronization(동기화)

**다중 프로그래밍 시스템**

- 여러 개의 프로세스들이 존재
- 프로세스들은 서로 독립적으로 동작
- 공유자원 또는 데이터가 있을 때, 문제 발생 가능

**동기화(Synchronization)**

- 프로세스 들이 서로 동작을 맞추는 것
- 프로세스 들이 서로 정보를 공유 하는 것

## Asynchronous and Concurrent P's

- 비동기적(Asynchronous)
  - 프로세스들이 서로에 대해 모름
- 병행적(Concurrent)
  - 여러 개의 프로세스 들이 동시에 시스템에 존재

병행 수행중인 비동기적 프로세스들이 공유 자원에 동시 접근 할 때 문제가 발생할 수 있다.

### 용어 정리

**Shared data(공유 데이터)**

- 여러 프로세스 들이 공유하는 데이터

**Critical section(임계 영역)**

- 공유 데이터를 접근하는 코드 영역

**Mutual exclusion(상호배제)**

- 둘 이상의 프로세스가 동시에 critical section에 접근하는것을 막음

## Mutual Exclusion Methods

**Mutual exclusion primitives**

- **enterCS()** primitive
  - Critical section 진입 전 검사
  - 다른 프로세스가 critical section 안에 있는지 검사
- **exitCS()** primitive
  - Critical section을 벗어날 때의 후처리 과정
  - Critical section을 벗어남을 시스템이 알림

<a href="https://imgur.com/xYNe3I7"><img src="https://i.imgur.com/xYNe3I7.png" title="source: imgur.com" /></a>

안에 누가 있는지 **진입전 검사**하는것을 enterCS()작업이라고 한다.  
작업이 끝나고 섹션을 벗어났음을 알리는것을 exitCS()작업이라고 한다.

### Requirements for ME primitives

**Mutual exclusion (상호배제)**

- Critical section(CS) 에 프로세스가 있으면, 다른 프로세스의 진입을 금지

**Progress (진행)**

- CS안에 있는 프로세스 외에는, 다른 프로세스가 CS에 진입하는것을 방해하면 안됨

**Bounded waiting (한정대기)**

- 프로세스의 CS진입은 유한시간 내에 허용되어야 함

### Software solution

**Dekker's Algorithm**

<a href="https://imgur.com/aVisWl9"><img src="https://i.imgur.com/aVisWl9.png" title="source: imgur.com" /></a>

Two process ME을 보장하는 최초의 알고리즘이다.  
상호간의 플래그와, 순서를 함께 기록해서 상대의 플래그가 세워있는지 판별하고,  
자신의 순서인지 판별하여 ME를 지킨다.

**Dijkstra's Algorithm**

<a href="https://imgur.com/JJ1jzci"><img src="https://i.imgur.com/JJ1jzci.png" title="source: imgur.com" /></a>

똑같이 플래그와 순서를 기록하지만, 2개보다 많은 n개의 프로세스를  
me처리 할려고 할때, 1단계와 2단계로 나누는 알고리즘이다.  
**1단계**는 **want-in**단계에서 들어가고싶다고 의사를 밝힌다. (플래그를 올린다)  
순서가 자신의 순서가 아니면, 기다린다.  
순서가 다가와서 자신의 턴을 뺏는다면 while문 안으로 접근한다.(2단계 접근)  
**2단계**는 inCS에 자신이외에 아무것도 없을 때 까지 처리한다.(즉 자신 이외에 접근한면 빠져나옴)

</br>

**SW solution들의 문제점**

- 속도가 느림
- 구현이 복잡함
- ME primitive 실행 중 preemption 될 수 있다
- Busy waiting(비효율적)

### Hardware Solution

**TestAndSet instruction**

- Test와 Set을 한번에 수행하는 기계어
- Machine instruction
  - 실행 중 interrupt를 받지 않음 (preemption 되지않음)

<a href="https://imgur.com/FyfGkrl"><img src="https://i.imgur.com/FyfGkrl.png" title="source: imgur.com" /></a>

위 그림을 보면 lock이라는 변수를 만들어 초기값을 false로 만들어준다.  
false니 while을 벗어나 CS에 접근한다.  
CS에접근한 프로세스가 lock을 true로 바꿨기에 다른 프로세스는 while문에 잠긴다.  
CS에 접근한 프로세스가 CS를 벗어나 lock을 false로 바꾸면 다른 프로세스가 접근한다.

다만 **3개 이상의 프로세스의 경우, Bounded waiting 조건에 위배**된다.

### OS supported SW solution

**Spinlock**

- **정수형 변수 (S)(초기화, P(), V() 연산으로만 접근 가능한 변수)**를 OS가 보장해준다.
- 전체가 한 instruction cycle에 수행된다.

<a href="https://imgur.com/33EZGqG"><img src="https://i.imgur.com/33EZGqG.png" title="source: imgur.com" /></a>

프로세스가 들어가기전에 P연산, 들어갔다 나와서는 V연산을 한다.

</br>

**Semaphore**

- Dijkstra가 제안(이쯤되면 갓이다..)
- Busy waiting 문제 해결
- 음이 아닌 정수형 변수(S)
  - 초기화 연산 P() V()
- **임의의 S 변수 하나에 ready queue하나가 할당 됨**

- **Semaphore로 해결 가능한 동기화 문제들**

  - 상호배제 문제
  - 프로세스 동기화 문제
  - 생산자-소비자 문제
  - Reader-writer 문제
  - Dining philosopher problem
  - 기타

<a href="https://imgur.com/VR1qtc0"><img src="https://i.imgur.com/VR1qtc0.png" title="source: imgur.com" /></a>

spinlock과의 차이점은 readyQueue를 사용해서 활동을 마친 프로세스가  
대기중인 프로세스를 깨워준다.

</br>

**Eventcount/Sequencer**

- 은행의 번호표와 비슷한 개념
- Sequencer
  - 정수형 변수
  - 생성시 0으로 초기화, 감소하지 않음
  - 발생 사건들의 순서 유지
  - ticket() 연산으로만 접근가능
- ticket(S)
  - 현재까지 ticket() 연산이 호출 된 횟수를 반환
  - Indivisible operation
- Eventcount
  - 정수형 변수
  - 생성시 0으로 초기화, 감소하지 않음
  - 특정 사건의 발생 횟수를 기록
  - 특정 연산으로만 접근 가능
- read(E)
  - 현재 Eventcount 값 반환
- advance(E)
  - E++
  - E를 기다리고 있는 프로세스를 깨움 (wake-up)
- await(E, v)
  - V는 정수형 변수
  - if (E < v) 이면 E에 연결된 Qe에 프로세스 전달(push) 및 CPU스케쥴러 호출
- Mutual exclusion  
  <a href="https://imgur.com/UByJVvG"><img src="https://i.imgur.com/UByJVvG.png" title="source: imgur.com" /></a>

### Language-Level solution

**Monitor**

- 공유 데이터와 Critical section의 집합
- Conditional variable
  - wait(), signal() operations
- **구조**
  - Entry queue(진입큐)
    - 모니터 내의 절차 수 만큼 존재
  - Mutual exclusion
    - 모니터 내에는 항상 하나의 프로세스만 진입가능
  - Information hiding(정보 은폐)
    - 공유 데이터는 모니터 내의 프로세스만 접근 가능
  - Condition queue(조건 큐)
    - 모니터 내의 특정 이벤트를 기다리는 프로세스가 대기
  - Signaler queue(신호제공자 큐)
    - 모니터에 항상 하나의 신호제공자 큐가 존재
    - signal() 명령을 실행한 프로세스가 임시대기

**장점**

- 사용이 쉽다
- Deadlock등 error발생 가능성이 낮다.

**단점**

- 지원하는 언어에서만 사용가능
- 컴파일러가 OS를 이해하고 있어야함
