# 데이터베이스 정규화

- 데이터베이스의 설계를 재구성하는 기술
- 1차 정규화, 2차 정규화, 3차 정규화, BCNF, 4차 정규화, 5차 정규화로 나뉘어 진다.
  - 일반적으로는 1차 정규화부터 순차적으로 진행하며, BCNF까지 한다.

## 목적

1. 불필요한 데이터(중복)를 제거한다.
2. 데이터 저장을 "논리적으로" 한다.

## 1차 정규화

- 각 로우마다 컬럼의 값이 1개씩만 있어야 한다. (원자값)
  - 컬럼값이 2개 이상인 경우 1개씩만 존재하도록 나눈다.
  - 중복 행이 늘어남에 따라 데이터의 중복(redundancy)이 증가한다.

### 1차 정규화 전 테이블

Student(PK) | Age | Subject(PK)
--------|-----|---------
Adam | 15 | Biology, Maths
Alex | 14 | Maths
Stuart | 17 | Maths

### 1차 정규화 후 테이블

Student(PK) | Age | Subject(PK)
--------|-----|---------
Adam | 15 | Biology
Adam | 15 | Maths
Alex | 14 | Maths
Stuart | 17 | Maths

## 2차 정규화

- 모든 컬럼이 완전 함수적 종속을 만족해야한다.
  - 즉, 특정 기본키에만 종속된 속성(부분적 종속)이 없어야 한다.
  - 테이블을 쪼개는 것으로 해결이 가능하다.

### 2차 정규화 전 테이블

Student(PK) | Age | Subject(PK)
--------|-----|---------
Adam | 15 | Biology
Adam | 15 | Maths
Alex | 14 | Maths
Stuart | 17 | Maths

### 2차 정규화 후 테이블

Student(PK) | Age
--------|-----
Adam | 15
Alex | 14
Stuart | 17

Student(PK) | Subject(PK)
--------|---------
Adam | Biology
Adam | Maths
Alex | Maths
Stuart | Maths

## 3차 정규화

- 기본키를 제외한 속성들 간의 이행적 함수 종속이 없어야 한다.
  - 즉, 기본키를 제외한 속성들 끼리에 종속 관계가 없어야 한다.
  - 2차 정규화와 마찬가지로 테이블을 쪼개는 것으로 해결이 가능하다.

### 3차 정규화 전 테이블

- 전제조건: 모든 교수는 1개의 과목 만 담당한다.

ManageId(PK) | Student | Subject | Professor | Location
---------|---------|---------|-----------|----------
1 | Adam | Biology | Kim | 5N302
2 | Adam | Maths | Lee | 5S505
3 | Alex | Maths | Lee | 5S505
4 | Stuart | Maths | Lee | 5S505

### 3차 정규화 후 테이블

ManageId(PK) | Student | Subject
-------------|---------|---------
1 | Adam | Biology
2 | Adam | Maths
3 | Alex | Maths
4 | Stuart | Maths

Subject(PK) | Projessor | Location
------------|-----------|----------
Biology | Kim | 5N302
Maths | Lee | 5S505

## BCNF

- Boyce and Codd Normal Form의 약자, 3차 정규화의 강화버전이다.
- 3차 정규화를 만족하면서 모든 결정자가 후보키 집합에 속해야 한다.
  - 즉, 일반 컴럼이 후보키를 결정하지 말아야 한다.

### BCNF 전 테이블

- 전제조건: 모든 교수는 1개의 과목 만 담당한다.

Student(PK) | Subject(PK) | Professor
--------|---------|-----------
Adam | Biology | Kim
Adam | Maths | Lee
Alex | Maths | Lee
Stuart | Maths | Lee

### BCNF 테이블

Student(PK) | Subject(PK)
--------|---------
Adam | Biology
Adam | Maths
Alex | Maths
Stuart | Maths

Professor(PK) | Subject
----------|---------
Kim | Biology
Lee | Maths

## 참고

- [데이터베이스 정규화 1NF, 2NF, 3NF, BCNF](https://3months.tistory.com/193)