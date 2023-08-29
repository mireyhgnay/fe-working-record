# <div align="center">✏️ get() : 제이쿼리에서 돔 객체 비교하기</div>

<br>

## Jquery를 이용한 Object 비교

제이쿼리에서는 같은 Object를 비교하더라도 계속해서 다르다고 나오는 경우가 있다.

```jsx
console.log($(".div") === $(".div")); // false
```

위 코드 처럼 같은 객체를 비교하는데도 실제 비교를 찍어보면 false 가 나온다.

<br>

제이쿼리를 이용하면 해당 노드에 대한 정보가 배열로 저장이 되는데, 이 배열에서 해당 노드에 대한 정보만 뽑아서 비교해주어야 한다.

```jsx
console.log($(".div")[0] === $(".div")[0]); // true

console.log($(".div").get(0) === $(".div").get(0)); // true
```

.div 노드 정보에서 첫번째 배열만 가져오거나, 혹은 `get()` 메소드를 이용해서 비교하면 원하는 값을 얻어 비교할 수 있다.

<br>
<br>

## `.get()`

**.get()은 선택한 요소를 배열(Array)로 가져옵니다.**

- .get() : 선택한 모든 요소를 가져옵니다.
- .get(index) : 선택한 특정한 것만 가져옵니다.

<br>
<br>

---

<br>

## 🦄 나의 경험

작업 저장소가 모두 제이쿼리로 짜여진 곳이였다.

제이쿼리에서 돔 객체를 비교해서 CSS 속성을 추가할지 말지를 제어해야하는 경우 였다.

```javascript
for (var i = 0; i < itemCount; ++i) {
  let cssProps = {
    float: "none",
    position: "relative",
  };

  let ulWrap = document.getElementById("ulWrap" + (i + 1));
  if (this.welItem.eq(i) !== ulWrap) {
    // true 라면 display 속성 제외
    cssProps.display = "block";
  }
}

this.welItem.eq(i).css(cssProps);
```

<br>

- 맨 아래 있는 this.welItem.eq(i) 요소인 태그 안에 인라인 스타일로 cssProps 를 추가해주고 있었다.

- 그 요소에서 특별한 경우에만 display: block 스타일을 제거해야했다.

- this.welItem.eq(i) 와 ulWrap 를 비교해서 display: block 포함 여부를 결정한다.

<br>

```jsx
var ulWrap = document.getElementById("ulWrap" + (i + 1));
if (this.welItem.eq(i) !== ulWrap) {
  // ... 생략
}
```

⇒ `this.welItem.eq(i)` 돔 요소와 아이디 값이 #ulWrap 이 아니면 display: block 넣어주기!!

🥲 하지만 조건은 맞았지만 뭔가 제대로 되지 않았다^^;

<br>

## 🗣️ 코드리뷰

`this.welItem.eq(i)` 는 jquery 객체라서 `this.welItem.eq(i).get(0)`으로 dom 객체를 가져와서 비교해줘야 할 것 같아요!

<br>

## .get() 으로 가져와 돔 객체를 비교해줘야하는 이유는?

jquery로 가져온 객체를 찍어보면 아래와 같이 나온다.

0번째 인덱스가 dom 객체이다.

![get1](https://github.com/mireyhgnay/fe-working-record/assets/111990266/4e47b18e-bba3-4632-b832-b0e233342cf7)

<br>

![get2](https://github.com/mireyhgnay/fe-working-record/assets/111990266/60e1171d-05f1-450a-9162-ad6d0bd253e7)

내가 지금 비교하고 싶은 것은 dom 객체!

그럼 돔객체는 돔객체끼리 비교해줘야 하기 때문에 첫번째 코드처럼 하게 되면 코드상으로는 같은 코드여도 무조건 false를 반환한다.

<br>

## 🥳 그리하여 수정한 코드

```jsx
var ulWrap = document.getElementById("ulWrap" + (i + 1));
if (this.welItem.eq(i).get(0) !== ulWrap) {
  // ... 생략
}
```

배열 0번째가 dom객체를 가지고 있기 때문에 .get(0) 으로 가져와 돔 객체끼리 비교 할 수 있게 된다.
