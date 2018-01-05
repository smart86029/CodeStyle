# 設計方針

#### 一般設計原則

> **堅持** 使用 HTML5。

```html
<!DOCTYPE html>
```

> **堅持** 使用 UTF-8 編碼。

```html
<meta charset="UTF-8">
```

> **堅持** 使用 `<title>` 標籤宣告標題。

```html
<title>測試網站</title>
```

> **堅持** 確保根目錄 favicon.ico 存在，或指定 icon 的地址。

```html
<link href="/source/other/favicon.ico" rel="shortcut icon" >
```

> **考慮** 宣告 IE 相容模式。

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

> **考慮** 宣告裝置大小，以支持行動裝置。

```html
<meta name="viewport" content="width=device-width; initial-scale=1.0;">
```

> **考慮** 在 `<html>` 標籤宣告 `lang` 屬性。

```html
<html lang="zh-TW">
```

> **考慮** 在 `<head>` 引入所有需要的 `CSS` 樣式表，無須宣告 `type="text/css"`，但必須宣告 `rel="stylesheet"`。

```html
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
<link href="/css/style.css" rel="stylesheet">
```

> **考慮** 將 JavaScript 放在頁面最下方，且無須宣告 `type="text/javascript"`。

```html
<body>
  <!-- 其餘項目 -->
  <script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
</body>
```

#### 表單

> **堅持** 將 `<label>` 標籤與 `<input>` 標籤關聯。

```html
<label for="password">密碼</label>
<input type="password" id="password">

<label>
  <input type="checkbox"> 記住我
</label>
```

> **堅持** 在 `<button>` 標籤宣告 `type` 屬性。

```html
<button type="submit">送出</button>
<button type="button">取消</button>
```

> **避免** 在 `<button>` 標籤宣告 `name` 屬性。

```html
<!-- 不建議使用 -->
<button type="button" name="button-test">測試</button>
```

#### 圖片

> **堅持** 宣告 `alt` 屬性，提高載入失敗後的使用者體驗。

```html
<img src="/images/avatar.jpg" alt="大頭貼">
```

> **禁止** 宣告 `src` 屬性為空，避免部分瀏覽器重新載入頁面。

```html
<!-- 錯誤 -->
<img src="">
```



