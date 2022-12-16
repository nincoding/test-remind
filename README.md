# test-remind

최종 코딩테스트 대비 리마인드 기록 저장소

## 프로젝트 진행 순서

1. 프로젝트 깃허브 링크에 들어가서 우측상단 Fork 아이콘을 누른다.
2. Owner에 나의 깃허브 아이디(nincoding)을 선택한 후, Create fork를 누른다.
3. 바탕화면의 터미널을 열고, `git clone https://github.com/nincoding/레파지토리이름.git`
4. `cd 레파지토리이름`
5. `git checkout -b nincoding`
6. vs코드를 열고, open클릭 -> hansuji -> 레파지토리이름 -> 열기 
7. 파일을 생성하거나 수정할때, 항상 하단 Spaces:2 로 맞추기 (띄어쓰기 대신 tap키를 사용한다.)
8. 처음 문제를 받고, 전체적으로 한번 훑어본다.
9. docs/README.cd 에 구현할 기능 목록을 정리해서 수정 후 저장한다.(각각의 역할대로 분리하여 작성)
  - 프로젝트 이름
  - 기능 목록
  - App(UI로직)
  - 입력기능
  - 출력기능
  - 도메인로직 기능
  - 컨트롤러 
  - 오류판별 기능
  - 기능요구 사항(받은 문제 복붙하면 편함)
  - `[ ]` 와 `[X]` 를 사용하며, 해당 기능을 완료했을때마다 docs 문서를 수정한다.
 10. 작성한 기능 목록을 토대로 해당 파일을 추가하거나, 수정한다.
  - 고정된 상수 같은 경우 constants 폴더를 따로 만들어, `Messages.js파일`(입출력,오류 메세지 상수 객체)과 `Values.js파일`(심볼,컨트롤넘버, 숫자나 고정된 값 객체) 을 생성한다.
  - 입출력 요구사항과 실행 예시를 참고하면 분리하기 쉬워진다.
  - 파일 생성 후 마지막 줄에 모듈 작업을 진행한다. 하나의 클래스 또는 객체를 모듈화할땐 `module.exports = BridgeGame;` 처럼 좌항엔 객체나 클래스 파일 이름을 넣는다.
  - 한 파일에 모듈로 내보낼 객체가 많을땐, `module.exports = { OUTPUT, INPUT, ERROR };` 처럼 생성한 객체이름을 넣어준다.
  - 모듈 된 파일을 불러와서 사용해야 될땐, 해당 파일 맨 윗줄에 아래와 같이 사용한다.
  ```
  const Validate = require("./Validate");
  const { CONTROL, ERROR } = require("./constants/Values");
  const { Console } = require("@woowacourse/mission-utils");
  ```
 11. 해당 프로젝트에서의 진행 흐름(연결고리)을 순서대로 파악하고, 순서에 맞춰 작업을 진행하면 속도가 향상된다. (실행예시를 참고하면 이해하기 쉬움)
  - 해당 파일에서 클래스를 불러올때, 아래처럼 constructor를 활용한다.
  ```
    constructor() {
    this.gameController = new GameController();
  }
  play() {
    this.gameController.play();
  }
  ```
 12. 실행예시를 참고하며, 게임시작 후 준비되어야 할 작업(객체 생성)에 대해 고민한다.
 13. 게임시작 후 계산되어야 할 작업(객체)에 대해 고민한다.
 14. 재실행이 필요한 경우(초기화 객체)에 대해 고민한다.
 15. 오류출력 후 재실행 해야될 경우 컨트롤러에서 `try catch`문을 통해 작성하는 것을 고민한다.
 16. 입력받은 값을 전달받아 오류를 판별해야 될 경우 컨트롤러에서 호출하여 bind 하는 것을 고민한다.
  - 뷰에선 callback 사용을 할 수 있는지 생각하여 적용한다.
 17. 모델에선 값을 return받을 수 있는 메서드 생성을 고민한다.
 18. 컨트롤러에선 전달받은 값을 상황별로 컨트롤할 메서드와 호출 메서드 생성에 대해 고민한다.
 19. 작은 기능별로 작업을 추가 저장 후 vs코드 내에서 터미널을 열어,
 `git status` -> `git add .` -> `git commit -m "커밋메세지 내용작성"` -> `git push origin nincoding` 을 하여 깃허브 nincoding 브랜치에 정상커밋되었는지 체크한다.
 20. 모든 작업을 완료했다면, 풀리퀘스트를 보낸다.
