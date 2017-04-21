# 命名方針

#### 帕斯卡命名法 \(Pascal Case\)

每一個單字的第一個字母都採用大寫字母，適用於所有公用成員 \(`public`、`protected`、`internal`\)。

```csharp
public string UserName { get; set; }
```

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

```csharp
var userName = "Admin";
```

* 欄位 \(Field\)
* 變數 \(Variable\)
* 參數 \(Parameter\)

#### 匈牙利命名法 \(Hungarian Notation\)

不使用。

#### 縮略字 \(Acronym\)

兩個字母的縮略字使用全部大寫，三個字母以上的縮略字使用帕斯卡命名法。

```csharp
public class DBUtility
{
    public int ContextId { get; set; }  // 例外，identification 的縮寫，非縮略字

    public void ExecuteSql(string sql)
    {
    }
}
```

#### 複合詞彙和一般詞彙

> **避免** 搞混一般詞彙和複合詞彙。

| Do | Do Not | Do | Do Not |
| :--- | :--- | :--- | :--- |
| Callback | CallBack | UserName | Username |
| Email | EMail | WhiteSpace | Whitespace |
| Endpoint | EndPoint |  |  |
| Hashtable | HashTable |  |  |
| Metadata | MetaData |  |  |
| Namespace | NameSpace |  |  |
| Placeholder | PlaceHolder |  |  |

#### 一般命名慣例

> **堅持** 使用有意義的名稱。

```csharp
for (var i = 0; i < 5; i++)  // 例外，迴圈變數 i
    result += i;

Customers.Find(c => c.Name == "Anne");  // 例外，匿名函式的輸入參數 c
```

> **堅持** 可讀性優先於簡潔性。

```csharp
public bool CanScrollHorizontally { get; set; }  // 較優
public bool ScrollableX { get; set; }
```

