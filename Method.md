기능 구현(문제해결)을 위해선 자바스크립트의 데이터 타입별 속성을 파악하고,<br>
자바스크립트 내장 객체,메서드를 활용하여 코드를 구성하는 것이 중요하다.

# 타입의 변환에 자주 사용되는 메서드들에 대한 정리

## 상황에 따른 타입변환의 필요성

- 숫자타입은 산술연산이 가능하다(`+, -, *, /, %`)
- 문자타입은 배열과 같이 인덱스를 가지고 있으며 쪼개서 분리하거나 합칠 수 있다.
- Object는 키와 값으로 이루어져 데이터를 관리하기 용이하다.

- `typeof` : 해당 값의 타입을 확인할 수 있다.

```
typeof 100; // 'number'
typeof -100; // 'number'
typeof '안녕'; // 'string'
```

- `String()` : 괄호안에 값을 문자타입으로 변환하여 반환함

```
let a = 123;
String(a) // '123'
let b = [1,2,3];
String(b) // '1,2,3' 배열을 집어넣으면 , 까지 같이 포함됨 (length변경)
```

- `.toString()` : 앞에 붙이는 객체를 문자타입으로 변환하여 반환함

```
let a = 123;
a.toString(); //'123'
[456].toString(); //'456'
```

- `Number()` : 괄호안에 값이 문자타입 숫자라면 숫자타입으로 변환하여 반환함

```
Number('123'); //123
Number('안녕'); //NaN
```

- `parseInt()` : 괄호안에 값이 문자타입 숫자라면 숫자타입으로 변환하여 반환함(`Number()`와 같은 역할)

```
parseInt('123'); //123
parseInt('안녕'); //NaN
```

- `Object.values()` : 괄호안에 객체를 넣으면 주어진 객체의 값들을 일반적인 반복문과 동일한 순서로 순회되는 열거할 수 있는 배열로 반환함 (객체의 값들만 합쳐서 배열로 빼냄)

```
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};
Object.values(object1); // ['somestring', 42, false]
```

- `Object.keys()` : 괄호안에 객체를 넣으면 주어진 객체의 이름들을 일반적인 반복문과 동일한 순서로 순회되는 열거할 수 있는 배열로 반환함 (객체의 키값들만 합쳐서 배열로 빼냄)

```
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};
Object.keys(object1); // ['a', 'b', 'c']
```

# Number타입에 자주 사용되는 메서드들에 대한 정리

- `.toFixed()` : 앞에 숫자타입을 입력한 후 괄호안에 소수점 n번째 자리까지 변환할 값을 반환함(원하는 소수점자리까지 변환)

```
let a = 123.456;
a.toFixed(0); // 123
a.toFixed(1); // 123.4
```

- `isNaN()` : 괄호 안의 값이 NaN인지 판별함(ture / false로 반환됨)

```
//특정 값이 숫자인지 판별할때 숫자라면 false가 나옴
let a = 123;
let b = '123';
let c = '가나다';
isNaN(a) //false
isNaN(b) //false 타입이 문자여도 값이 숫자라면 false가 나옴 (숫자가 맞음)
isNaN(c) //ture (숫자가 아님)
```

## Math 내장 객체

- `Math.floor()` : 괄호 안의 숫자를 내림하여 반환함

```
Math.floor(100.621); // 100
```

- `Math.ceil()` : 괄호 안의 숫자를 올림하여 반환함

```
Math.ceil(100.621); // 101
Math.ceil(0.1); // 1
```

- `Math.round()` : 괄호 안의 숫자를 반올림하여 반환함

```
Math.round(100.621); // 101
Math.round(100.421); // 100
```

- `Math.abs()` : 괄호 안의 숫자의 절대값을 반환함

```
Math.abs(-100); // 100
Math.abs(100); // 100
```

- `Math.sqrt()` : 괄호 안의 숫자의 루트값을 반환함

