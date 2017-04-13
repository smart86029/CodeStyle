# C\#命名方針

#### 帕斯卡命名法 \(Pascal Case\)

每一個單字的第一個字母都採用大寫字母，適用於所有公用成員 \(`public`、`protected`、`internal`\)。

> 例如: StringBuilder、UserName

* 命名空間 \(Namespace\)
* 類別 \(Class\)
* 結構 \(Struct\)
* 介面 \(Interface\)
* 委派 \(Delegate\)
* 事件 \(Event\)
* 列舉 \(Enum\)，及列舉的項目 
* 屬性 \(Property\)
* 方法 \(Method\)
* 常數 \(Const\)

#### 駝峰式命名法 \(Camel Case\)

第一個單字以小寫字母開始，其餘單字的首字母大寫。

> 例如: stringBuilder、userName

* 欄位 \(Field\)
* 變數 \(Variable\)
* 參數 \(Parameter\)

#### 縮略字 \(Acronym\)

兩個字母的縮略字使用全部大寫，三個字母以上的縮略字使用帕斯卡命名法。

> 例如: DB、UI、Sql、Html
>
> 例外: Id \(identification 的縮寫，非縮略字\)

#### 複合詞彙和一般詞彙

> **避免 **將一般詞彙當成複合詞彙

| Do | Do Not | Do | Do Not |
| :--- | :--- | :--- | :--- |
| Callback | CallBack | UserName | Username |
| Email | EMail | WhiteSpace | Whitespace |
| Endpoint | EndPoint |  |  |
| Hashtable | HashTable |  |  |
| Metadata | MetaData |  |  |
| Namespace | NameSpace |  |  |
| Placeholder | PlaceHolder |  |  |



