# vue란?

+ 프론트엔드 자바스크립트 프레임워크 Angular,React 에비해 가볍고 간단함
+ Vue 에서도 서버사이드 랜더링이 가능함.
+ CDN을 통해 스크립트를 불러와서 적용.

![vue의 인기](https://velopert.com/wp-content/uploads/2017/01/Screenshot-from-2017-01-21-12-10-50.png)


# React와 비교 

#### 공통점 
+ 가상 DOM 사용
+ 컴포넌트를 제공
+ 뷰에 집중하고 있고, 라우터, 상태관리를 위해서는 써드파티 라이브러리를 사용함

####  차이점
![성능비교](https://velopert.com/wp-content/uploads/2017/01/Screenshot-from-2017-01-21-13-52-46.png)


#Vue.js 불러오기

CDN주소로 링크 걸기 
```html
<script src="https://unpkg.com/vue/dist/vue.js"></script>
```

### 시작하기
######html
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app">
    <h1>Hello, {{ name }}</h1>
  </div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
// 새로운 뷰를 정의합니다
var app = new Vue({
  el: '#app', // 어떤 엘리먼트에 적용을 할 지 정의
  // data 는 해당 뷰에서 사용할 정보를 지닙니다
  data: {
    name: 'Vue'
  }   
});
```

### 디렉티브 
Vue의 기능을 사용하기 위해서 사용하는 HTML태그안에 들어가는 하나의 속성 v- prefix 사용
1. v-text
2. v-html
3. v-show
4. v-if
5. v-else
6. v-else-if
7. v-pre
8. v-cloak
9. v-once

######html
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app" v-cloak>
    <h1>hello, {{ name }}</h1>
    
    <!-- v-text -->
    <h1>hello, <span v-text="name"></span></h1>
    
    <!-- v-html -->
    <h1>hello, <span v-html="namehtml"></span></h1>
    <!-- console : app.name = '' -->
    
    <!-- v-show -->
    <h1>hello, <span v-show="visible" v-html="namehtml"></span></h1>
    <!-- visible 변수명 설절 consol app.visible = false -->
  </div>
  
  <div id="app2" v-cloak>
    <h1 v-if="value > 5">value 가 5보다 크군요</h1>
    <h1 v-else-if="value === 5">딱 5</h1>
    <h1 v-else>value 가 5보다 작아요</h1>
    <h2 v-once>초기 값: {{ value }}</h2>
    <h2>현재 값: {{ value }}</h2>
    <!-- app2.value = 6 -->
    <h1 v-pre>{{ 이건 그대로 렌더링 }}</h1>
    <!-- {{}} 머스태쉬 무시 -->
  </div>
  
 

  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
var app = new Vue({
  
  el : '#app' ,// 엘리먼트 지정
  //data 는 해당 뷰에서 사용할 정보
  data : {
    name: 'vue',
    namehtml: '<i>styleship</i>',
    
    visible: true
}
});

var app2 = new Vue({
  
  el : '#app2' ,// 엘리먼트 지정
  //data 는 해당 뷰에서 사용할 정보
  data : {
     value: 5
}
});
```


10. v-bind

######html
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app">
    <h1>Hello, {{ name }}</h1>
    <img v-bind:src="feelsgood"/>
  </div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
// 새로운 뷰를 정의합니다
var app = new Vue({
  el: '#app', // 어떤 엘리먼트에 적용을 할 지 정합니다
  // data 는 해당 뷰에서 사용할 정보를 지닙니다
  data: {
    name: 'Vue',
    feelsgood: 'https://imgh.us/feelsgood_1.jpg'
  }   
});
```
간단한 방법
```html
<img :src="feelsgood"/>
```
응용
>머스태쉬 태그나 디렉티브 사용할때, 그 내부깞을 꼭 데이터명으로 할필요가 없다. 자바스크립트 표현식으로도 사용가능.
```html
<h2>{{ Date() }}</h2>
```

활용

######html
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app">
    <h1>Hello, {{ name }}</h1>
    <h2>{{ Date() }}</h2>
    <img :src="smile ? feelsgood : feelsbad"/>
  </div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
var app = new Vue({
  el: '#app', // 어떤 엘리먼트에 적용을 할 지 정합니다
  // data 는 해당 뷰에서 사용할 정보를 지닙니다
  data: {
    name: 'Vue',
    smile: true,
    feelsgood: 'https://imgh.us/feelsgood_1.jpg',
    feelsbad: 'http://imgh.us/feelsbad.jpg'
  }   
});
```

11. v-for
HTML 에서 for-loop 을 구현
######html
```html

<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app">
    <h2>오늘 할 일</h2>
    <ul>
      <li v-for="todo in todos">{{ index }}{{ todo.text }}</li>
    </ul>
  </div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
var app = new Vue({
  el: '#app', 
  data: {
    todos: [
      { text: 'Vue.js 튜토리얼 작성하기' },
      { text: 'Webpack2 알아보기' },
      { text: '사이드 프로젝트 진행하기' }
    ]
  }   
});
```

>이 디렉티브는 item in items 의 형식으로 작성
items는 Vue 엘리먼트 데이터 안에 들어있는 배열 이름 -> todos
item 랜더링하게될때 각 원소를 가르치는 별칭(alias) --> todo

12. v-model
지금까지의 예제는 단방향바인딩
양방향바인딩 뷰,데이터가 양방향으로 흐르게 해줌
######html
```html

<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app">
    <h1>Hello, {{ name }}</h1>
    <input type="text" v-model="name"/>
  </div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
###### javascript
```javascript
var app = new Vue({
  el: '#app', 
  data: {
    name: 'Vue'
  }   
});
```
응용
######html
```html

<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  
  <div id="app">
    <h1>Hello, {{ name }}</h1>
    <h3><input type="checkbox" v-model="smile"/>웃어요 개구리</h3>
    <img :src="smile ? feelsgood : feelsbad"/>
  </div>
  
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
</body>
</html>
```
```

var app = new Vue({
  el: '#app', // 어떤 엘리먼트에 적용을 할 지 정합니다
  // data 는 해당 뷰에서 사용할 정보를 지닙니다
  data: {
    name: 'Vue',
    smile: true,
    feelsgood: 'https://imgh.us/feelsgood_1.jpg',
    feelsbad: 'http://imgh.us/feelsbad.jpg'
  }   
});
```

https://jsbin.com/hewekigeti/edit?html,js,output
