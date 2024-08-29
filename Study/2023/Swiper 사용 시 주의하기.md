# <div align="center">👩🏻‍💻 Swiper JS 라이브러리 사용 시 주의하기</div>

<br>

## JavaScript 에서 Swiper 라이브러리를 사용하기 위해서는?

Swiper API : https://swiperjs.com/swiper-api#swiper-full-html-layout

Swiper Demos : https://swiperjs.com/demos

Swiper Get Started https://swiperjs.com/get-started

<br>
<br>

## Install

스와이퍼 최신 버전은 10버전이지만, 서비스 환경에서 동작하지 않아 **6.8.4** 버전 설치하여 사용하였습니다.

```bash
npm install swiper@6.8.4
```

<br>
<br>

## Swiper 생성하기

```jsx
import Swiper from "swiper";

const swiper = new Swiper(".swiper-container", {
  loop: true,
  autoplay: { delay: 5000, disableOnInteraction: false },
  navigation: {
    nextEl: ".btn_next",
    prevEl: ".btn_prec",
  },
  pagination: {
    el: ".pagenation",
    type: "fraction",
  },
});
```

<br>
<br>

## 오류1

돔이 다 그려진 상태에서 스와이퍼를 적용해야 합니다.

돔을 레이지 로딩으로 그려지는 경우나 append 로 이후 추가해주는 경우는 스와이퍼가 돔을 인식하지 못해서 제대로 동작하지 않았습니다.

<br>

## 오류1 : 대응 방안

### 1) 돔을 다 그려준 후에! 슬라이드가 구현되도록 합니다.

### 2) 만약 돔을 나중에 그려줘야 하는 경우, swiper의 appendSlide() 를 사용해서 돔을 추가해준다.

🔗 https://swiperjs.com/swiper-api#method-swiper-appendSlide

- 슬라이드로 동작되어야 할 한판의 단위를 문자열로 appendSlide 각 하나씩 추가해서 넣어주는 것!

### 3) appendSlide() 후, swiper.update() 추가!

🔗 https://swiperjs.com/swiper-api#method-swiper-update

- 슬라이드를 수동으로 추가/제거하거나 숨김/표시하거나 Swiper로 사용자 지정 DOM 수정을 수행한 후 호출해야 합니다.
- 이벤트마다 스와이퍼 업데이트 할 때 사용하면 좋을 메소드입니다.

<br>

```jsx
const swiper = new Swiper(".swiper-container", {
  loop: true,
  autoplay: { delay: 5000, disableOnInteraction: false },
  navigation: {
    nextEl: ".btn_next",
    prevEl: ".btn_prec",
  },
  pagination: {
    el: ".pagenation",
    type: "fraction",
  },
});

  // ... 코드 생략 ...
  // targetElement 를 객체로 넣어주고 있는 상황

  swiper.appendSlide(targetElement[0].outerHTML);
  swiper.update();
}
```

<br>
<br>

## 오류2

저렇게 돔을 추가해줘도 자동재생이나 <, > 버튼을 눌러도 슬라이드가 동작되지 않았습니다.

**⭐️ 스와이퍼의 각 기능들을 사용하기 위해서는 사용할 모듈들을 Import 해주어야합니다. ⭐️**

```jsx
// 사용할 모듈 import
import Swiper, { Autoplay, Navigation, Pagination } from "swiper";

// 모듈 사용하기
Swiper.use([Autoplay, Navigation, Pagination]);
const swiper = new Swiper(".swiper-container", {
  loop: true,
  autoplay: { delay: 5000, disableOnInteraction: false },
  navigation: {
    nextEl: ".btn_next",
    prevEl: ".btn_prec",
  },
  pagination: {
    el: ".pagenation",
    type: "fraction",
  },
});
```

<br>

### 그랬더니 성고오오옹!!!!!!!!!!!🥳
