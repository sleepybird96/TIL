### Reference

[Lecture 3. Process Management (2/2) / 운영체제 강의](https://youtu.be/MJTr37lgaMA)

# 프로세스 관리

## 인터럽트

- 예상치 못한, 외부에서 발생한 이벤트
- **인터럽트의 종류**
  - I/O 인터럽트
  - Clock 인터럽트
  - 콘솔 인터럽트
  - 프로그램 체크 인터럽트
  - 머신체크 인터럽트
  - 시스템콜 인터럽트
  - 인터프로세스 인터럽트

### 인터럽트 처리과정

1. 인터럽트 발생
2. 프로세스 중단
3. 인터럽트처리
4. 인터럽트 발생 장소, 원인 파악
5. 인터럽트 서비스 할것인지 결정
6. 인터럽트 서비스 루틴 호출

## 문맥 교환

- **Context**
  - 프로세스와 관련된 정보들의 집합
- **Context saving**
  - 현재 프로세스의 Register context를 저장하는 작업
- **Context restoring**
  - register context를 프로세스로 복구하는 작업
- **Context switching**
  - 실행중인 프로세스의 context를 저장하고,  
    앞으로 실행할 프로세스의 context를 복구하는일

컨텍스트 스위칭은 비용이 많이 들기때문에 지양한다.
