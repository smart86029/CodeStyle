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

> **堅持** 在正確位置加入空格，以下在之後加一空格 \(句末除外\)，包含 `,`、`;`、`{`、`//`、`///` 等；在運算子前後各加一空格；以下不加空格，包含 ++、--、\[、\]、\(、\)、&lt;、&gt; 等。

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

#### 排序 \(Ordering\)



