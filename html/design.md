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

> **堅持** 使用 &lt;title&gt; 標籤宣告標題。

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

> **考慮** 在 &lt;head&gt; 引入所有需要的 `CSS` 樣式表，無須宣告 `type="text/css"`，但必須宣告 `rel="stylesheet"`。

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



