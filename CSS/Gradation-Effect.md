# 그라데이션 효과

- 배경을 단색이나 이미지로 지정하는 방법외에 CSS3부터 그라데이션 효과로 배경색을 표현하는 것이 가능해졌다.
- 그라데이션 효과 설정 방법에 대해 정리한다.

## 선형 그라데이션 설정

- 색상이 수직, 수평, 대각선 방향으로 일정하게 변하는 그라데이션을 의미한다.
- 기본형은 `linear-gradient(<각도> | to <방향> [<방향>] , start-color[, color-stop[, ...]], end-color);`이다.

속성값 | 설명
------|------
각도 | 그라데이션의 진행 방향. 12시방향을 0deg로 시계방향으로 각도가 증가
방향 | 그라데이션의 진행 방향. left, right, top, bottom이 가능. 방향을 2개 넣어 대각선 지정 가능
start-color | 그라데이션의 시작 색상
color-stop | 그라데이션 도중 바뀌는 부분의 색과 위치(띄어쓰기로 구분). 위치는 백분율로 표시. 위치 생략가능
end-color | 그라데이션의 끝 색상

## 원형 그라데이션 설정

- 원이나 타워형의 중심부터 바깥방향으로 일정하게 변하는 그라데이션을 의미한다.
- 기본형은 `radial-gradient([<최종 모양>] [<크기>] [at <가로 위치> [<세로 위치>]], start-color[, color-stop[, ...]], end-color);`이다.

속성값 | 설명
------|------
최종 모양 | 원이면 circle, 타원이면 ellipse. 기본값은 ellipse
크기 | 원의 크기를 지정.
가로 위치 | 중심의 가로위치를 지정. 키워드(left, center, right)나 백분율
세로 위치 | 중심의 세로위치를 지정. 키워드(top, center, bottom)나 백분율. 생략 할 경우 가로 위치와 동일 값이 설정
start-color | 그라데이션의 시작 색상
color-stop | 그라데이션 도중 바뀌는 부분의 색과 위치(띄어쓰기로 구분). 위치는 백분율로 표시. 위치 생략가능
end-color | 그라데이션의 끝 색상

### 크기 설정

속성값 | 설정
------|-------
closest-side | 그라데이션의 가장자리가 원의 중심에서 요소의 가장 가까운 모서리와 만나게 설정됨
closest-corner | 그라데이션의 가장자리가 원의 중심에서 요소의 가장 가까운 꼭지점과 만나게 설정됨
farthest-side | 그라데이션의 가장자리가 원의 중심에서 요소의 가장 먼 모서리와 만나게 설정됨
farthest-corner | 그라데이션의 가장자리가 원의 중심에서 요소의 가장 먼 꼭지점과 만나게 설정됨

## 반복 그라데이션 설정

### 선형 반복 그라데이션 설정

- 선형 반복 그라데이션은 `repeating-linear-gradient()`를 사용한다.
- 기본형은 `repeating-linear-gradient([<각도> | to <방향> [<방향>],] color-stop, color-stop[, ...]);`

### 원형 반복 그라데이션 설정

- 원형 반복 그라데이션은 `repeating-radial-gradient()`를 사용한다.
- 기본형은 `repeating-radial-gradient([[<최종 모양>] [<크기>] [at <가로 위치> <세로 위치>],] color-stop, color-stop[, ...]);`

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)