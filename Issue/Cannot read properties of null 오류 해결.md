# <div align="center">๐จ Uncaught TypeError: Cannot read properties of null (reading 'querySelector') ์ค๋ฅ</div>

<br>

## ๐ ์ํฉ

ํ์ ๋ด ์์ ์์๋ฅผ ์ ํํด์ addEventListener ํด๋ฆญ์ด๋ฒคํธ๋ฅผ ์คํํด์ฃผ์ด์ผํ๋ค.  
๊ทผ๋ฐ ํด๋ฆญ์ด๋ฒคํธ ๋์์ ์ ์ํ์ด ๋๋๋ฐ ์ฝ์์ ํด๋น ์๋ฌ๊ฐ ๋จ๊ณ  ์์ด ๋์ํด์ฃผ์๋ค.

<br>

## ๐ฉ๐ปโ๐ป HTML ์ฝ๋

ํ์ ๊ตฌ์กฐ๋ ๋๊ฐ ์ด๋ฌํ ๊ตฌ์กฐ์ด๋ค.

```html
<section class="popup_wrap" id="app_download_popup">
  <div class="popup_dimmed"></div>
  <div class="popup_layer popup_prmo">
    <div class="popup_prmo_thumb">
      <img src="example.png" alt="" />
    </div>
    <div class="popup_btn_wrap">
      <button type="button" class="btn_point">์ฑ์ผ๋ก ๋ณด๊ธฐ</button>
      <a href="#" class="btn_txt">๊ด์ฐฎ์ต๋๋ค. ๋ชจ๋ฐ์ผ์น์ผ๋ก ๋ณผ๊ฒ์.</a>
    </div>
  </div>
</section>
```

์ฌ๊ธฐ์ ์ต์๋จ ๋ถ๋ชจ์์์ธ `#app_download_popup` ๋ฅผ ๊ธฐ์ค์ผ๋ก  
`button.btn_point`, `a.btn_txt` ์์ ๋๊ฐ์ ๋ํ ํด๋ฆญ ์ด๋ฒคํธ๋ฅผ ๊ฐ๊ฐ ์คํํด ์ฃผ์ด์ผํ๋ค.

<br>

## ๐ฉ๐ปโ๐ป JavaScript ์ฝ๋

์๋ ์ฝ๋๋ก ๊ฐ ์ด๋ฒคํธ๋ ์ ์ํ๋์๋ค.

```jsx
function showPopupDownloadLink() {
  const appDownloadPopup = document.querySelector("#app_download_popup");
  const appViewButton = appDownloadPopup.querySelector(".btn_point");
  const webViewButton = appDownloadPopup.querySelector(".btn_txt");

  if (appDownloadPopup) {
    // ์ฑ์ผ๋ก ๋ณด๊ธฐ
    appViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... ํจ์ ๋ด์ฉ ์๋ต
      return false;
    });

    // ๋ชจ๋ฐ์ผ์น์ผ๋ก ๋ณผ๊ฒ์
    webViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... ํจ์ ๋ด์ฉ ์๋ต
      return false;
    });
  }
}
```

<br>

## ๐จย ์๋ฌ ๋ด์ฉ

