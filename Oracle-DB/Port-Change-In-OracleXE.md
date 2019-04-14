# Oracle XE에서 포트번호 변경 및 확인 방법

## DB접속 포트번호 확인 방법

1. `oracleXE설치폴더\app\oracle\product\11.2.0\server\network\ADMIN`로 이동
1. `listener.ora`파일 내부의 LISTENER -> DESCRIPTION_LIST -> DESCRIPTION -> PORT의 값을 확인

## DB접속 포트번호 변경 방법

1. sqlplus 실행
2. 시스템 계정으로 접속
3. `LSNRCTL STOP`을 실행
   - 리스너 정지 구문
4. `oracleXE설치폴더\app\oracle\product\11.2.0\server\network\ADMIN`로 이동
5. `listener.ora`파일 내부의 LISTENER -> DESCRIPTION_LIST -> DESCRIPTION -> PORT의 값을 변경
6. `LSNRCTL START`을 실행
   - 리스너 시작 구문
7. `ALTER SYSTEM SET LOCAL_LISTENER = "(ADDRESS = (PROTOCOL = TCP) (HOST = HOST값) (PORT = 변경한 포트 값))";`을 실행
8. `ALTER SYSTEM REGISTER;`을 실행

## HTTP접속 포트번호 확인 방법

1. sqlplus 실행
1. 시스템 계정으로 접속
1. `select dbms_xdb.gethttpport() from dual;`을 실행

## HTTP접속 포트번호 변경 방법

1. sqlplus 실행
1. 시스템 계정으로 접속
1. `exec DBMS_XDB.SETHTTPPORT(nnnn);`을 실행
  - `nnnn`은 변경 할 포트 번호

## 참고

- https://docs.oracle.com/cd/E36055_01/server.112/b66471/network.htm#BHCDDAII