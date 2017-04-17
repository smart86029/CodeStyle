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

> **禁止** 陳述式或含大括號的成員共用同一行。

```csharp
public string Version { get; set; }  // 例外，短的屬性

public User GetUser(int id)
{
    if (id <= 0) throw new ArgumentException();  // 錯誤
    
    return new User();
}
```



