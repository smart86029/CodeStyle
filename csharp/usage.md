# 用法方針

#### 例外狀況 \(Exception\)

> **堅持** 攔截例外狀況要有相應的處理。

```csharp
// 禁止
catch (ArgumentException ex)
{
}
```

> **堅持** 擲回例外狀況，而非回傳錯誤碼。
>
> **堅持** 盡量使用標準的例外狀況類型。
>
> **堅持** 除了系統錯誤，應盡可能使用一般流程控制而不使用例外狀況，讓使用者可以撰寫不會擲回例外狀況的方法。

```csharp
// Tester-Doer 模式，避免擲回 InvalidOperationException
var scores = new List<int>();
if (scores.Count > 0)
    Console.WriteLine(scores.Max());
```

> **考慮** 擲回例外狀況可能會降低效能。

```csharp
// Try-Parse 模式，避免擲回 ArgumentNullException、FormatException、ArgumentException
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    { 
        // ... 
    }

    public static bool TryParse(string dateTime, out DateTime result)
    {
        // ...
    }
}
```

> **考慮** 重新擲回例外時保留原有的堆疊追蹤。

```csharp
// 建議
catch (ArgumentException ex)
{
    throw;
}

// 若無特別考量，不建議使用
catch (ArgumentException ex)
{
    throw ex;
}
```

> **考慮** 使用例外狀況產生器方法，用來建立相同的例外狀況。

```csharp
public void Execute()
{
    // ...
    throw NewCustomException();
}

// 統一呼叫此方法以建立相同的例外狀況
private CustomException NewCustomException()
{
    return new CustomException("Error")
}
```



