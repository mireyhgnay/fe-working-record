# <div align="center">👩🏻‍💻 webpack HtmlWebpackPlugin 에 사용되는 template.html 파일의 용도는?</div>

<br>

## **📍 상황**

모노레포 이관 작업 중 public/template.html 파일이 대부분 사용되고 있는데

어느 서비스에서는 사용되지 않아 이게 어느 경우에 필수인거고?

어떤 용도로 사용되는지 제대로 이해하기 위해 webpack HtmlWebpackPlugin 검색해서 공부가 필요한 것 같다.

<br>

## **public/template.html 은?**

webpack dev server 돌릴 때 사용할 html 이다.

이 파일이 없다면, 현재 구조에서 webpack dev server 걸어서 작업할 html 이 없는 것!!

<br>

### **`/webpack/config.dev.server.js`**

```js
module.exports = {
  mode: 'development',
  devtool: 'cheap-module-eval-source-map',
  **plugins: [
    new HtmlWebpackPlugin({
      template: 'public/template.html',
    }),**
    new webpack.HotModuleReplacementPlugin(),
    new FriendlyErrorsWebpackPlugin(),
  ],
  devServer: {
    open: true,
    host: PROXY_HOST,
    historyApiFallback: true,
    inline: true,
    hot: true,
    port: 3000,
    proxy,
  },
};
```

<br>

프록시로 dev 서버 화면 불러와서 js 파일만 붙여서 테스트 하는 경우가 있고,

이 template.html 은 다른 서버에서 화면을 불러오는게 아니라 그 template.html 에서 바로 js 파일을 붙여서 테스트 하는 것!

하지만 보통은 html 에서 그냥 dev || qa proxy 를 불러와서 js를 붙여서 테스트를 하는 경우가 많음 (편하니까!)

<br>

public/template.html 이 없는 서비스의 경우는 결국 로컬에서만 돌리는걸 안쓰겠다! 라는 것이다.

다 프록시 서버 불러와서 js 붙여서 로컬 테스트 하는 것

<br>

1. dev or qa 프록시 서버 화면 가져와 띄우기 + 로컬 JS 파일 붙여서 테스트
2. 로컬 template.html 에서 화면 띄우기 + 로컬 JS 파일 테스트

<br>

보통은 로컬만의 템플릿을 테스트하는 경우가 거의 없을 것이다.

프록시에 올라간 내용들이 테스트하기 확실한 부분도 있기도 하니까…?

<br>

추가로 template.html 쓰려면 dev css 경로 박아서 사용하면 되긴 하지만,

그것보다는 바로 dev proxy 붙이는게 더 빠르고 효율적이기 때문에 위처럼 css 를 html에 박아서 쓰는 경우는 없는 것이다.
