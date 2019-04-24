# Git이란?

- DVCS의 일종으로 가장 널리쓰이는 VCS(Version Control System)이다.
- Git은 이전에 사용하던 VCS(ex. Subversion)와 인터페이스는 비슷하나 정보를 취급하는 방식이 다르다.

## 데이터 관리 방법의 차이

- 일반적인 VCS가 관리하는 정보는 파일들의 목록이다.
  - 변화가 시간순으로 관리되는 파일들의 집합
  - 델타 기반 버전관리 시스템이라고 함

![델타 기반 버전관리 시스템 개략도](https://git-scm.com/book/en/v2/images/deltas.png)

- Git이 관리하는 정보는 파일 시스템 스냅샷의 히스토리다.
  - 버전이 생성 되는 순간의 프로젝트 전체 상태를 저장한다.
  - 변경이 있는 파일만 새로 저장하고, 변경이 없는 파일은 이전 상태의 파일에 대한 링크만 저장한다.

![Git의 버전관리 개략도](https://git-scm.com/book/en/v2/images/snapshots.png)

- Git의 이러한 관리 방식으로 인해 브랜치의 활용이 용이하다.

## 명령 실행 장소의 차이

- CVCS의 경우 저장소가 서버에만 있기 때문에 저장소와 관련한 모든 명령을 서버에 전달해야 했다.
  - 그로인해 서버의 성능에 따라 응답 속도가 결정
  - 서버와 연결되지 않으면 버전의 생성(커밋)이 불가능
- Git의 경우 저장소가 로컬에 전부 복제되어 있기 때문에 로컬 환경에서 명령어의 사용이 가능하다.
  - 네트워크 환경과 무관한 빠른 응답 속도
  - 로컬에서도 버전의 생성(커밋)이 가능

## Git의 무결성

- Git은 **체크섬(checksum)** 이라는 데이터를 통해 모든 데이터(저장 된 파일 및 버전정보 등)을 관리한다.
- Git은 SHA-1해시를 사용해 체크섬을 만들며, 40자 길이의 16진수 문자열로 구성되어 있다.
  - 파일의 내용이나 디렉토리 구조를 이용하여 체크섬 생성
- Git으로 관리되던 저장소는 Git이 없어지는 경우 더 이상 관리가 불가능해 진다.
  - 관리는 체크섬으로 이루어지고 있으며, Git만이 체크섬을 해석 할 수 있기 때문

## Git의 데이터

- Git은 저장소에 데이터를 추가하는 역할 만 한다.
- 되돌리거나, 삭제하는 명령어를 실행시켜도 그렇게 보일 뿐 실제로는 삭제되지 않는다.

## 파일관리 상태 구분

- Git은 관리하고 있는 파일(tracked)과 관리하고 있지 않는 파일(untracked)로 구분한다.
- 관리하고 있는 파일은 크게 3가지 상태로 구분한다.
  - Commited : 저장소에 저장되어 있음
  - Modified : 현재 버전과 비교하여 변경이 생김
  - Staged : Modified 중에 다음 버전으로 적용 시킬 대상으로 선정 됨

![Git 프로젝트의 3가지 영역](https://git-scm.com/book/en/v2/images/areas.png)

- 파일의 3가지 상태는 Git 프로젝트의 3가지 영역과 관련이 있다.
  - Repository : 저장소 영역, 버전으로 관리되어 있는 파일의 집합으로 비교 대상이다.
  - Working Directory(Tree) : 작업 영역, Repository에서 Checkout받은 파일은 이 영역으로 복제된다.
  - Staging Area(Index) : 무대 영역, 다음 버전으로 만들 파일은 이 영역으로 복제된다. 커밋으로 다음 버전이 만들어 지면, 이 영역에 있던 파일은 Repository로 이동하고, 이 영역에서는 삭제된다.

## 작업의 흐름

1. Repository에서 checkout으로 최신 버전의 스냅샷을 Working Directory에 복사한다.
2. Working Directory(Tree)에 있는 파일을 수정한다. (modified로 변경 됨)
3. 대상 파일을 Staging Area에 등록한다. (등록 당시의 파일이 복제 되면서 Staged로 변경 됨)
4. 커밋 메세지를 작성하고, 커밋한다. (Staging Area의 파일이 Repository로 복제 되면서 Commited로 변경 됨)

## 참고

- [Pro Git 2nd Edition > 1.3 시작하기 - Git 기초](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)
