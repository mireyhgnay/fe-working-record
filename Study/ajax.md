# <div align="center">👩🏻‍💻 Ajax </div>

<br>

@Reference

https://azderica.github.io/00-javascript-ajax/

<br>

### js 라이브러리 중 하나이고, 자바스크립트를 사용한 비동기 통신이다.

<br>

### 왜 사용하나?

- 웹에서 무언가를 부르거나 데이터를 조회하고 싶은 경우, 페이지 전체를 새로고침 하지 않기 위해 사용한다.
- 페이지 전체가 아닌 일부만 갱신 가능하도록 서버에 요청합니다.

<br>

### 예제

```jsx
$.ajax({
  // URL은 필수 요소이므로 반드시 구현해야 하는 Property입니다.
  url: 'url', // 요청이 전송될 URL 주소
  type: 'GET', // http 요청 방식 (default: ‘GET’)
  async: true // 요청 시 동기화 여부. 기본은 비동기(asynchronous) 요청 (default: true)
  cache: true // 캐시 여부
  timeout: 3000, // 요청 제한 시간 안에 완료되지 않으면 요청을 취소하거나 error 콜백을 호출.(단위: ms)
  data: { key: value }, // 요청 시 포함되어질 데이터
  processData: true // 데이터를 컨텐트 타입에 맞게 변환 여부
  contentType: 'application/json', // 요청 컨텐트 타입
  dataType: 'json', // 응답 데이터 형식 (명시하지 않을 경우 자동으로 추측)
  beforeSend: function() {
    // XHR Header를 포함해서 HTTP Request를 하기전에 호출됩니다.
  },
  success: function(data, status, xhr) {
    // 정상적으로 응답 받았을 경우에는 success 콜백이 호출되게 됩니다.
    // 이 콜백 함수의 파라미터에서는 응답 바디, 응답 코드 그리고 XHR 헤더를 확인할 수 있습니다.
  },
  error: function(xhr, status, error) {
    // 응답을 받지 못하였다거나 정상적인 응답이지만 데이터 형식을 확인할 수 없기 때문에
    // error 콜백이 호출될 수 있습니다.
    // 예를 들어, dataType을 지정해서 응답 받을 데이터 형식을 지정하였지만,
    // 서버에서는 다른 데이터형식으로 응답하면  error 콜백이 호출되게 됩니다.
  },
  complete: function(xhr, status) {
    // success와 error 콜백이 호출된 후에 반드시 호출됩니다.
    // try - catch - finally의 finally 구문과 동일합니다.
  },
})
```