```
Math.abs(4); // 2
Math.abs(2); // 1.4142135623730951
```

- `Math.pow()` : 괄호 안의 첫번째 숫자를 밑으로, 두번째 숫자를 지수인 숫자로 반환함(첫번째를 두번째 숫자로 제곱함)

```
Math.pow(2, 5); // 32
```

- `Math.min()` : 괄호 안의 값들을 비교하여 가장 작은 값을 반환함(배열을 괄호안에 넣을땐 경계연산자 사용하기)

```
Math.min(3,1,2) //1
Math.min('3','1','2') //1
//배열을 집어넣을땐 `...` 경계연산자를 사용한다.
let a = [4,5,6]
Math.min(...a) //4
```

- `Math.max()` : 괄호 안의 값들을 비교하여 가장 큰 값을 반환함(배열을 괄호안에 넣을땐 경계연산자 사용하기)

```
Math.max(3,1,2) //3
Math.max('3','1','2') //3
//배열을 집어넣을땐 `...` 경계연산자를 사용한다.
let a = [4,5,6]
Math.max(...a) //6
```

# String타입에 자주 사용되는 메서드들에 대한 정리

- `.length` : 문자열의 길이를 반환함

```
'안녕하세요'.length; // 5
```

- `[n]` : 문자열 뒤에 붙이면 해당 문자열의 n번째 인덱스를 반환함(문자열 인덱스는 0부터 시작)

```
'안녕하세요'[0]; // '안'
```

- `.toLowerCase()` : 문자열을 소문자로 변경함

```
'HELLO WORLD'.toLowerCase(); // 'hello world'
```

- `.toUpperCase()` : 문자열을 대문자로 변경함

```
'hello world'.toUpperCase(); // 'HELLO WORLD'
```

- `.concat()` : 문자열 연결 연산자 `+` 처럼 문자열을 이어붙임 (앞에는 붙일 문자열을, 괄호안에는 뒤에 연이어 붙일 문자열을 넣어준다.)

```
'hello '.concat('world'); // 'hello world'
```

- `.slice()` : 문자열의 일부를 잘라서 반환함 (괄호안에 시작할 인덱스와 종료할 인덱스의 숫자를 넣어준다.)

```
this.#player.upsides = this.#stairs.upside.slice(0, step + 1);
'hello world'.slice(0, 5); // 'hello'
```

- `.substring()` : 앞의 문자열을 입력한 후, 괄호 안에 시작 인덱스와 종료인덱스의 숫자를 넣어주면 문자열을 자른것처럼 반환함(종료인덱스를 넣지 않으면 시작인덱스 부터 문자열의 끝까지 반환)

```
let a = '안녕하세요';
a.substring(0,2) // '안녕'
a.substring(2) // '하세요'
```

- `.indexOf()` : 문자열 내의 특정 문자가 몇 번째 위치하는지 인덱스 숫자로 반환함(앞에는 탐색할 문자열을 입력하고, 괄호안에는 찾을 특정문자를 입력한다. 특정문자가 없다면 `-1`을 반환함/ 특정문자가 있다면 해당 문자가 몇번째 위치에 있는지 위치 인덱스를 반환함)

```
'123'.indexOf(2); // 1
'123'.indexOf('2'); // 1
//활용 예시- 배열이나 문자열에서 특정값이 포함되어있나 찾기
if(lastStep[POSITION_SYMBOLL.UP_STREET].indexOf(MOVING.UNPASSED) > -1 ||
  lastStep[POSITION_SYMBOLL.DOWN_STREET].indexOf(MOVING.UNPASSED) > -1) {
  return RESULT.FAIL;
}
```

- `.split()` : 문자열을 괄호안의 문자를 기준으로 분리하여 배열로 반환함

```
'123'.split(''); // ['1', '2', '3']
```

# 배열(Array)에 자주 사용되는 메서드들에 대한 정리

- `new Array()` : 괄호안에 숫자를 넣으면 인덱스를 그 숫자만큼 가진 새로운 배열을 만든다.

