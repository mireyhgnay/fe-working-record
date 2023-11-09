# <div align="center">👩🏻‍💻 bind()</div>

<br>

[🔗 MDM - Function.prototype.bind()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)

[🔗 참고 블로그](https://shplab.tistory.com/entry/Javascript-bind-%ED%95%A8%EC%88%98-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)

<br>

## bind() 함수

bind() 함수는 새롭게 바인딩한 함수를 만드는 함수로, 바인딩한 함수는 원본 함수 객체를 감싸는 함수로써,

바인딩한 함수를 호출하면 일반적으로 래핑된 함수가 호출 된다.

```jsx
const obj = {
  name: "shpark",
};

function bindTest() {
  console.log(this.name); // 여기서는 obj 객체가 this가 아님
}

bindTest(); // undefined 출력

const bindTest2 = bindTest.bind(obj); // bindTest 함수에 obj 객체를 bind
// 이제 obj 를 사용할 수 있게 되었다.

bindTest2(); // obj의 name 값인 shpark 이 표출
```

<br>

하나씩 봐보자면!

```jsx
const obj = {
  name: "shpark",
};

function bindTest() {
  console.log(this.name); // 여기서는 obj 객체가 this가 아님
  console.log(this);
}

bindTest(); // undefined 출력
```

bindTest() 함수 안에서 this 를 콘솔에 찍어보면 Window 객체가 출력된다.

그래서 this.name 을 출력하라고 하면 undefined가 출력된다.

<br>

바인딩 해보자면!

```jsx
const obj = {
  name: "shpark",
};

function bindTest() {
  console.log(this.name); // 여기서는 obj 객체가 this가 아님
  console.log(this); // window 찍힘
}

bindTest(); // undefined 출력

const bindTest2 = bindTest.bind(obj); // obj를 바인딩해주기

bindTest2(); // {name : shpark} 객체 출력
```

bindTest.bind(obj); 로 바인딩 해주면

bindTest 함수안의 this 가 오브젝트 obj 가 된다.

그렇게 되도록 새로운 함수가 복제되어 만들어 진다!!
