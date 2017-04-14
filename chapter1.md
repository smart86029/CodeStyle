# C\#命名方針

#### 帕斯卡命名法 \(Pascal Case\)

每一個單字的第一個字母都採用大寫字母，適用於所有公用成員 \(`public`、`protected`、`internal`\)。

> **例如** StringBuilder、UserName。

* 命名空間 \(Namespace\)
* 類別 \(Class\)
* 結構 \(Struct\)
* 介面 \(Interface\)
* 委派 \(Delegate\)
* 事件 \(Event\)
* 列舉 \(Enum\)，及列舉的項目 
* 屬性 \(Property\)
* 方法 \(Method\)
* 常數 \(Constant\)

#### 駝峰式命名法 \(Camel Case\)

第一個單字以小寫字母開始，其餘單字的首字母大寫。

> **例如** stringBuilder、userName。

* 欄位 \(Field\)
* 變數 \(Variable\)
* 參數 \(Parameter\)

#### 縮略字 \(Acronym\)

兩個字母的縮略字使用全部大寫，三個字母以上的縮略字使用帕斯卡命名法。

> **例如** DB、UI、Sql、Html。
>
> **例外** Id \(identification 的縮寫，非縮略字\)。

#### 複合詞彙和一般詞彙

> **避免 **搞混一般詞彙和複合詞彙。

| Do | Do Not | Do | Do Not |
| :--- | :--- | :--- | :--- |
| Callback | CallBack | UserName | Username |
| Email | EMail | WhiteSpace | Whitespace |
| Endpoint | EndPoint |  |  |
| Hashtable | HashTable |  |  |
| Metadata | MetaData |  |  |
| Namespace | NameSpace |  |  |
| Placeholder | PlaceHolder |  |   |

#### 一般命名慣例

使用有意義的名稱。

> **例外** for 迴圈中用來計數的迴圈變數、匿名函式的輸入參數。

```csharp
for (var i = 0; i < 5; i++)
    result += i;

Customers.Find(c => c.Name == "Anne");
```

可讀性優先於簡潔性。

> **例如** CanScrollHorizontally 優於 ScrollableX。

使用正確的拼寫以及慣用詞彙。參考 [CA1726](https://msdn.microsoft.com/zh-tw/library/ms182258.aspx)。

> **例如** Writable 而非 Writeable、SignIn 而非 SignOn。

使用正確的單複數。

```csharp
var car = new Car();
var cars = new List<Car>();
```

使用正確的大小寫。

使用正確的相對詞。

> **例如** OpenTime 和 CloseTime 而非 OpenTime 和 StopTime。

使用相同的詞彙表達一樣的概念。

```csharp
public Book GetBook(int id)
{
}

public Magazine RetrieveMagazine(int id)  // 應修正為 GetMagazine
{
}
```

禁止使用底線、 連字號或任何其他非英數字元。

> **例外** 單元測試的方法。

```csharp
[TestMethod]
public void GetName_ReturnName_WhenUserIsNotNull()
{
}
```

禁止使用匈牙利命名法。

避免使用縮寫或不常用的縮略字。

> **例如** 使用 QueryData 而非 QryData。

#### 識別項命名慣例

類別、結構。

> **堅持** 使用名詞或名詞片語。

> **考慮** 使用基底類別的名稱做為後置詞。

```csharp
public class UserService : Service
{
}
```

> **禁止** 使用前置詞。

```csharp
public class CUser  // 應修正為 User
{
}
```

介面。

> **堅持** 使用形容詞片語、名詞或名詞片語。

> **堅持** 使用 "I" 做為前置詞。

```csharp
public interface IService
{
}
```

泛型型別參數。

> **堅持** 使用 T 做為前置詞。

```csharp
public interface ISessionChannel<TSession> where TSession : ISession{
    TSession Session { get; }
}
```

> **考慮** 使用 T 做為型別參數名稱，若單一字母已經能表達且增加描述性名詞不會增加價值。

```csharp
public delegate bool Predicate<T>(T item);
```



