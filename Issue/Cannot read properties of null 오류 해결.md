# <div align="center">🚨 Uncaught TypeError: Cannot read properties of null (reading 'querySelector') 오류</div>

<br>

## 📍 상황

팝업 내 자식 요소를 선택해서 addEventListener 클릭이벤트를 실행해주어야한다.  
근데 클릭이벤트 동작은 잘 수행이 되는데 콘솔에 해당 에러가 뜨고 있어 대응해주었다.

<br>

## 👩🏻‍💻 HTML 코드

팝업 구조는 대강 이러한 구조이다.

```html
<section class="popup_wrap" id="app_download_popup">
  <div class="popup_dimmed"></div>
  <div class="popup_layer popup_prmo">
    <div class="popup_prmo_thumb">
      <img src="example.png" alt="" />
    </div>
    <div class="popup_btn_wrap">
      <button type="button" class="btn_point">앱으로 보기</button>
      <a href="#" class="btn_txt">괜찮습니다. 모바일웹으로 볼게요.</a>
    </div>
  </div>
</section>
```

여기서 최상단 부모요소인 `#app_download_popup` 를 기준으로  
`button.btn_point`, `a.btn_txt` 요소 두개에 대한 클릭 이벤트를 각각 실행해 주어야했다.

<br>

## 👩🏻‍💻 JavaScript 코드

아래 코드로 각 이벤트는 잘 수행되었다.

```jsx
function showPopupDownloadLink() {
  const appDownloadPopup = document.querySelector("#app_download_popup");
  const appViewButton = appDownloadPopup.querySelector(".btn_point");
  const webViewButton = appDownloadPopup.querySelector(".btn_txt");

  if (appDownloadPopup) {
    // 앱으로 보기
    appViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... 함수 내용 생략
      return false;
    });

    // 모바일웹으로 볼게요
    webViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... 함수 내용 생략
      return false;
    });
  }
}
```

<br>

## 🚨 에러 내용

![error](https://user-images.githubusercontent.com/111990266/224693853-dce0a020-c3a9-474f-84ef-bb1e923d0616.png)

<br>

## 🚨 에러 원인

이리 저리 검색을 해보니 위 에러는 흔히 나타나는 에러로 주로 HTML 에서 DOM이 형성되기 전에 JS로 이벤트를 줄 경우  
또는 크롬에서 정의되지 않은 객체의 property를 읽어내거나 method를 호출했을 때 발생합니다.

<br>

`btn_point`, `btn_txt` 요소는 `#app_download_popup` 이 하위 요소로 `#app_download_popup` 가 있을 때만 동작을 해야하는데  
`#app_download_popup` 가 null일 경우 (팝업이 노출되지 않는 경우)  
하위요소인 btn_point, btn_txt 요소가 querySelector 가 되지 않는 것!

<br>

```javascript
const appDownloadPopup = document.querySelector("#app_download_popup");
const appViewButton = appDownloadPopup.querySelector(".btn_point");
const webViewButton = appDownloadPopup.querySelector(".btn_txt");
```

하위 요소가 appDownloadPopup 부모인 얘한테 의존을 하고있기 때문에  
아무것도 정의되지 않은 값인 appDownloadPopup 에 참조하게되니 하위함수에는 querySelector를 사용할 수없다.  
<br>
저 appViewButton이랑 webViewButton 변수는 appDownloadPopup이 있을때만 사용하면 되니까 변수 선언문들을 if문 안에 넣어주면서 해결되었다.

<br>

최종 코드!

```jsx
function showPopupDownloadLink() {
  const appDownloadPopup = document.querySelector("#app_download_popup");

  if (appDownloadPopup) {
    const appViewButton = appDownloadPopup.querySelector(".btn_point");
    const webViewButton = appDownloadPopup.querySelector(".btn_txt");

    // 앱으로 보기
    appViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... 함수 내용 생략
      return false;
    });

    // 모바일웹으로 볼게요
    webViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... 함수 내용 생략
      return false;
    });
  }
}
```

---

<br>

```
진짜.. 조금만 생각하면 간단한 문제였는데 else문으로 이벤트를 막아야하나 이생각까지 간게 참… ㅠㅠ

appDownloadPopup 가 아니면 굳이 선언할 필요가 없는 변수기때문에 메모리 관점에서 보더라도 if문 안에 선언하는게 더 좋다!!!!

앞으로 변수는 사용하는 함수 안에서만 선언하도록하자!!!!
```
