# System.Globalization.CultureInfo

常用于多语言版本 的信息，和 Resouce 文件配合使用。
```csharp
Thread.CurrentThread.CurrentUICulture = new System.Globalization.CultureInfo("zh-CHS");
```

# GetTamplateChird()

- 只要有Export特性暴露出来，就能获取得到。
  * 和接口环境

# System.Threading.Mutex

System.Threading.Mutex:一台电脑上面只有一个进程实例在运行，利用Mutex互斥量可以实现了这个功能费

# where T : class含义

.NET支持的类型参数约束有以下五种：
```cs
where T : struct                               | T必须是一个结构类型  
where T : class                                | T必须是一个Class类型  
where T : new()                               | T必须要有一个无参构造函数  
where T : NameOfBaseClass          | T必须继承名为NameOfBaseClass的类  
where T : NameOfInterface             | T必须实现名为NameOfInterface的接口  
```
# System.Lazy\<TEntity\>

提供对延迟初始化的支持

# 使用C＃7，您现在可以使用“ 丢弃”

_ 是上下文关键字  
我们正在创建一个虚拟变量，以后将不会使用它或将其丢弃。

tips：  
与 int _ = 0; 不同。  
该处是一个变量。

