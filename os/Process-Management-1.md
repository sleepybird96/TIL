### Reference

[Lecture 3. Process Management (1/2) / 운영체제 강의](https://youtu.be/jZuTw2tRT7w)

# 프로세스 관리

## JOB vs Process

- 작업(job)/ 프로그램(program)
  - 실행할 프로그램 + 데이터
  - 컴퓨터 시스템에 실행 요청 전의 상태
- 프로세스
  - 실행을 위해 시스템에 등록된 작업
  - 시스템 성능 향상을 위해 커널에 의해 관리 됨

## 프로세스의 정의

- 실행중인 프로그램
  - 커널에 등록되고 커널의 관리하에 있는 작업
  - 각종 자원들을 요청하고 할당 받을 수 있는 개체
  - 프로세스 관리 블록을 할당 받은 개체
  - 능동적인 개체
    - 실행중에 각종 자원을 요구, 할당, 반납하여 진행

## 프로세스의 종류

**역할**

- 시스템 커널 프로세스
- 사용자 프로세스

**병행 수행 방법**

- 독립 프로세스
- 협력 프로세스

## 자원(Resource)의 개념

- 커널의 관리 하에 프로세스에게 할당/반납되는 수동적 개체
- 자원의 분류
  - H/W resources
  - S/W resources

## Process Control Block(PCB)

- OS가 프로세스 관리에 필요한 정보 저장
- 프로세스 생성 시, 생성 됨

**PCB가 관리하는 정보**

- 프로세스 고유 식별 번호
- 스케줄링 정보
- 프로세스 상태
- 메모리 관리 정보
- 입출력 상태정보
- 문맥저장영역(context)
- 계정 정보

## Process State Transition Diagram

### Created State

- 작업을 커널에 등록
- PCB 할당 및 프로세스 생성
- 커널
  - 가용 메모리 공간 체크 및 프로세스 상태 전이
  - ready로 갈것인가 suspended ready로 갈것인가

### Ready State

- 프로세서 외에 다른 모든 자원을 할당 받은 상태

  - 프로세서 할당 대기 상태
  - 즉시 실행 가능 상태

- Dispatch
  - 기다리고 있다가 running상태가 되면 이를 Dispatch,또는 스케쥴링 됐다라고 한다

### Running State

- 프로세서와 필요한 자원을 모두 할당 받은 상태

- Preemption
  - Running state -> ready state
  - 프로세서 스케쥴링(우선순위 변경, 시간초과)
- Block/sleep
  - Running state -> asleep state
  - I/O등 자원 할당 요청

### Blocked/Asleep State

- 프로세서 외에 다른 자원을 기다리는 상태
  - 자원 할당은 System call에 의해 이루어짐
- Wake-up
  - Asleep state -> ready state

### Suspended State

- 메모리를 할당 받지 못한(빼앗긴) 상태
  - 메모리 이미지를 swap device에 보관
  - 커널 또는 사용자에 의해 발생
- Swap-out(suspended), Swap-in(resume)

### Terminated/Zombie State

- 프로세스 수행이 끝난 상태
- 모든 자원 반납 후,
- 커널 내에 일부 PCB 정보만 남아있는 상태
  - 이후 프로세스 관리를 위해 정보 수집
