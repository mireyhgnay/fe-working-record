# <div align="center">👩🏻‍💻 new Promise()</div>

<br>

@Reference

- https://velog.io/@bigbrothershin/JavaScript-Promise-%EC%83%9D%EC%84%B1%EC%9E%90
- https://joshua1988.github.io/web-development/javascript/promise-for-beginners/

<br>

### 프로미스

프로미스는 자바스크립트 비동기 처리에 사용되는 객체입니다.

자바스크립트의 비동기 처리란 ‘특정 코드의 실행이 완료될 때까지 기다리지 않고

다음 코드를 먼저 수행하는 자바스크립트의 특성’을 의미합니다.

프로미스는 주로 서버에서 받아온 데이터를 화면에 표시할 때 사용합니다.

<br>

### 프로미스의 3가지 상태

- Pending (대기) : 비동기 처리 로직 완료 안된 상태
- Fulfilled (이행) : 비동기 처리 완료되어 프로미스가 결과 값을 반환해준 상태
- Rejected (실패) : 비동기 처리가 실패하거나 오류 발생한 상태

<br>

### Pending

먼저 아래와 같이 new Promise() 메서드를 호출하면 대기(Pending) 상태가 됩니다.

```jsx
new Promise();
```

<br>

new Promise() 메서드를 호출할 때 콜백 함수를 선언할 수 있고, 콜백 함수의 인자는 resolve, reject입니다.

```jsx
new Promise(function (resolve, reject) {
  // ...
});
```

<br>

### Fulfilled

여기서 콜백 함수의 인자 resolve를 아래와 같이 실행하면 이행(Fulfilled) 상태가 됩니다.

```jsx
new Promise(function (resolve, reject) {
  resolve();
});
```

<br>

그리고 이행 상태가 되면 아래와 같이 then()을 이용하여 처리 결과 값을 받을 수 있습니다.

```jsx
function getData() {
  return new Promise(function (resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// resolve()의 결과 값 data를 resolvedData로 받음
getData().then(function (resolvedData) {
  console.log(resolvedData); // 100
});
```

<br>

## Rejected

new Promise()로 프로미스 객체를 생성하면 콜백 함수 인자로 resolve와 reject를 사용할 수 있다고 했습니다. 여기서 reject를 아래와 같이 호출하면 실패(Rejected) 상태가 됩니다.

```jsx
new Promise(function (resolve, reject) {
  reject();
});
```

<br>

그리고, 실패 상태가 되면 실패한 이유(실패 처리의 결과 값)를 catch()로 받을 수 있습니다.

```jsx
function getData() {
  return new Promise(function (resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// reject()의 결과 값 Error를 err에 받음
getData()
  .then()
  .catch(function (err) {
    console.log(err); // Error: Request is failed
  });
```

<br>

### 매개변수

실행 함수는 프로미스 구현에 의해 resolve와 reject 함수를 받아 즉시 실행됩니다.

executor는 결과 즉시 얻든, 늦게 얻든 상관없이 아래 콜백 중 하나를 반드시 호출해야 합니다.

- resolve(value) — 일이 성공적으로 끝난 경우 결과를 나타내는 value와 함께 호출
- reject(error) — 에러가 발생한 경우 에러 객체를 나타내는 error와 함께 호출