```
let a = new Array(3) // [undefined, undefined, undefined]
```

- `.fill()` : 앞에 입력한 배열에 괄호안에 넣은 값 하나로 length 만큼 전부 채움(채울인덱스, 시작인덱스, 끝인덱스를 인자로 넣을 수 있음)

```
let arr = [1, 2, 3];
arr.fill(4) // [4, 4, 4];
arr.fill(4, 0) // [4, 4, 4];
arr.fill(4, 1) // [1, 4, 4];
arr.fill(5, 0, 2) // [5,5,3];
```

- `.splice()` : 앞에 입력한 배열의 기존 요소를 삭제/ 교체/ 추가하여 변환함(시작할 인덱스, 제거할 요소의 수, 추가할 값)

```
let arr = [1, 2, 3];
arr.splice(1, 0, 4);
console.log(arr); // [1, 4, 2, 3]
//활용 예시
if(moving === MOVING.UPSIDE_STRING) this.#stairs.downside.splice(step, 1, MOVING.BLANK);
```

- `.push()` : `.`앞에 배열을 입력하면 해당 배열의 맨 마지막 인덱스 뒤에 괄호안의 값을 추가하여 변환함

```
let a = 4;
let arr = [1,2,3];
arr.push(a) // [1, 2, 3, 4]
```

- `.pop()` : `.`앞에 배열을 입력하면 해당 배열의 맨 마지막 요소를 제거하고 마지막 요소를 반환함(앞에 입력된 배열은 마지막요소가 제거된 상태로 변환됨)

```
let arr = [1, 2, 3];
arr.pop(); // 3
arr; // [1, 2]
```

- `.join()` : 배열의 모든 요소를 연결해 하나의 문자열로 변환하여 반환함

```
let arr = [1, 2, 3];
arr.join() // '1,2,3' (빈 괄호상태라면 배열의 `,` 까지 같이 하나의 문자로 합쳐짐)
arr.join('') //'123' (괄호안에 `''`을 넣어주면 값만 하나의 문자로 합쳐짐)
let a = 98;
arr.join(a) // '1982983' (괄호안에 특정값을 넣으면 배열의 `,` 부분이 특정값으로 변환됨)
//활용예시
this.#player.downsides.join(MOVING.JUMP);
```

- `.sort()` : `.`앞에 배열을 입력하면, 해당 배열의 요소를 유니코드 순으로 재정렬하여 반환함

```
//문자요소 재정렬시
let arr1 = ['가', '다', '나'];
arr1.sort(); // ['가', '나', '다']

//숫자요소 재정렬시 (오름차순 정렬)
let arr2 = [2, 10, 3, 0];
arr2.sort() // [0, 10, 2, 3] (두자리 이상의 수는 정렬이 정확하지 않음)
// 정확한 숫자 오름차순 정렬
let arr2 = [2, 10, 3, 0];
arr2.sort((a, b) =>  a - b ); // [0, 2, 3, 10] (괄호안에 콜백함수를 넣어 요소의 순서를 재정렬해야됨)
// 정확한 숫자 내림차순 정렬
let arr2 = [2, 10, 3, 0];
arr2.sort((a, b) =>  b - a ); // [10, 3, 2, 0]
```

- `.reduce()` : `.`앞에 배열을 입력하고, 괄호안에 주로 콜백함수를 넣어 배열의 전체 인덱스를 합친 값을 계산할 때 주로 사용됨

```
let arr = [1, 2, 3];
arr.reduce((acc, v) => acc + v); // 6
```

- `.some()` : `.`앞에 배열을 입력하고, 괄호안에 판별함수를 넣어 해당 배열안의 하나의 요소라도 주어진 판별함수를 통과하는지 테스트함(반환값은 ture/ false)

