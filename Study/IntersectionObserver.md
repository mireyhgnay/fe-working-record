# <div align="center">👩🏻‍💻 IntersectionObserver</div>

<br>

https://heropy.blog/2019/10/27/intersection-observer/

<br>

## IntersectionObserver

IntersectionObserver는 브라우저 뷰포트(Viewport)와 설정한 요소(Element)의 교차점을 관찰하며, 요소가 뷰포트에 포함/미포함 되는지, 더 쉽게는 사용자 화면에 지금 보이는 요소인지 아닌지를 구별하는 기능을 제공합니다.

이 기능은 비동기적으로 실행되기 때문에, scroll 같은 이벤트 기반의 요소 관찰에서 발생하는 렌더링 성능이나 이벤트 연속 호출 같은 문제 없이 사용할 수 있습니다.

<br>

## 사용하기

new IntersectionObserver()를 통해 생성한 인스턴스(io)로 관찰자(Observer)를 초기화하고 관찰할 대상(Element)을 지정합니다.

```jsx
const io = new IntersectionObserver(callback, options); // 관찰자 초기화
io.observe(element); // 관찰할 대상(요소) 등록
```

observer로 관찰할 선택 대상을 지정할 수 있는게 개인적으로 너무 좋은 기능인 것 같다👍

<br>

## entries

- boundingClientRect: 관찰 대상의 사각형 정보(DOMRectReadOnly)

- intersectionRect: 관찰 대상의 교차한 영역 정보(DOMRectReadOnly)

- intersectionRatio: 관찰 대상의 교차한 영역 백분율(intersectionRect 영역에서 boundingClientRect 영역까지 비율, Number)

- isIntersecting: 관찰 대상의 교차 상태(Boolean)

- rootBounds: 지정한 루트 요소의 사각형 정보(DOMRectReadOnly)

- target: 관찰 대상 요소(Element)

- time: 변경이 발생한 시간 정보(DOMHighResTimeStamp)

<br>

## observer

콜백이 실행되는 해당 인스턴스를 참조합니다.

```jsx
const io = new IntersectionObserver((entries, observer) => {
  console.log(observer);
}, options);

io.observe(element);
```

<br>

```jsx
io1.observe(div); // DIV 요소 관찰
io2.observe(li); // LI 요소 관찰
io2.observe(h2); // h2 요소 관찰
```
