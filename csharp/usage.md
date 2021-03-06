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

#### 集合 \(Collections\)

> **堅持** 盡量使用集合而非陣列。
>
> **堅持** 使用位元組陣列。

```csharp
void ToInt32(byte[] value, int startIndex)

// 錯誤
void ToInt32(ICollection<byte> value, int startIndex)
```

> **堅持** 傳回空集合，而非 `null`。

```csharp
if (dataTable.Rows == 0)
    return new List<int>();
```

#### 參數 \(Parameter\)

> **堅持** 移除不使用的參數。

```csharp
// 移除 name
public decimal GetSum(decimal amount, int count, string name)
{
    return amount * count;
}
```

> **避免** 使用選擇性引數 \(optional arguments\)。

```csharp
// 使用多載
public decimal GetSum(decimal amount, int count)
{
    // 沒有折扣的邏輯
}

public decimal GetSum(decimal amount, int count, decimal discount)
{
    // 有折扣的邏輯
}
```

參考

* [用法方針](https://msdn.microsoft.com/zh-tw/library/ms229035%28v=vs.110%29.aspx)



