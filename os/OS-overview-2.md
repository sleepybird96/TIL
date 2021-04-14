### Reference

[Lecture 2. OS Overview (2/3) / 운영체제 강의](https://youtu.be/hzXVQIlSSos)

# 운영체제 개요 2/3 ~ 3/3

## 운영체제의 구분

### 작업수행방식

- **일괄처리시스템**
  1. 모든 시스템을 중앙에서 관리 및운영
  2. 일정시간 모아두었다가 한번에 처리
  3. 시스템지향적  
     장점: 많은사용자가 시스템자원공유, 처리효율향상  
     단점: 생산성저하, 긴응답시간
- **시분할 시스템**
  1. 여러 사용자가 자원을 동시에 사용
  2. 사용자 지향적  
     장점: 응답시간 단축, 생산성 향상  
     단점: 통신비용 증가, 개인 사용자 체감 속도 저하
- **병렬 처리 시스템**
  1. 단일 시스템 내에서 둘 이상의 프로세서 사용
  2. 메모리 등의 자원공유
  3. 사용목적
  - 성능향상
  - 신뢰성향상
  4. 프로세서간 관계 및 역할 관리 필요
- **분산 처리 시스템**
  1. 네트워크를 기반으로 구축된 병렬처리 시스템
  2. 물리적인 분산, 통신망 이용한 상호연결
  3. 사용자는 분산운영체제를 통해 하나의 프로그램, 자원처럼사용가능
  4. 각 구성요소들간의 독립성유지, 공동작업가능
  5. 클러스터시스템 등  
     장점: 자원공유를 통한 높은 성능, 고신뢰성, 높은 확정성  
     단점: 구축 관리가 어려움
- **실시간 시스템**
  1. 작업 처리에 제한시간을 갖는 시스템
  2. 작업의 종류
  - Hard real-time task
  - Soft real-time task
  - Non real-time task

## 운영체제의 구조

### 커널(kernel)

- OS의 핵심부분, 메모리 상주(가장빈번하게 사용되는 기능들 담당)
- 동의어 (핵, 관리자, 상주프로그램, 제어프로그램)

### 유틸리티(utility)

- 비상주 프로그램
- ui등 서비스 프로그램

### 단일 구조

**장점**

- 커널 내 모듈간 직접 통신
- 효율적 자원관리 및 사용

**단점**

- 커널의 거대화
- 오류 및 버그, 추가기능 구현 등 유지보수가 어려움
- 동일메모리에 모든 기능이 있어, 한 모듈의 문제가 전체시스템 영향

### 계층 구조

**장점**

- 모듈화
- 계층간 검증 및 수정용의
- 설계 및 구현의 단순화

**단점**

- 단일구조 대비 성능 저하
- 원하는 기능 수행을 위해 여러 계층을 거쳐야함

### 마이크로 커널 구조

- 커널의 크기 최소화
  - 필수 기능만 포함
  - 기타 기능은 사용자 영역에서 수행

## 운영체제의 기능

### 프로세스 관리

- 프로세스(Process)
  - 커널에 등록된 실행단위 (실행중인 프로그램)
  - 사용자 요청/ 프로그램의 수행주체(entity)
- OS의 프로세스 관리 기능
  - 생성/삭제, 상태관리
  - 자원할당
  - 프로세스간 통신 및 동기화
  - 교착상태 관리
- 프로세스 정보 관리(PCB)

### 프로세서 관리

- 중앙 처리 장치(CPU)
  - 프로그램을 실행하는 핵심자원
- 프로세스 스케줄링
  - 시스템 내의 프로세스 처리 순서 결정
- 프로세서 할당 관리

### 메모리 관리

- 주기억장치
  - 작업을 위한 프로그램 및 데이터를 올려놓는 공간
- Multi-user, Multi-tasking 시스템
  - 프로세스에 대한 메모리 할당 및 회수
  - 메모리 여유 공간 관리
  - 각 프로세스의 할당 메모리 영역 접근 보호
- 메모리 할당 방법
  - 전체적재
  - 일부적재

### 파일관리

- 파일: 논리적 데이터 저장 단위
- 사용자 및 시스템의 파일 관리
- 디릭토리 구조 지원
- 파일 관리 기능
  - 파일 및 디렉토리 생성/삭제

### I/O 관리

- 입출력 과정
  - OS를 반드시 거쳐야 함