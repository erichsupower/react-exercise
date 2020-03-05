# React 學習
[教學來源：React 中文教學](https://zh-hant.reactjs.org/docs/add-react-to-a-website.html)

---

## 使用 JSX

### 方法一：

將下列這個 `<script>` 標籤加入網頁：

```js
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

在任何 `<script>` 標籤裡加上 `type="text/babel"` 的 attribute 後使用 JSX 語法。

### 方法二：使用 JSX Preprocessor [[↗]](https://zh-hant.reactjs.org/docs/add-react-to-a-website.html#optional-try-react-with-jsx)

第一步： 執行 `npm init -y`

第二步： 執行 `npm install babel-cli@6 babel-preset-react-app@3`

第三步： 建立一個名為 *src* 的文件夾，然後執行這個終端指令：

`npx babel --watch src --out-dir . --presets react-app/prod`

## 受歡迎的 React toolchain [[↗]](https://zh-hant.reactjs.org/docs/create-a-new-react-app.html)

- 如果你正在學習 React 或建立全新的 single-page 應用程式，請使用 Create React App。
- 如果你正在建立一個使用 Node.js 的 server-rendered 網頁，請使用 Next.js。
- 如果你正在建立一個靜態內容的網頁，請使用 Gatsby。
- 如果你正在建立一個 component 函式庫或與現存程式碼倉庫進行接軌，請使用更靈活的 Toolchain。

---

## CDN 連結

以下的版本只適用於開發環境，並不適合用於線上環境：

```html
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
```

以下為已壓縮和最佳化的版本：

```html
<script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
```

更改版本號碼 16 來載入指定版本的 react 和 react-dom。

---

## React Developer Tools [[↗]](https://reactjs.org/blog/2015/09/02/new-react-developer-tools.html#installation)

![image](https://reactjs.org/devtools-full-f57ae67cfaa1fe76880654e2eddbf71f.gif)

---