> **堅持** 使用正確的拼寫以及慣用詞彙。參考 [CA1726](https://msdn.microsoft.com/zh-tw/library/ms182258.aspx)。

```csharp
public bool IsWriteable { get; set; }  // 應修正為 IsWritable

public void SignOn(string account, string password)  // 應修正為 SignIn
{
}
```

> **堅持** 使用正確的單複數。

```csharp
var car = new Car();
var carList = new List<Car>();  // 應修正為 cars
```

> **堅持** 使用正確的相對詞。

```csharp
public DateTime OpenTime { get; set; }
public DateTime StopTime { get; set; }  // 應修正為 CloseTime
```

> **堅持** 使用相同的詞彙表達一樣的概念。

```csharp
public Book GetBook(int id)
{
}

public Magazine RetrieveMagazine(int id)  // 應修正為 GetMagazine
{
}
```

> **避免** 使用縮寫或不常用的縮略字。

```csharp
public void QryData()  // 應修正為 QueryData
{
}
```

> **禁止** 使用底線、 連字號或任何其他非英數字元。

```csharp
[TestMethod]
public void GetName_ReturnName_WhenUserIsNotNull()  // 例外，單元測試的方法
{
}
```

#### 識別項命名慣例

##### 類別、結構

> **堅持** 使用名詞或名詞片語。
>
> **考慮** 使用基底類別的名稱做為後置詞。

```csharp
public class UserService : Service
{
}
```

> **避免** 使用 Base 做為基底類別的後置詞。

```csharp
public abstract class ServiceBase  // 應修正為 Service
{
}
```

> **禁止** 使用前置詞。

```csharp
public class CUser  // 應修正為 User
{
}
```

##### 介面

> **堅持** 使用形容詞片語、名詞或名詞片語。
>
> **堅持** 使用 "I" 做為前置詞。

```csharp
public interface IService
{
}
```

##### 泛型型別參數 \(Generic type parameter\)

> **堅持** 使用 T 做為前置詞。

```csharp
public TEntity ToEntity<TEntity>(string json)
{
}
```

> **考慮** 使用 T 做為型別參數名稱，若單一字母已經能表達且增加描述性名詞不會增加價值。

```csharp
public delegate bool Predicate<T>(T item);
```

##### 衍生型別、實作型別

> **堅持** 使用 Attribute 做為後置詞，若基底型別為 `System.Attribute`。

```csharp
public class AuthorizedAttribute : Attribute
{
}
```

> **堅持** 使用 EventArgs 做為後置詞，若基底型別為 `System.EventArgs`。

```csharp
public class MouseEventArgs : EventArgs
{
}
```

> **堅持** 使用 Exception 做為後置詞，若基底型別為 `System.Exception`。

```csharp
public class BusinessException : Exception
{
}
```

> **堅持** 使用 Dictionary 做為後置詞，若基底型別為 `IDictionary` 或 `IDictionary<TKey, TValue>`。

```csharp
public class UserDictionary : IDictionary
{
}
```

> **堅持** 使用 Collection 做為後置詞，若基底型別為 `IEnumerable`、`ICollection`、`IList`、`IEnumerable<T>`、`ICollection<T>`、`IList<T>`。

```csharp
public class UserCollection : ICollection
{
}
```

> **堅持** 使用 Stream 做為後置詞，若基底型別為 `System.IO.Stream`。

```csharp
public class FileStream : Stream
{
}
```

> **堅持** 使用 Permission 做為後置詞，若基底型別為 `IPermission`。

```csharp
public class SoundPermission : IPermission
{
}
```

##### 委派

> **堅持** 使用 EventHandler 做為後置詞，若為事件中所使用的委派，並使用 sender、e 為事件處理常式參數名稱。
>
> **堅持** 使用 Callback 做為後置詞，若不是事件處理常式。
>
> **禁止** 使用 Delegate 做為後置詞。

```csharp
public delegate void MouseEventHandler(object sender, MouseEventArgs e);
public delegate bool WorkCompletedCallback(int count);
```

##### 事件

> **堅持** 使用動詞或動詞片語。
>
> **堅持** 使用動詞時態來表示引發事件時的時間，現在式為之前的概念，過去式為之後的概念。
>
> **禁止** 使用 Before 或 After 做為前置詞。

```csharp
public event EventHandler Closing;
```

##### 列舉

> **堅持** 使用單數名詞。
>
> **堅持** 使用複數名詞，若為旗標列舉。
>
> **禁止** 使用型別名稱做為列舉的項目的前置詞。
>
> **禁止** 使用 Enum、Flag、Flags 做為後置詞。

```csharp
public enum MainDish
{
    Beef = 0,
    Pork = 5,
}

[Flags]
public enum SideDishes
{
    Potato = 0,
    Tomato = 1,
    Bacon = 2,
    Corn = 4
}
```

##### 屬性

> **堅持** 使用名詞、名詞片語或形容詞。
>
> **堅持** 使用肯定型 Be 動詞或助動詞來表示布林值。
>
> **考慮** 使用與其型別相同的名稱。
>
> **禁止** 使用的名稱和其中有 Get 的方法名稱相符。

```csharp
public MainDish MainDish { get; set; }
public bool HasNotDessert { get; set; }  // 應修正為 HasDessert

public GetMainDish()  // 應修正 MainDish 名稱或修正 GetMainDish 名稱
{
}
```

##### 方法

> **堅持** 使用動詞或動詞片語。

```csharp
public void SaveChanges()
{
}
```

##### 欄位

> **堅持** 使用名詞、名詞片語或形容詞。
>
> **禁止** 使用前置詞。

```csharp
public class Address
{
    private string _postCode;  // 應修正為 postCode
}
```

##### 參數

> **堅持** 使用描述性的名詞、名詞片語或形容詞。
>
> **考慮** 根據參數的意義，而不是參數的型別。

```csharp
public List<Person> GetChildren(Person parent)
{
}
```

###### 

###### 參考

* [命名方針](https://msdn.microsoft.com/zh-TW/library/ms229002%28v=vs.110%29.aspx)
* [命名警告](https://msdn.microsoft.com/zh-tw/library/ms182232.aspx)
* [StyleCop](http://stylecop.soyuz5.com/Naming Rules.html)



