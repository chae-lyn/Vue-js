# Component 통신

- vue는 컴포넌트로 화면을 구성, 같은 웹페이지라도 데이터를 공유할 수 없는 경우가 많음
- 각 컴포넌트들의 scope가 독립적이기 때문에 다른 컴포넌트의 값을 직접참조할 수 없음

### 상/하위 컴포넌트 관계
- vue의 가장 기본적인 데이터 전달방법
```
하위 컴포넌트 - 이벤트 발생 -> 상위 컴포넌트
상위 컴포넌트 - props 전달 -> 하위 컴포넌트
```

- 상위 컴포넌트에서 props라는 속성으로 전달
- 하위 컴포넌트에서 상위 컴포넌트로는 기본적으로 이벤트만 전달 가능
- **props** : 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달할 때 사용하는 속성, 하위 컴포넌트의 속성에 정의

#### 상위에서 하위로 데이터 전달
```javascript
    // 하위 컴포넌트의 props 속성 정의 방식

    Vue.component('child-component', {
        props : ['props name'],
    });
```

- 상위 컴포넌트의 HTML 코드에 정의된 child-component 태그에 v-bind 속성을 정의   
```javascript
<child-component v-bind:props></child-component>
```

#### 하위에서 상위로 데이터 전달
- 이벤트를 발생시켜 (event emit) 상위 컴포넌트에 신호를 보냄
```javascript
    // 이벤트 발생
    this.$emit('eventName');

    // 이벤트 수신
    <child-component v-on:eventName="상위 컴포넌트 메서드명"></child-component>
```

#### 같은 레벨의 컴포넌트 간 통신
```
    Child(하위) -> Parent(상위) -> Children(하위 2개)
```
~~컴포넌트 간 직접적인 통신은 불가하도록 되어있음~~

### Event Bus
- 상위 - 하위 관계가 아닌 컴포넌트 간 통신을 위해 활용할 수 있음
```javascript
    // 화면 개발을 위한 인스턴스와 다른 별도의 인스턴스를 생성하여 활용
    var eventBus = new Vue();

    new Vue({
        . . .
    })
```
1. 이벤트를 발생시킬 컴포넌트에서 `$emit()`호출
```javascript
    eventBus.$emit("refresh", 10);
```
2. 이벤트를 받을 컴포넌트에서 `$on()` 이벤트 수신
```javascript
    // 이벤트 버스 이벤트는 일반적으로 라이트 사이클에서 수신
    new Vue({
        created: function() {
            eventBus.$on("refresh", function(data) {
                console.log(data);  // 10
            });
        }
    });
```


> 참고 웹문서
>
> - [Vue.js 입문서](https://joshua1988.github.io/web-development/vuejs/vuejs-tutorial-for-beginner)