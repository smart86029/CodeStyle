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

#### 列舉 \(Enum\)

> **堅持** 提供 `0` 做為預設值，若為旗標列舉，命名為 None。
>
> **考慮** 使用 `System.Int32` 做為列舉的基礎型別。

```csharp
public enum MainDish
{
    Beef = 0,
    Pork = 5,
}

[Flags]
public enum SideDishes
{
    None = 0,
    Tomato = 1,
    Bacon = 2,
    Corn = 4
}
```

> **避免** 使用只有一個選項的列舉。

#### 屬性 \(Property\)

> **堅持** 提供合理的預設值。

```csharp
public int Year { get; set; } = 1970;
```

> **考慮** 使用自動實作屬性，若不需要自訂存取子。

```csharp
public Name { get; set; }
```

> **避免** `get` 存取子擲回例外狀況。
>
> **禁止** 只提供 `set` 存取子，或 `set` 存取子比 `get` 存取子有更大的存取範圍。

```csharp
public Name { set; }  // 錯誤
public Age { protected get; set; }  // 錯誤
```

#### 索引子 \(Indexer\)

> **考慮** 提供索引子，若型別表示項目的集合。

```csharp
public class MyCollection<T>
{
    // 宣告索引子
}
```

> **避免** 使用多個參數的索引子。

#### 方法 \(Method\)

> **禁止** 多載擴充方法。

#### 欄位 \(Field\)

> **堅持** 宣告欄位為 `private`，除了常數和靜態唯讀欄位。

```csharp
public const int MaxLength = 10;
private string name;
```

#### 參數 \(Parameter\)

> **考慮** 使用 `params` 關鍵字，若有不定數目參數。
>
> **避免** 使用 `out` 或 `ref` 參數。



