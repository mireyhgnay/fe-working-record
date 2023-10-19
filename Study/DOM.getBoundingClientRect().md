# <div align="center">👩🏻‍💻 DOM.getBoundingClientRect()</div>

<br>

https://webisfree.com/2020-09-21/[%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8]-%EC%97%98%EB%A6%AC%EB%A8%BC%ED%8A%B8%EC%9D%98-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%9C%84%EC%B9%98-%EC%95%8C%EC%95%84%EB%82%B4%EA%B8%B0-getboundingclientrect

<br>

## DOM.getBoundingClientRect()

대부분의 브라우저에 호환되면서 쉽게 위치 값을 가져올 수 있다.

```jsx
const ele = document.querySelector("#id");
const imgRect = ele.getBoundingClientRect();
console(imgRect);
```

<br>

결과는

```
// 출력결과
{
  bottom: 178
  height: 44
  left: 212.5
  right: 1092.5
  top: 134
  width: 880
  x: 212.5
  y: 134
}
```

- top or y // 화면 상단 부터 대상의 처음 위치 값
- bottom // 화면 상단 부터 대상의 끝 위치 값
- left or x // 화면 좌측 부터 대상의 처음 위치 값
- right // 화면 좌측 부터 대상의 끝 위치 값
- width // 대상의 길이
- height // 대상의 높이

<br>

그래서 특정 스크롤 위치를 구할 때

IntersectionObserver와 getBoundingClientRect을 함께 사용하면 위치와 스크롤 이동과 요소의 위치와 복합적인걸 쉽게 접근해서 구할 수 있다!!
