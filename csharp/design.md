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

> **堅持** 謹慎使用抽象類別，或考慮使用介面。

```csharp
public abstract class Door
{
    public abstract void Open();
    public abstract void Close();
}
```

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

> **堅持** 至少提供一個衍生類別，有助於驗證此抽項類別的設計。

```csharp
public class AutoDoor : Door
{
}
```

#### 結構 \(Struct\)

* 實值類型。
* 具有原子性，邏輯上為單一值。
* 具有常量性。
* 執行個體很小。

> **考慮** 使用結構，當符合以上特性且不會經常 Boxing。

```csharp
public struct RgbColor
{
    public int Red { get; private set; }
    public int Green { get; private set; }
    public int Blue { get; private set; }

    public RgbColor(int red, int green, int blue)
    {
        Red = red;
        Green = green;
        Blue = blue;
    }
}
```

#### 介面 \(Interface\)

可以包含事件、屬性、索引子、方法。

> **堅持** 至少提供一個實作型別，有助於驗證此介面的設計。
>
> **堅持** 使用介面，當結構需要抽象化。

```csharp
public interface IShape
{
    decimal Area { get; }
}

public struct Rectangle : IShape
{
    public decimal Length { get; private set; }
    public decimal Width { get; private set; }
    public decimal Area
    {
        get
        {
            return Length * Width;
        }
    }
}
```

> **考慮** 使用介面，當需要多重繼承。

```csharp
public class Bird : Animal, IFlyable
{
}
```

> **避免** 使用不含成員的介面。

```csharp
public interface IMarker
{
}
```

#### 委派 \(Delegate\)

> **堅持** 使用 `EventHandler<TEventArgs>` 而不是自訂委派，當定義事件處理常式時。
>
> **堅持** 使用 `Func<>`、 `Action<>` 或 `Expression<>` 委派而不是自訂委派，當定義回呼時。

#### 事件 \(Event\)

> **堅持** 引發靜態事件時傳遞 `null` 做為 sender。
>
> **禁止** 引發非靜態事件時傳遞 `null` 做為 sender。
>
> **禁止** 引發事件時傳遞 `null` 做為事件資料參數。應傳遞 `EventArgs.Empty`。

```csharp
Closing(this, EventArgs.Empty);
```



