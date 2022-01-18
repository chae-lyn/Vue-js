# ES6

### ES5와 ES6의 코드 차이
```javascript
// ES5
var num = 10;
var sumNumbers = function(a, b) {
    return a + b;
};
sumNumbers(10, 20); // 30


// ES6
const num = 10;
let sumNumbers = (a, b) => {
    return a + b
};
sumNumbers(10, 20); // 30
```

### const와 let
- 변수를 선언할 때 사용하는 예약어
```javascript
// let - 할당된 값을 변경할 수 있음
let a = 10;
a = 20; // 20

// const - 값의 갱신을 허용하지 않음
const a = 10;
a = 20; // Uncaught TypeError: Assignment to constant variable
```

### 블록의 유효 범위
```javascript
// ES5
var i = 10; 
for(var i = 0; i < 5; i++) {
    console.log(i) // 0,1,2,3,4
}
console.log(i); // 5

// ES6
let i = 10;
or(let i = 0; i < 5; i++){
    console.log(i); // 0,1,2,3,4
}
console.log(i); // 10
```

### 화살표 함수
```javascript
// ES5
var sumNumbers = function(a, b) {
    return a + b;
};

// ES6
var sumNumbers = (a, b) => {
    return a + b;
}
```

### Import & Export
- 자바스크립트 모듈화와 관련된 기능, 모듈화란 코드를 특정 기능이나 로직 단위로 구분해 각 모듈로 관리하는 것

```javascript
// 모듈화 기법 중 네임스페이스 활용
var numA = {
    num : 10
};

var numB = {
    num : 20
};
console.log(numA); // 10
console.log(numB); // 20
```

- import : 한 파일에서 다른파일의 내용을 불러올 때 사용
- export : 한 파일의 특정 기능을 다른 파일에서 사용할 수 있도록 설정할 때 사용

```javascript
// ./app/login.js
export const id = 'test';

// ./main.js
import { id } from './app/login.js';
console.log(id);
```