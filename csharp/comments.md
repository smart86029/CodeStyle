# 註解方針

#### 單行註解 \(Single Line Comments\)

> **堅持** 以好的命名與架構表達語意，而非以大量註解說明。
>
> **考慮** 使用註解說明演算法內容、商務邏輯、設計考量等。

```csharp
// 用於說明程式碼
// 避免大量註解反而造成閱讀困難
```

> **考慮** 使用 `HACK`、`TODO`、`UNDONE` 等語彙基元建立工作清單。

```csharp
// HACK: 重構方法
// TODO: 效能調教
// UNDONE: 參數檢核
```

> **禁止** 使用排版符號。

```csharp
// ----------
// 禁止使用
// ----------
```

#### 分隔註解 \(Delimited Comments\)

不使用。

```csharp
/* 不使用此種註解方式 */
```

#### XML 文件註解 \(XML Documentation Comments\)

> **堅持** 公用成員 \(`public`、`protected`、`internal`\) 必須添加文件註解。
>
> **堅持 **文件註解必須包含 `<summary>`。

```csharp
/// <summary>
/// 使用者服務。
/// </summary>
public class UserService
{
}
```

> **堅持** 泛型型別參數必須添加文件註解。
>
> **堅持** 參數必須添加文件註解。
>
> **堅持** 傳回值必須添加文件註解。
>
> **堅持** 例外狀況必須添加文件註解。

```csharp
/// <summary>
/// 取得模型。
/// </summary>
/// <typeparam name="T">模型類別。</typeparam>
/// <param name="id">ID。</param>
/// <returns>模型的執行個體。</returns>
/// <exception cref="ArgumentException"><paramref name="id"/> 不合法。</exception>
public T GetModel<T>(int id)
{
    if (id <= 0)
        throw new ArgumentException("不合法的 ID", nameof(id));

    return default(T);
}
```

> **堅持** 列舉的項目必須添加文件註解。

```csharp
/// <summary>
/// 性別。
/// </summary>
public enum Sex
{
    /// <summary>
    /// 未知項。
    /// </summary>
    NotKnown = 0,

    /// <summary>
    /// 男性。
    /// </summary>
    Male = 1,

    /// <summary>
    /// 女性。
    /// </summary>
    Female = 2,

    /// <summary>
    /// 未規定項。
    /// </summary>
    NotApplicable = 9
}
```

> **堅持** 屬性的值必須添加文件註解。

```csharp
/// <summary>
/// 取得或設定使用者名稱。
/// </summary>
/// <value>使用者名稱。</value>
public string UserName { get; set; }
```

> **考慮** 使用其他的標記添加文件註解。參考 [MSDN](https://msdn.microsoft.com/zh-tw/library/5ast78ax.aspx)。



###### 參考

* [XML 文件註解](https://msdn.microsoft.com/zh-tw/library/b2s063f7.aspx)
* [StyleCop](http://stylecop.soyuz5.com/Documentation%20Rules.html)



