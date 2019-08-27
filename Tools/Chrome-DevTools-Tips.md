# 크롬 개발자 도구 사용 팁

- 크롬 71 버전 기준으로 개발자 도구 사용 팁을 정리한다.

## 일반

- 크롬 개발자 도구를 사용 할 경우 게스트 창에서 수행하는 것을 추천한다.
  - 디버깅시 확장 프로그램이 영향을 줄 수 있다.

## Elements 탭

- 폰트 크기 번경시 키보드의 화살표로 조정 가능하다.
  - 화살표를 누르면 1씩 변화
  - Shift + 화살표를 누르면 10씩 변화
- Event Listeners 탭에서 HTML태그에 설정되어 있는 이벤트와 자바스크립트 코드위치가 확인 가능하다.
- html태그에 breakpoint 설정이 가능하다.
  - breakpoint를 걸 태그를 Elements탭의 코드에서 클릭
  - 마우스 오른쪽 클릭 -> Break On
    - subtree modifications: 태그 내부의 내용이 변경될 때 breakpoint 설정
    - attribute modifications: 태그의 속성이 변경될 때 breadpoint 설정
    - node remover: 태그가 삭제될 때 breakpoint 설정
  - breakpoint가 설정되면 해당 태그의 코드 좌측에 동그라미가 표시 됨
  - breakpoint를 해제하고 싶을 경우, 설정 할 때와 동일한 순서로 조작

## Sources 탭

- Sources 탭에서 `ESC`키를 누르면 Console 창이 사라지고, 다시 누르면 표시된다.
- Event Listener Breakpoints를 이용하면 특정 이벤트가 발생에 Breakpoint 설정이 가능하다.
  - 소스를 보고 특정이벤트가 어떤 코드와 연결되어 있는지 찾는 수고로움이 사라진다.
- 파일 네비게이션의 Filesystem 탭에서 현재 작업중인 파일이 있는 폴더를 연결 할 경우, 크롬에서 수정한 코드가 실제 파일에 저장된다.
  - 서버에서 가져오는 파일과 싱크가 되었는지는 파일아이콘의 왼쪽하단의 회색점으로 확인 가능하다.
  - 대상 파일인데도 싱크가 되지 않았다면, network 탭에서 Disable cache를 선택하고 새로고침한다.
- debugger부분에 Pause on exceptions(원 안에 세로선 두개가 그려진 아이콘)를 활성화 시키면, 자바스크립트 실행 시 예외가 발생할 경우, 예외 발생 직전에  breakpoint가 설정된 것처럼 동작한다.
  - 예외 발생으로 인해 예외 발생 부분에서 멈췄을 경우, 예외가 발생 할 부분을 정상적으로 수정 후 Resume 시키면, 정상적으로 동작한다.
- breakpoint에 조건을 적용하는 것이 가능하다.
  - breakpoint를 설정할 라인을 클릭
  - 마우스 오른쪽 클릭 -> Edit breakpoint...
  - breakpoint가 걸릴 조건을 논리식으로 작성
- Blackboxing을 이용해 외부 라이브러리를 디버깅 시 무시할 수 있다.
  - 라이브러리 사용시 이벤트로 breakpoint를 설정 할 경우, 라이브러리 내부의 함수에 breakpoint가 걸리는 경우가 발생한다.
  - 이러한 경우 라이브러리 파일을 blackbox로 지정 할 경우, 디버깅 시에 무시되어 원하는 부분에 breakpoint가 걸리도록 하는 것이 가능하다.
  - 설정방법 : 개발자 도구 설정(`F1`) -> Blackboxing -> Add Pattern... -> blackbox화 할 파일을 선택하는 정규표현식 입력 -> Add
- 특정 AJAX 통신이 발생 할때 break되도록 설정 할 수 있다.
  - XHR/fetch Breakpoints에 확인하고 싶은 AJAX의 접속 URL을 등록하면 된다.

## Console 탭

- 디버깅 중 Console 창에서 특정 변수를 입력하면 변수의 저장값이 콘솔창에 표시된다.
- 디버깅 중 Console 창에서 `copy(arg)`메소드를 이용하면 `arg`에 저장된 값을 clipboard에 복사 할 수있다.
  - 변수의 값을 복사하기위해 마우스를 사용하는 수고로움이 사라진다.
- console sidebar에서는 콘솔에 표시된 메세지를 그룹핑해서 보여준다.
- Console 창에서 `monitorEvents('이벤트 감시 부분의 DOM', '이벤트 종류')`메소드를 이용하면 해당 부분의 해당 이벤트가 발생하였을 경우, 이벤트의 정보가 console에 출력된다.
  - ex: `monitorEvents('document.body', 'click');`

## 크롬에서 캐쉬 사용하지 않게 하는 방법

1. 개발자 도구를 연다.
2. settings로 들어간다. (F1)
3. Preferences -> Network -> Disable cache (while DevTools is open)을 체크한다.
4. 끝!

## 참고

- [[토크ON세미나] Javascript 디버깅 및 테스트 방법 1강 | T아카데미](https://youtu.be/_RMRIPz4Xr0)
- [[토크ON세미나] Javascript 디버깅 및 테스트 방법 2강 | T아카데미](https://youtu.be/TSw69uo-1e0)
- [[크롬/Chrome] 개발자도구 - 캐시 사용 없이 새로고침 하기](https://kkotkkio.tistory.com/55)