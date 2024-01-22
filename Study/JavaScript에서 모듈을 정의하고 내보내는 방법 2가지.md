# <div align="center">✏️ JavaScript에서 모듈을 정의하고 내보내는 방법 2가지</div>

<br>

자바스크립트 구현시 내가 기존에 많이 사용했던 방법은 객체를 내보내는 방법이였다.

코드의 차이를 보자면

## 클래스로 내보내기

```jsx
export default class Main {
  constructor() {
    this.autoPlay();
    this.setEvent();
  }

  autoPlay() {
    // code ...
  }

  setEvent() {
    // code ...
  }
}
```

<br>

## 객체로 내보내기

```jsx
const moreButton = bannerGallery.querySelector(".more_button");
const closeButton = bannerGallery.querySelector(".close_button");

const handleClickEvent = () => {
  // code...
};

const setEvent = () => {
  // code..
};

export default {
  render() {
    try {
      handleClickEvent();
      setEvent();
    } catch (error) {
      console.warn(error);
    }
  },
};
```

<br>

## 두 방식의 차이점은?

1. 클래스 vs 객체
   1. 클래스로 내보내면 클래스를 정의하고 내보냅니다. 클래스는 객체지향프로그래밍에서 사용됩니다.
      클래스를 사용하여 인스턴스를 생성할 수 있습니다.
      (인스턴스란? [https://velog.io/@k7nsuy/인스턴스란](https://velog.io/@k7nsuy/%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%EB%9E%80)) ⇒ `Animal dog = new Animal()`
      그래서 최종적으로 렌더링 될 때 this.oHomeMainBannerView = new HomeMainBannerView(); 이렇게 내보내는군…
   2. 객체를 바로 내보냅니다. render 메서드가 존재합니다.
2. 인스턴스화 vs 직접 호출
   1. 클래스를 사용해서 객체를 인스턴스화 하고, 생성자를 호출해야 합니다.
      new Main() 이런식으로 호출해야 렌더링 됩니다.
   2. 객체 방식은 객체를 바로 내보내기 때문에 render 메서드를 호출할 수 있습니다.
      Main.render(); 이렇게 호출합니다.
3. 예외 처리
   1. 클래스에서는 따로 예외처리를 구현하고 있지 않습니다.
   2. try-catch 를 사용해서 안전하게 에러 처리를 할 수 있습니다.

<br>

## 뭘 사용해야할까?

콛의 선택은 사용 사례에 따라 다를 것이다.

클래스를 사용하면 더 많은 기능과 상태를 포함할 수 있지만, 단순한 기능을 갖는 경우에는 객체를 지겆ㅂ 내보내는 것이 더 간단할 수 있습니다.
