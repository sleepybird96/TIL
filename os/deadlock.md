### Reference

[Lec 7. Deadlock (1/5) - Deadlock and Resource types / 운영체제 강의](https://youtu.be/xvoEsy2zJnc)

# 교착상태 (Deadlocks)

- Blocled/Asleap state

  - 프로세스가 특정 이벤트를 기다리는 상태
  - 프로세스가 필요한 자원을 기다리는 상태

- Deadlock state

  - 프로세스가 발생 가능성이 없는 이벤트를 기다리는 경우
    - 프로세스가 데드락상태에 있음
  - 시스템 내에 deadlock에 빠진 프로세스가 있는경우
    - 시스템이 deadlock 상태에 있음

- **Starvation vs Deadlock**

Starvation은 cpu를 기다린다 즉 ready상태이고,  
이것이 기다리고 있는것은 자원이고 절대 발생할 수 없는 사건이 아닌,  
운이 없어서 계속 기다리는 현상이다.  
Deadlock은 발생가능성이 없다는 점에서 차이가 있다.

## 자원의 분류

**일반적 분류**

- Hardware resorces vs Software resources

### 선접 가능 여부에 따른 분류

- preemptible resources

  - 선점 당한 후, 돌아와도 문제가 발생하지 않는 자원
  - Processor, memmory 등

- Non-preemptible resources
  - 선점 당하면, 이후 진행에 문제가 발생하는 자원
    - Rollback, restart등 특별한 동작이 필요
  - E.g, disk drive 등

### 할당 단위에 따른 분류

- Total allocation resources

  - 자원 전체를 프로세스에게 할당
  - E.g., Proessor, disk drive 등

- Partitioned allocation resources
  - 하나의 자원을 여러 조각으로 나누어, 여러 프로세스 들에게 할당
  - E.g., Memory 등

### 동시 사용 가능 여부에 따른 분류

- Exclusive allocation resources

  - 한 순간에 한 프로세스만 사용 가능한 자원
  - E.g., Processor, memory, disk drive 등

- Shared allocation resource
  - 여러 프로세스가 동시에 사용 가능한 자원
  - E.g., Program(sw), shared data 등

### 재사용 가능 여부에 따른 분류

- SR (Serially-reusable Resources)

  - 시스템 내에 항상 존재 하는 자원
  - 사용이 끝나면 다른 프로세스가 사용 가능
  - E.g., Processor, memory, disk drive, program 등

- CR (Consumable Resources)
  - 한 프로세스가 사용한 후에 사라지는 자원
  - E.g., signal, message 등

## Deadlock과 자원의 종류

- Deadlock을 발생시킬 수 있는 자원의 형태

  - Non-preemptible resources
  - Exclusive allocation resources
  - Serially reusable resources

- CR을 대상으로 하는 Deadlock model
  - 너무 복잡!!!!!