```
let arr1 = [1, 2, 3];
let validate = (element) => element % 2 === 0; //짝수의 조건
arr.some(validate) // ture (짝수 2를 배열안에 포함하고 있기 때문)
let arr2 = [1, 3, 5];
arr2.some(validate) // false (배열안에 홀수만 있기 때문)

```

- `.includes()` : `.` 앞에 배열을 입력하고, 괄호안에 특정 값을 넣으면 해당 배열이 특정값을 포함하고 있는지 판별함(반환값은 ture/ false)

```
let arr = [1, 2, 3];
let a = 2;
let b = 4;
let c = '1';
arr.includes(a); // ture
arr.includes(b); // false
arr.includes(c); // false
```

- `.forEach()` : `.`앞에 배열을 입력한 후, 괄호안에 콜백함수를 넣으면 해당 배열 요소 각각에 대해 실행함 (주로 for문 대신 사용하는 용도로 쓰임)

```
let arr = [1, 2, 3];
arr.forEach((value) => console.log(value * 2)) // 2 4 6 순서대로 총3번 출력됨

//활용예시
memo[user].forEach(userFriend => {
  delete memo[userFriend];
})
```

- `.map()` : `.`앞의 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환함

```
let arr = [1, 2, 3];
arr.map((value) => value * 2) // [2, 4, 6]
arr; // [1, 2, 3] 이기 때문에 map으로 새로운 배열을 반환한 값을 다른 변수에 담아서 사용해야함
//예시
let multy = arr.map((value) => value * 2);
```

- `.filter()` : `.`앞에 배열을 입력한 후, 괄호안에 함수를 넣으면 주어진 함수를 통과(ture)하는 모든 요소를 모아 새로운 배열로 반환함.

```
let arr = [1, 2, 3];
let arr2 = arr.filter((value) => value < 3);
arr2 // [1, 2]
//활용예시
let countRankFive = this.overlapList.filter((value) => value === OVERLAP_COUNT_THREE).length;
```

# Set 객체 메서드에 대한 정리

- `new Set()`; : Set 생성방법, 괄호안에 배열을 집어넣으면 값들로만 이루어진 객체로 반환함
  (Set의 사용은 왠만하면 지양하도록 하자)

```
let x = new Set([1, 2, 3]); // {1, 2, 3}
let y = new Set("안녕") // {'안', '녕'} 괄호안에 문자열을 집어넣으면 한글자씩 잘라서 객체로 반환됨
```

- `new Set().size` : 생성된 Set객체의 길이를 반환함

```
let x = new Set([1, 2, 3]).size // 3
```

# 아스키코드에 주로 사용되는 메서드에 대한 정리

- `.charCodeAt()` : `.`앞에 문자를 아스키코드 넘버로 바꿔줌. (한글자 단위), 괄호안에 숫자를 넣으면 해당 문자열 인덱스를 아스키코드 넘버로 바꿔줌

```
let str1 = 'a';
str1.charCodeAt() //97 소문자는 97 ~  122
let str2 = 'A';
str2.charCodeAt() //65 대문자는 65 ~ 90
let str3 = ' '; //공백
str3.charCodeAt() //32

let str4 = 'bac';
str4.charCodeAt(1) //97

//활용예시 - 배열의 값들을 전부 아스키코드로 바꿔야 할 경우
  for (let i = 0; i < word.length; i++) {
    askiiNum.push(word.charCodeAt(i));
  }
```

- `String.fromCharCode()` : 괄호안에 아스키코드 넘버를 넣어주면 해당하는 문자로 바꿔줌

```
String.fromCharCode(97); // 'a'

//활용예시
for (let i = 0; i < askiiNum.length; i++) {
  if (askiiNum[i] >= 65 && askiiNum[i] <= 90) {
    askiiStr.push(String.fromCharCode(155 - askiiNum[i]));
  }
```

# Symbol 심벌과 상수 사용하기 (자바스크립트에서 enum 흉내내기)

- `Object.freeze()` : 괄호안의 객체를 동결시킴
- `Symbol()` : 괄호안의 값을 심벌화함

