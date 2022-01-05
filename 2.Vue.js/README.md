# Instance, Component, Life Cycle

**Vue.js 기본 구조**

```javascript
<template>
  <div></div>
</template>

<script>
export default {};
</script>

<style></style>
```

### Instance

- 뷰로 화면을 개발하기 위해 필수적으로 생성해야 하는 기본 단위, **필수조건**
- 간단한 템플릿 렌더링부터 데이터 바인딩, 컴포넌트 등 많이 동작이 수행됨

```javascript
new Vue({
  . . .
})
```

- new Vue()로 인스턴스를 생성할 때 Vue를 생성자라고함
  - 뷰로 개발할 때 필요한 기능들을 생성자에 미리 정의,   
  사용자가 그 기능을 재정의하여 편리하게 사용하도록 하기 위해 생성자를 사용

- 뷰 인스턴스 옵션 속성은 인스턴스를 생성할 때 재정의할 data, template 등의 속성을 의미

|   용어   |                                          설명                                          |
| :------: | :------------------------------------------------------------------------------------: |
| template  |                                 사용자에게 보이는 화면                                 |
| methods |                HTML 문서에 들어가는 요소의 정보를 담고 있는 데이터 트리                |
| cerated |            돔의 변경 내역에 대해 즉각적으로 반응, 특정 로직을 수행하는 장치            |

### Life Cycle

|   용어   |                                          설명                                          | 특징 |
| :------: | :------------------------------------------------------------------------------------: |:---:|
| beforeCreate  | 인스턴스가 생성되고 나서 가장 처음으로 실행 | data, methods 속성이 인스턴스에 정의 X |
| created | beforeCreate 다음에 실행 | data, methods 속성이 정의 |
| beforeMount | 컴포넌트가 DOM에 추가 되기 직전에 실행 | 가상 DOM이 생성되어 있으나 실제 DOM에 부착되지는 않은 상태 |
| mounted | 컴포넌트가 DOM에 추가 된 후 호출 | data, computed, methods, watch 등 모든 요소에 접근가능 |
| beforeUpdate | DOM이 재 렌더링 되기 직전에 호출 | 업데이트 된 값들을 가지고 있는 상태이기 때문에<br> 업데이트 된 값으로 다른 값들을 업데이트 할 수 있음 |
| updated | DOM이 재 렌더링된 후에 호출 | 변경 된 후의 DOM을 이용해야 하는 처리를 할 때 사용 |
| beforeDestroy | 컴포넌트가 제거 되기 직전에 호출 | 이벤트 리스너, 컴포넌트에서 동작으로 <br> 할당 받은 자원들을  해제해야 할 때 사용 |
| Destroyed | 컴포넌트가 제거 된 후 호출 | 컴포넌트의 모든 이벤트 리스너와 디렉티브의 바인딩 해제,<br> 하위 컴포넌트도 모두 제거됨 |

> ###### [라이프사이클 다이어그램](https://v3.ko.vuejs.org/guide/instance.html#%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%91%E1%85%B3%E1%84%89%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%8F%E1%85%B3%E1%86%AF-%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%A5%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%86%B7)

### Component

- 화면을 구성할 수 있는 하나의 블록
- HTML 마크업, 자바스크립트 로직을 포함한 하나의 덩어리
- 컴포넌트를 활용하여 화면을 만들면 보다 빠르게 구조화, 일괄적인 패턴으로 개발할 수 있음
- 캡슐화가 자연스럽게 가능, 재사용 가능

##### 전역 컴포넌트
```javascript
Vue.component("componentName", {
  . . .
})
```
- 뷰 라이브러리를 로딩하고 나면 접근 가능한 Vue 변수를 이용하여 등록
- 모든 인스턴스에 등록하려면 Vue 생성자에서 .component()를 호출하여 수행

##### 지역 컴포넌트
```javascript
new Vue({
  . . .
  components: {
    "something" : somethingComponent
  }
})
```
- 인스턴스에 components 속성을 추가하고 등록할 컴포넌트 이름과 내용 정의


<br><br><br>

> 참고 웹문서
>
> - [Vue.js 공식사이트 Life Cycle](https://v3.ko.vuejs.org/api/options-lifecycle-hooks.html)
> - [버미노트](https://beomy.tistory.com/47)
> - [Bottlehs Tech Blog](https://www.bottlehs.com/vue/vue-js-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-&-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%86%8C%EA%B0%9C/)