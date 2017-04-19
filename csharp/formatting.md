# 格式方針

#### 排版 \(Layout\)

> **堅持** 在新行加入大括號。

```csharp
public class User {  // 錯誤
}

public class Role
{
}
```

> **堅持** 在成員之間加入空行，除了欄位之外。

```csharp
public string Account { get; set; }

public string Password { get; set; }
```

> **堅持** 在 using 指示詞和命名空間宣告之間加入空行。

```csharp
using System;

namespace WebApplication.Model
{
}
```

> **考慮** 在不同邏輯區塊之間加入空行。

```csharp
public int GetChosonOne()
{
    // 宣告區塊
    var min = 0;
    var max = 10000;

    // 邏輯區塊一
    ...

    // 邏輯區塊二
    ...

    return result;
}
```

> **考慮** 單行陳述式加入大括號。

```csharp
if (age > 19)
{
    if (isStudent)
        Notify("兵役緩徵");
}
else
{
    Notify("兵役體檢");  // 若省略大括號，else 會跟著最近的 if
}
```

> **禁止** 陳述式或含大括號的成員共用同一行。

```csharp
public string Version { get; set; }  // 例外，短的屬性

public User GetUser(int id)
{
    if (id <= 0) throw new ArgumentException();  // 錯誤

    return new User();
}
```

> **禁止** 相連語句之間的空行，包含 `if-else`、`try-catch`、`do-while` 等。

```csharp
if (hasPermission)
{
}

else  // 錯誤
{
}
```

> **禁止** 不必要的空行。

```csharp
public class Person
{  // 錯誤，左括號後不可接空行

    public string FirstName { get; set; }


    public string LastName { get; set; }  // 錯誤，空行以一行為限

}  // 錯誤，右括號前不可接空行
```

#### 空格 \(Spacing\)

> **堅持** Tab 設為 4 spaces。

```csharp
namespace Sample.Data
{
    public class Repository
    {
    }
}
```

> **堅持** 關鍵字應在正確位置加入空格，以下關鍵字通常在之後加一空格，包含 `catch`、`fixed`、`for`、`foreach`、`from`、`group`、`if`、`in`、`into`、`join`、`let`、`lock`、`new`、`orderby`、`return`、`select`、`stackalloc`、`switch`、`throw`、`using`、`var`、`where`、`while`、`yield` 等；以下關鍵字後不加空格，包含 `checked`、`default`、`nameof`、`sizeof`、`typeof`、`unchecked` 等。

```csharp
var fibonacciNumbers = new[] { 1, 1, 2, 3, 5, 8, 13 }  // 例外，初始化陣列

if (user == null)
    throw new ArgumentNullException(nameof(user));
```

> **堅持** 在正確位置加入空格，以下在之後加一空格 \(句末除外\)，包含 `,`、`;`、`{`、`//`、`///` 等；在運算子前後各加一空格；以下不加空格，包含 `++`、`--`、`[`、`]`、`(`、`)`、`<`、`>` 等。

```csharp
/// <summary>
/// 計算
/// </summary>
[Conditional("DEBUG")]
public void Calculate<T>()
{
    var result = 0;
    var numbers = new List<T> { 1, 2, 3 };

    // 單行註解
    for (var i = 0; i < 10; i++)
        result += i;
}
```

> **禁止** 多個空格，縮排除外。

```csharp
private int length = 4;
private int width  = 3;  // 錯誤
```

#### 排序 \(Ordering\)

> **堅持** 以下列順序組織成員。

* 欄位 \(Fields\)
* 建構子 \(Constructors\)
* 解構子 \(Destructors\)
* 委派 \(Delegates\)
* 事件 \(Events\)
* 列舉 \(Enums\)
* 介面 \(Interfaces\)
* 屬性 \(Properties\)
* 索引子 \(Indexers\)
* 方法 \(Methods\)
* 結構 \(Structs\)
* 類別 \(Classes\)

> **堅持** 以下列順序組織存取修飾詞。

* `public`
* `internal`
* `protected internal`
* `protected`
* `private`

> **堅持** 以存取修飾詞、static 修飾詞、其他關鍵字的順序宣告成員，並以此順序進行排序。

```csharp
private static readonly int index = 0;
```

> **堅持** `using` 指示詞優先放置 `System` 命名空間，並以命名空間字母正向排序。
>
> **堅持** `using` 靜態指示詞放置在 `using` 指示詞之後，並以命名空間字母正向排序。
>
> **堅持** `using` 別名指示詞放置在 `using` 靜態指示詞之後，並以別名字母正向排序。

```csharp
using System;
using System.Linq;
using Autofac;
using static System.Console;
using Excel = Microsoft.Office.Interop.Excel;
```

> **堅持** 靜態成員放置在非靜態成員之前。

```csharp
public static int Version { get; set; }

public string Name { get; set; }
```

> **堅持** 常數欄位放置在一般欄位之前。
>
> **堅持** 唯讀欄位放置在一般欄位之前。

```csharp
private const int Size = 10;
private readonly int startAt = 0;
private int count;
```

> **堅持** 屬性 `get` 存取子放在 `set` 存取子之前。

```csharp
public int Age { get; set; }
```

> **堅持** 事件 `add` 存取子放在 `remove` 存取子之前。

```csharp
public event EventHandler Closing
{
    add { this.closing += value }
    remove { this.closing -= value }
}
```

#### 可讀性 \(Readability\)

> **堅持** 一行一陳述式，過長的陳述式，在 `.` 之前、`,` 之後或運算子之後換行。

```csharp
public List<string> GetNames(int age, int height, int weight,
    int chest, int waist, int hips)
{
    var result = People
        .Where(p => p.Age < age)
        .Select(p => p.Name);

    return result;
}
```

> **堅持**

> **堅持** 使用關鍵字宣告型別。

```csharp
private Int32 count;  // 應改為 int
```

| **關鍵字** | **型別** | **關鍵字** | **型別** |
| :--- | :--- | :--- | :--- |
| sbyte | System.SByte | float | System.Single |
| byte | System.Byte | double | System.Double |
| short | System.Int16 | decimal | System.Decimal |
| ushort | System.UInt16 | bool | System.Boolean |
| int | System.Int32 | char | System.Char |
| uint | System.UInt32 | string | System.String |
| long | System.Int64 | object | System.Object |
| ulong | System.UInt64 |  | 　 |

> **堅持** 使用 `T?` 表達  `System.Nullable<T>`。

```csharp
private int? version;
```

> **考慮** 使用 var 宣告區域變數。

```csharp
var count = 0;
var sql = new StringBuilder();
```

> **避免** 使用 `#region`。

在大多數情況之下，將過長的方法擷取成較小的方法，將過長的程式碼拆分到新檔案，並不需要使用 `#region`，使用 `#region` 會使程式碼多一層無意義的層級，大綱展開與摺疊需要額外的動作。