```
//활용예시 (주로 고정된 constants 객체에 사용하면 좋음)
const CONTROL = Object.freeze({
  START: Symbol('1'),
  END: Symbol('2'),
  RETRY: Symbol('3')
});
```

- 상수의 네이밍 컨벤션은 대문자 스네이크 표기법을 사용한다.

```
//예시
START_NUMBER
```

# 객체나 클래스 모듈화(내보내기/ 받아오기)

- `module.exports` : 모듈 내보내기

```
//주로 파일 맨 마지막 줄에 작성함
module.exports = BridgeGame; //BridgeGame 이라는 클래스

//한 파일에 내보내야할 객체가 많을때
module.exports = { OUTPUT, INPUT, ERROR }; //객체로 묶어서 해당 객체이름을 각각 입력
```

- `require()` : 모듈 받아오기

```
//주로 파일 맨 윗 줄에 작성함
const Validate = require("./Validate"); //같은폴더의 파일 전체 받아오기
const { CONTROL, ERROR } = require("./constants/Values"); //다른폴더의 파일(특정 객체만) 받아오기
const { Console } = require("@woowacourse/mission-utils"); //외부API(특정 객체만) 받아오기
```

- 모듈로 받아온 객체를 사용하기

```
//활용 예시1 모듈로 받아온 객체 호출하기
  printStart() {
    Console.print(`${OUTPUT.START}\n`);
  }
//활용 예시2
const OutputView = require("./OutputView");
const BridgeGame = require("./BridgeGame");
const Validate = require("./Validate");
const{ CONTROL } = require("./constants/Values");

class GameController {

  constructor() {
    this.brideGame = new BridgeGame();
    this.validate =  new Validate();
  }

  play() {
    OutputView.printStart();
  }
}
```

# 입력값을 외부에서 오류 처리해야 할 때

- `.bind(this)` : 새로운 함수를 생성, 받게되는 첫 인자의 value로는 this 키워드를 설정하고, 이어지는 인자들은 바인드된 함수의 인수에 제공됨.

- `try {} catch(error) {}` : try 문 안에는 오류를 판별할 메서드를 호출, catch 문 안에는 오류발생시 계속 실행될 메서드를 호출

- `throw new Error()` : 오류를 발생시킴, 괄호안에는 오류가 실행될 때 사용할 메세지를 넣음

```
//활용예시 - 입력값을 try/catch문으로 전달
requestBridgeSize() {
  InputView.readBridgeSize(this.tryBuildBridge.bind(this));
}

//try/catch문에서 오류 발생 시 재실행 될 수 있도록 만듬
tryBuildBridge(size) {
  try {
    this.validate.validateBridgeSize(size);
    this.brideGame.ready(size);
    this.requestMoving();
  } catch(error) {
    this.retryRequestBridgeSize();
  }
}

//조건에 맞지 않다면 오류 발생시키도록 구현한 메서드
validateCommand(command) {
  if(command !== RETRY.REPLAY && command !== RETRY.END) throw new Error(ERROR.INPUT_RETRY);
}
```

# class 의 필드를 선언할 때, `#` 활용하기

- class 의 순서도 컨벤션

```
class 클래스명 {

  필드

  constructor( ) {

  }

  메서드( ) {

  }
}
```

- `#변수` : 필드에 변수 선언시 변수앞에 `#`을 붙여 private class 필드로 구현한다. (객체의 상태를 외부에서 직접 접근하는 방식을 최소화)

```
//활용예시
class BridgeGame {

  #stairs;
  #player;
  #count;

  constructor() {
    this.#stairs = { bridge: [] };
    this.#player = { step: [], upsides: [], downsides: [] };
    this.#count = 1;
  }

  ready(size) {
    const bridgeInformation = makeBridge(Number(size), generate);
    this.#stairs.bridge = bridgeInformation;
    this.addBridgeCondition();
  }
}

```
