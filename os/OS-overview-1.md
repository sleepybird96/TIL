### Reference

[Lecture 2. OS Overview (1/3) / 운영체제 강의](https://youtu.be/nxl_cUd55Ag)

# 운영체제 개요 1/3

## 운영체제의 역할

- User Interface (CUI, GUI, EUCI)
- Resource management (HW resource, SW resource)
- Process and Thread management
- System management

## 컴퓨터 시스템의 구성

컴퓨터 하드웨어 위에 OS가 있다(커널)  
그 위에 System Call Interface가 있는데,  
사용자가 커널을 직접 access하면 문제가 생기기 때문에  
이를 통해 os에다가 요청을 한다.

## 운영체제의 구분

**동시 사용자 수**

- single-user system(window 7/10, android, ms-dos)
- multi-user system(windows server)

**동시 실행 프로세스 수**

- 단일작업

1. 시스템 내에 하나의 작업만 존재
2. 운영체제의 구조가 간단
   ex) ms-dos

- 다중작업

1. 동시에 여러작업(프로세스)의 수행가능
2. 운영체제의 기능 및 구조가 복잡
   ex) 유닉스, 리눅스, 윈도우 등
