# async & await
- 자바스크립트의 비동기 처리 패턴 중 하나
- 기존의 비동기 처리 방식인 콜백함수와 프로미스의 단점을 보완, 개발자가 읽기 좋은 코드를 작성할 수 있게 도와줌

### 기본문법
```javascript
async function 함수명() {
    await 비동기처리_메서드명();
}
```
- 함수의 앞에 async라는 예약어를 붙이고 한수 내 로직 중 HTTP 통신을 하는 비동기 처리 코드 앞에 await을 붙임
- 주의점 : 비동기 처리 메서드가 꼭 프로미스 객체를 반환해야 await가 의도한 대로 동작함

```javascript
// promise 
function getUser() {
    const user = this.getUserApi()
    .then(user => {
        return user;
    })
}

// async & await
async function getUser() {
    const user = await this.getUserApi();
}
```

### 반복문 처리
```javascript
// 비동기 처리를 위한 비동기 호출 샘플
function wait(m) {
    return ne Promise(resolve => setTimeout(resolve, m);)
}

async function waitLog(item) {
    await wait(500);
    console.log( ${item} );
}

// forEach
async function forEachLog(){
    [1, 2, 3].forEach(async index => await this.waitLog(index));
    console.log('end');     
    // end가 먼저 출력된 후 1, 2, 3이 출력
    // forEach는 반복문 전체가 종료되는 것에 대한 결과를 기다려 주지 않음
}

// for...of
async function forOfLog(){
    const arrays = [1, 2, 3];

    for(const index of arrays) {
        await this.waitLog(index);
    }
    console.log('end');
    // 1,2,3이 출력된 후 end 출력
}
```

<br><br><br>

> 참고 웹문서
>
> - [캡틴판교](https://joshua1988.github.io/web-development/javascript/js-async-await/)
> - [woolta](https://blog.woolta.com/categories/3/posts/138)