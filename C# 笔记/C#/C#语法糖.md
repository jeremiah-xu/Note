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

# linq的Select方法（）
https://docs.microsoft.com/zh-cn/dotnet/api/system.linq.enumerable.select?view=netcore-3.1  
注解
此方法是使用**延迟执行实现的**。 即时返回值是一个对象，该对象存储执行操作所需的所有信息。 此方法表示的查询在枚举对象之前不会执行，方法是直接调用其 GetEnumerator 方法，或者通过 foreach 在 Visual c # 中使用或 For Each 在 Visual Basic 中使用。
selector表示要处理的元素的第一个参数。 第二个参数，用于 selector 表示源序列中该元素的从零开始的索引。 例如，如果元素处于已知顺序，并且你想要对特定索引处的元素执行某些操作，则这会很有用。 如果要检索一个或多个元素的索引，此方法也会很有用。
此投影方法要求转换函数 selector 为源序列中的每个值生成一个值 source 。 如果 selector 返回本身为集合的值，则由使用者手动遍历个子序列。 在这种情况下，你的查询将返回值的单个合并序列可能更好。 若要实现此目的，请使用 SelectMany 方法而不是 Select 。 尽管 SelectMany 的工作方式类似于，但它的不同之处在于， Select 转换函数返回一个集合，然后在 SelectMany 返回之前扩展。