![error](https://user-images.githubusercontent.com/111990266/224693853-dce0a020-c3a9-474f-84ef-bb1e923d0616.png)

<br>

## ๐จ ์๋ฌ ์์ธ

์ด๋ฆฌ ์ ๋ฆฌ ๊ฒ์์ ํด๋ณด๋ ์ ์๋ฌ๋ ํํ ๋ํ๋๋ ์๋ฌ๋ก ์ฃผ๋ก HTML ์์ DOM์ด ํ์ฑ๋๊ธฐ ์ ์ JS๋ก ์ด๋ฒคํธ๋ฅผ ์ค ๊ฒฝ์ฐ  
๋๋ ํฌ๋กฌ์์ ์ ์๋์ง ์์ ๊ฐ์ฒด์ property๋ฅผ ์ฝ์ด๋ด๊ฑฐ๋ method๋ฅผ ํธ์ถํ์ ๋ ๋ฐ์ํฉ๋๋ค.

<br>

`btn_point`, `btn_txt` ์์๋ `#app_download_popup` ์ด ํ์ ์์๋ก `#app_download_popup` ๊ฐ ์์ ๋๋ง ๋์์ ํด์ผํ๋๋ฐ  
`#app_download_popup` ๊ฐ null์ผ ๊ฒฝ์ฐ (ํ์์ด ๋ธ์ถ๋์ง ์๋ ๊ฒฝ์ฐ)  
ํ์์์์ธ btn_point, btn_txt ์์๊ฐ querySelector ๊ฐ ๋์ง ์๋ ๊ฒ!

<br>

```javascript
const appDownloadPopup = document.querySelector("#app_download_popup");
const appViewButton = appDownloadPopup.querySelector(".btn_point");
const webViewButton = appDownloadPopup.querySelector(".btn_txt");
```

ํ์ ์์๊ฐ appDownloadPopup ๋ถ๋ชจ์ธ ์ํํ ์์กด์ ํ๊ณ ์๊ธฐ ๋๋ฌธ์  
์๋ฌด๊ฒ๋ ์ ์๋์ง ์์ ๊ฐ์ธ appDownloadPopup ์ ์ฐธ์กฐํ๊ฒ๋๋ ํ์ํจ์์๋ querySelector๋ฅผ ์ฌ์ฉํ  ์์๋ค.  
<br>
์  appViewButton์ด๋ webViewButton ๋ณ์๋ appDownloadPopup์ด ์์๋๋ง ์ฌ์ฉํ๋ฉด ๋๋๊น ๋ณ์ ์ ์ธ๋ฌธ๋ค์ if๋ฌธ ์์ ๋ฃ์ด์ฃผ๋ฉด์ ํด๊ฒฐ๋์๋ค.

<br>

์ต์ข ์ฝ๋!

```jsx
function showPopupDownloadLink() {
  const appDownloadPopup = document.querySelector("#app_download_popup");

  if (appDownloadPopup) {
    const appViewButton = appDownloadPopup.querySelector(".btn_point");
    const webViewButton = appDownloadPopup.querySelector(".btn_txt");

    // ์ฑ์ผ๋ก ๋ณด๊ธฐ
    appViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... ํจ์ ๋ด์ฉ ์๋ต
      return false;
    });

    // ๋ชจ๋ฐ์ผ์น์ผ๋ก ๋ณผ๊ฒ์
    webViewButton.addEventListener("click", function (event) {
      event.preventDefault();
      //... ํจ์ ๋ด์ฉ ์๋ต
      return false;
    });
  }
}
```

---

<br>

```
์ง์ง.. ์กฐ๊ธ๋ง ์๊ฐํ๋ฉด ๊ฐ๋จํ ๋ฌธ์ ์๋๋ฐ else๋ฌธ์ผ๋ก ์ด๋ฒคํธ๋ฅผ ๋ง์์ผํ๋ ์ด์๊ฐ๊น์ง ๊ฐ๊ฒ ์ฐธโฆ ใ ใ 

appDownloadPopup ๊ฐ ์๋๋ฉด ๊ตณ์ด ์ ์ธํ  ํ์๊ฐ ์๋ ๋ณ์๊ธฐ๋๋ฌธ์ ๋ฉ๋ชจ๋ฆฌ ๊ด์ ์์ ๋ณด๋๋ผ๋ if๋ฌธ ์์ ์ ์ธํ๋๊ฒ ๋ ์ข๋ค!!!!

์์ผ๋ก ๋ณ์๋ ์ฌ์ฉํ๋ ํจ์ ์์์๋ง ์ ์ธํ๋๋กํ์!!!!
```
