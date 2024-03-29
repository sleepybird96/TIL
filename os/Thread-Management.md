### Reference

[Lecture 4. Thread management / 운영체제 강의](https://youtu.be/YlnvCIZQDkw)

# 스레드 관리

## 프로세스와 스레드

프로세스가 하는일은 자원을 할당받는다.  
그리고 프로세스는 자원을 제어하는게 역할이다.
이 할당과 제어 두가지역할로 생각할 수 있는데,  
이 **제어**부분만 따로 놓고 봤을 때 이 부분을 스레드라고 한다.

## 스레드

프로세스에는 각종 제어정보와, 지역데이터, 그리고 그 지역데이터를 쌓아놓는 스택이 있다.  
이러한 것들을 제어요소라고 하는데 이 하나의 제어요소를 **스레드**라고 하는데,

<a href="https://imgur.com/XLftUXb"><img src="https://i.imgur.com/XLftUXb.png" title="source: imgur.com" /></a>

스레드를 한 프로세스 안에서 여러개 생성이 가능하다.

<a href="https://imgur.com/LARfQfp"><img src="https://i.imgur.com/LARfQfp.png" title="source: imgur.com" /></a>

같은 프로세스의 스레드들은 동일한 주소공간을 공유한다.

### 특징

- Light Weight Process (LWP)
- 프로세서 활용의 기본단위
- 구성요소
  - Thread ID
  - Register set(PC, SP 등)
  - Stack(local data)(자기만의 작업영역)
- 제어요소 외 코드, 데이터 및 자원들은 프로세스 내 다른스레드들과 공유
- 전통적 프로세스 = 단일 스레드 프로세스

### 싱글스레드 vs 멀티스레드

**싱글스레드**는 자원요소도 **하나** 제어요소도 **하나** 이다.

반면 **멀티스레드**는 자원요소는 **하나**이지만 제어요소는 **여러개**가지고 있다면 멀티스레드 이다.

### 스레드의 장점

- **사용자 응답성**
  - 일부 스레드의 처리가 지연되어도, 다른 스레드는 작업을 계속 처리가능
- **자원공유**
  - 자원을 공유해서 효율성 증가 (커널의 개입을 최소화)
  - ex)여러 스레드가아닌 여러 프로세스가 자원을 사용한다면  
    다른 프로세스가 사용할 때 마다 컨텍스트 스위칭이 일어난다.
- **경제성**
  - 프로세스의 생성, context switch에 비해 효율적
- **멀티 프로세서 활용**
  - 병렬처리를 통해 성능 향상

그렇다면 이러한 스레드는 어떻게 구현되는것일까?  
크게 두가지로 분류할 수 있다.

## 사용자 수준 스레드 (1:n)(User thread)

### 사용자 영역의 스레드 라이브러리로 구현됨

어떤 라이브러리가 스레드의 생성 및 스케쥴링을 담당하는 경우가있다.  
대표적인 예로는 java스레드, posix스레드 등이 있다.

여기서 커널은 스레드의 존재를 모른다. 커널이 몰랐을 때 어떠한 장점을 가지고 있을까?

**커널의 관리(개입)을 받지 않음**  
커널은 개입하지않고 라이브러리영역에서 관리를 해주니 오버헤드가 적고,  
생성 및 관리의 부하가 적다. 또한 이식성이 높다.

그러나 장점만이 아닌 단점도 갖고 있는데,  
커널은 프로세스 단위로 자원을 할당 하기 때문에  
하나의 스레드가 block 상태가 되면, 모든 스레드가 **대기**상태가 된다.

## 커널 수준 스레드 (1:1)(kernel Threads)

### 커널 수준에서 스레드를 관리하겠다

커널안에 여러개의 스레드가 생기고 커널에서 생긴 스레드마다  
사용자 영역의 스레드도 여러개 생긴다. 따라서 오버헤드가 크다.  
다만 커널이 각 스레드를 개별적으로 관리하기 때문에,  
하나의 스레드가 block상태가 되어도, 다른 스레드는 계속 작업 수행이 가능하다.

## 혼합형 (n:m)스레드

그래서 우리의 공학도 들은 각각의 장점을 합쳐서 만들어보자 하고 구상했다.  
n개의 사용자 수준스래드와 m개의 커널스레드를 맵핑하는것이다.  
다만 사용자수준의 스레드가 항상 더 많거나 같아야 한다.  
이러면 사용자수준에서는 원하는 수만 큼의 스레드를 사용이 가능하고,  
커널스레드는 자신에게 할당된 하나의 사용자 스레드가 block이 되어도  
다른 스레드를 수행이 가능하다. 즉 병행처리가 가능하다.
