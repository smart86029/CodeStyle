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

> **禁止** 不必要的空行。

```csharp
public class Person
{  // 錯誤，左括號後不可接空行
    
    public string FirstName { get; set; }
    
    
    public string LastName { get; set; }  // 錯誤，空行以一行為限

}  // 錯誤，右括號前不可接空行
```



