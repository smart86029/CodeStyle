# 格式方針

#### 排版 \(Layout\) {#排版-layout}

> **堅持** 每個區塊、清單項目、表格元素都置於新行。

```html
<ul>
  <li>Apple</li>
  <li>Banana</li>
</ul>

<table>
  <tbody>
    <tr>
      <td>姓名</td>
      <td>性別</td>
    </tr>
  </tbody>
</table>
```

> **考慮 **在不同邏輯區塊之間加入空行，空行以一行為限。

```html
<div id="sidebar">
</div>

<div id="main">
</div>
```

#### 空格 \(Spacing\)

> **堅持 **Tab 設為 2 spaces。

```html
<html>
  <head></head>
  <body></body>
<html>
```

> **禁止** 屬性前後的空格。

```html
<a href = "#home">首頁</a>  <!-- 錯誤 -->
<a href="#about">關於</a>
```

#### 排序 \(Ordering\) {#排序-ordering}

> **考慮** 以下列順序組織屬性。

* `type`、`for`、`href`、`src`
* `class`
* `id`
* `name`
* `value`、`content`
* `title`、`alt`、`rel`
* `checked`、`selected` 等其餘項目

#### 可維護性 \(Maintainability\) {#可維護性-maintainability}

> **堅持** 關閉所有標籤。

```html
<p>Do not
<p>Do</p>
```

> **堅持** 自閉標籤省略結束標記。

```html
<br>
<input type="hidden" value="1">
```

> **堅持** 使用雙引號 `""` 框住屬性值。

```html
<a href="#"></a>
```

> **堅持** 使用小寫宣告標籤。

```html
<!DOCTYPE html>  <!-- 例外 -->

<A HREF="#"></A>  <!-- 錯誤 -->
```

> **堅持** 布林屬性省略屬性值。

```html
<input type="text" disabled>
```

> **堅持** 自定義屬性使用 `data-` 前綴詞。

```html
<input type="text" data-color="red">
```

###### 參考 {#參考}

* [w3schools.com](https://www.w3schools.com/html/html5_syntax.asp)



