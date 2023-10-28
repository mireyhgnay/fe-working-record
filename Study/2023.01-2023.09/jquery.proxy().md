# <div align="center">👩🏻‍💻 jquery.proxy() : 저장소에 많이 보이는 jquery 문법</div>

<br>

> 🔗 제이퀴리 공식 문서 https://api.jquery.com/jquery.proxy/

<br>

## 상황

저장소에 제이쿼리로 되어있는 코드가 많이 남아있는데, 그 중에서도 클릭이벤트나 전반적인 함수에

`$.proxy` 라고 앞에 꼭 붙어있었다.

대체 무엇인가?

<br>

## 이해하기

setEvent 라는 함수 클릭이벤트에 $.proxy(this.onClickTab, this) 가 사용되었다.

```jsx
setEvent: function(){
  this.welTabs.on('click', $.proxy(this.onClickTab, this));
},
```

<br>

onClickTab 함수가 별도로 존재

```jsx
onClickTab: function(e){
  e.preventDefault();
  var welCurrTab = $(e.currentTarget);

  this.welTabs.parent().removeClass('on');
  // 생략...
}
```

### 즉, onClickTab 함수를 setEvent 함수 안에서 접근할 수 있는 this로 쓰겠다.

- 클릭 함수 안에서 다른 this에 접근해야할 때 proxy를 쓰는 것이다.
- 클릭 함수 안에서 원래 this가 아닌 다른 this를 쓸거야! 라고 하면 $.proxy(함수, 다른 this)를 쓰는 것이다.
