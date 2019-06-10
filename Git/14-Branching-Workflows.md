# 브랜치 워크플로

- Git브랜치를 이용한 워크플로 중 Long-Running 브랜치와 토픽 브랜치에 대해 정리한다.
- 일반적으로 Long-Running 브랜치와 토픽 브랜치는 혼용하여 사용한다.

## Long-Running 브랜치

- 개발 및 안정화되지 않은 코드와 안정화되어 배포 되는 코드의 브랜치를 분리하여 작업하는 워크플로
- master 브랜치: 배포했거나 배포할 코드가 존재
- develop 브랜치: 개발을 진행하고 안정화하고 있는 코드가 존재
- topic 브랜치: 개발 토픽에 따라 개발을 진행하고 있는 코드가 존재

![Long-Running 브랜치 워크플로](https://git-scm.com/book/en/v2/images/lr-branches-2.png)

> Long-Running 브랜치 워크플로

- topic에 대한 개발이 완료되면 topic브랜치를 develop브랜치에 머지하고, 일련의 개발작업이 완료되어 안정화되면 develop브랜치를 master브랜치에 머지한다.
- 이런 이후로 master브랜치의 커밋 포인터가 가장 뒤에 있고, topic브랜치의 커밋 포인터가 가장 앞에 있게 된다.

![브랜치 별 커밋 포인터](https://git-scm.com/book/en/v2/images/lr-branches-1.png)

> 브랜치 별 커밋 포인터

## 토픽 브랜치

- 토픽 브랜치란 특정 토픽의 작업을 위해 만들어진 호흡이 짧은 브랜치이다.
- Git은 브랜치의 생성과 삭제, Merge가 자유롭기 때문에 특정 토픽에 대한 브랜치를 자주 생성 후 작업 종료시 순서에 상관없이 Merge하는 것이 가능하다.
- 예를 들어 아래와 같은 브랜치가 존재한다고 가정해보자.
  - master 브랜치: 안정화되어 배포 중인 코드
  - dumbidea, iss91 브랜치: 각 토픽에 대해 작업 중인 코드
  - iss91v2 브랜치: iss91 토픽에 대해 실험적인 작업을 하고있는 코드

![토픽 브랜치 예제 - Merge전](https://git-scm.com/book/en/v2/images/topic-branches-1.png)

> 토픽 브랜치 예제 - Merge전

- iss91v2 브랜치와 dumbidea 브랜치가 채택되고, iss91브랜치는 버려진다고 가정하여 Merge한다면 아래의 그림과 같아진다.

![토픽 브랜치 예제 - Merge후](https://git-scm.com/book/en/v2/images/topic-branches-2.png)

> 토픽 브랜치 예제 - Merge후

## 참고

- [Pro Git 2nd Edition > 3.4 Git 브랜치 - 브랜치 워크플로](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%9B%8C%ED%81%AC%ED%94%8C%EB%A1%9C)
