
### 사용자 입력 핸들링

> 좀더 디테일한 설명과 예시들..

#### v-on
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">메시지 뒤집기</button>
</div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: '안녕하세요! Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```

###### join() 함수

```
Join() 함수는 배열로 모든 데이터를 지정된 구분 문자열로 연결하여 하나로 만듬

    var arr = new Array("사과","오이","배추","무우");
    arr.join()
    document.write(arr);

```

#### 컴포넌트 시스템 
> 컴포넌트 시스템은 Vue의 또 다른 중요한 개념. 
이는 작고 그 자체로 제 기능을 하며 재사용할 수 있는 컴포넌트로 구성된 대규모 응용 프로그램을 구축할 수 있게 해주는 추상적 개념임.

![성능비교](https://kr.vuejs.org/images/components.png)


* Vue에서 컴퍼넌트 등록하는 방법

```javascript
// todo-item 이름을 가진 컴포넌트를 정의
Vue.component('todo-item', {
  template: '<li>할일 항목 하나입니다.</li>'
})
```

```html
<ol>
  <!-- todo-item 컴포넌트의 인스턴스 만들기 -->
  <todo-item></todo-item>
</ol>
```
* 위의 내용은 똑같은 내용만 랜더링함. 부모영역의 데이터를 자식 컴포넌트에 넣어야함.
* prop을 전달받을수 있도록 수정


```javascript
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { text: '채소' },
      { text: '치즈' },
      { text: '사람이 먹을 수 있는 다른 무언가' }
    ]
  }
})
```
```html
<div id="app-7">
  <ol>
    <!-- 이제 각 todo-item 에 todo 객체를 제공합니다. -->
    <!-- 화면에 나오므로, 각 항목의 컨텐츠는 동적으로 바뀔 수 있습니다. -->
    <todo-item v-for="item in groceryList" v-bind:todo="item"></todo-item>
  </ol>
</div>
```



#### 다음주 차

+ Vue 인스턴스
  + 생성자
  + 속성과 메소드
  + 인스턴스
+ 탬플릿 문법
