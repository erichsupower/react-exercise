# JSX 使用介紹

- [JSX 使用介紹](#jsx-%e4%bd%bf%e7%94%a8%e4%bb%8b%e7%b4%b9)
  - [在 JSX 中嵌入 Expression](#%e5%9c%a8-jsx-%e4%b8%ad%e5%b5%8c%e5%85%a5-expression)
    - [範例一：](#%e7%af%84%e4%be%8b%e4%b8%80)
    - [範例二：在 JSX 的大括號中可以寫入任何合法的 JavaScript expression。](#%e7%af%84%e4%be%8b%e4%ba%8c%e5%9c%a8-jsx-%e7%9a%84%e5%a4%a7%e6%8b%ac%e8%99%9f%e4%b8%ad%e5%8f%af%e4%bb%a5%e5%af%ab%e5%85%a5%e4%bb%bb%e4%bd%95%e5%90%88%e6%b3%95%e7%9a%84-javascript-expression)
  - [JSX 本身也是 Expression](#jsx-%e6%9c%ac%e8%ba%ab%e4%b9%9f%e6%98%af-expression)
  - [在 JSX 中指定屬性](#%e5%9c%a8-jsx-%e4%b8%ad%e6%8c%87%e5%ae%9a%e5%b1%ac%e6%80%a7)
  - [範列一：使用引號將字串設定為屬性：](#%e7%af%84%e5%88%97%e4%b8%80%e4%bd%bf%e7%94%a8%e5%bc%95%e8%99%9f%e5%b0%87%e5%ad%97%e4%b8%b2%e8%a8%ad%e5%ae%9a%e7%82%ba%e5%b1%ac%e6%80%a7)
  - [範列二：在屬性中使用大括號來嵌入一個 JavaScript expression：](#%e7%af%84%e5%88%97%e4%ba%8c%e5%9c%a8%e5%b1%ac%e6%80%a7%e4%b8%ad%e4%bd%bf%e7%94%a8%e5%a4%a7%e6%8b%ac%e8%99%9f%e4%be%86%e5%b5%8c%e5%85%a5%e4%b8%80%e5%80%8b-javascript-expression)
  - [在 JSX 中指定 Children](#%e5%9c%a8-jsx-%e4%b8%ad%e6%8c%87%e5%ae%9a-children)
  - [JSX 標籤也可以包含 children：](#jsx-%e6%a8%99%e7%b1%a4%e4%b9%9f%e5%8f%af%e4%bb%a5%e5%8c%85%e5%90%ab-children)
  - [JSX 防範注入攻擊](#jsx-%e9%98%b2%e7%af%84%e6%b3%a8%e5%85%a5%e6%94%bb%e6%93%8a)
  - [JSX 表示物件](#jsx-%e8%a1%a8%e7%a4%ba%e7%89%a9%e4%bb%b6)
- [深入了解 JSX](#%e6%b7%b1%e5%85%a5%e4%ba%86%e8%a7%a3-jsx)

---

## 在 JSX 中嵌入 Expression

### 範例一：

宣告一個 name 的變數，並在 JSX 中透過將其名稱包在大括號中使用：

```js
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

### 範例二：在 JSX 的大括號中可以寫入任何合法的 JavaScript expression。

嵌入呼叫 JavaScript function (formatName(user)) 的回傳值到一個 \<h1> element 中。

```js
function formatName(user) {
  return user.firstName+ ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

---

## JSX 本身也是 Expression

JSX expressions 會先編譯為一般的 JavaScript function，呼叫並回傳 JavaScript 物件。
這表示你也可以在 if 跟 for 迴圈中使用 JSX，將其指定到一個變數，使用 JSX 作為參數並由 function 中回傳。

```js
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

---

## 在 JSX 中指定屬性

## 範列一：使用引號將字串設定為屬性：

```js
const element = <div tabIndex="0"></div>;
```

## 範列二：在屬性中使用大括號來嵌入一個 JavaScript expression：

```js
const element = <img src={user.avatarUrl}></img>;
```

> **不要在嵌入 JavaScript expression 作為屬性的時候同時使用引號或是大括號。**
> 你應該要在使用字串屬性的時候使用**引號**，使用 expressions 的時候使用**大括號**，
> 但不要同時使用。

---

## 在 JSX 中指定 Children

就像是在 XML 之中，如果一個標籤是空白的，你可以用 /> 立刻關閉這個標籤：

```js
const element = <img src={user.avatarUrl} />;
```

---

## JSX 標籤也可以包含 children：

```js
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

---

## JSX 防範注入攻擊

在 JSX 之中可以安全的直接嵌入使用者輸入：

```js
const title = response.potentiallyMaliciousInput;
// 這是安全的：
const element = <h1>{title}</h1>;
```

> React DOM 預設會在 render 之前 escape 所有嵌入在 JSX 中的變數。
> 這保證你永遠不會不小心注入任何不是直接寫在你的應用程式中的東西。
> 所有變數都會在 render 之前轉為字串，這可以避免 XSS（跨網站指令碼）攻擊。

---

## JSX 表示物件

Babel 將 JSX 編譯呼叫 `React.createElement()` 的程式。

下面這兩個例子完全相同：

```js
const element = (
  <h1 className="greeting">
    Hello, World!
  </h1>
);
```
```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, World!'
);
```

`React.createElement()` 會進行一些檢查以幫助你寫出沒有 bug 的程式，但基本上它會產生類似下面的物件：

```js
// 注意：這是簡化過的結構
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

這種物件被稱呼為「React element」。你可以想像他們描述的是你想要在螢幕上看到的東西，React 會讀取這些物件並用這些描述來產生 DOM 並保持他們在最新狀態。


# 深入了解 JSX

[[ 傳送門 ↗ ]](https://zh-hant.reactjs.org/docs/jsx-in-depth.html#user-defined-components-must-be-capitalized)