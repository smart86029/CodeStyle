# 設計方針

#### 類別 \(Class\)

##### 靜態類別

只包含靜態成員的類別，且不能具現化 \(Instantiated\)，但可以包含靜態建構函式，通常用於定義擴充功能或工具性方法。

> **堅持** 謹慎使用靜態類別。

```csharp
public static class LogUtility
{
    public static void Error(string message)
    {
    }
}
```

##### 抽象類別

不能具現化，僅做為基底類別供其他類別繼承。

> **堅持** 將建構子宣告成 `protected` 或 `internal`。

```csharp
public abstract class Door
{
    protected Door()
    {
    }
}

public abstract class Window
{
    // 用來限制只有在同組件內才能繼承此類別
    internal Window()
    {
    }
}
```



