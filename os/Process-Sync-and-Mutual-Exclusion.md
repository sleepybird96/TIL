### Reference

[Lecture 6. Process Synchronization and Mutual Exclusion (1/7) - Introduction / 운영체제 강의](https://youtu.be/wdaf2gy83uU)

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
