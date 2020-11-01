# xmal笔记-control template

## System.Globalization.CultureInfo

常用于多语言版本 的信息，和 Resouce 文件配合使用。

```csharp
Thread.CurrentThread.CurrentUICulture = new System.Globalization.CultureInfo("zh-CHS");
```

## System.Threading.Mutex

System.Threading.Mutex:一台电脑上面只有一个进程实例在运行，利用Mutex互斥量可以实现了这个功能费

## where T : class含义

.NET支持的类型参数约束有以下五种：

where T : struct                               | T必须是一个结构类型  
where T : class                                | T必须是一个Class类型  
where T : new()                               | T必须要有一个无参构造函数  
where T : NameOfBaseClass          | T必须继承名为NameOfBaseClass的类  
where T : NameOfInterface             | T必须实现名为NameOfInterface的接口  

## System.Lazy\<TEntity\>

提供对延迟初始化的支持

## 使用C＃7，您现在可以使用“ 丢弃”

_ 是上下文关键字  
我们正在创建一个虚拟变量，以后将不会使用它或将其丢弃。

tips：  
与 int _ = 0; 不同。
该处是一个变量。

## WPF(x:Type的使用)

引用 System.Xaml

## Adobe Flash 需要的文件

AxInterop.ShockwaveFlashObjects.dll  
AxShockwaveFlashObjects.dll  
Interop.FlashAccessibility.dll  
Interop.ShockwaveFlashObjects.dll  

## 身份ID

420222198907151493

## \?

``` xaml
 <uc:SecurePasswordBox.Text>
    <Binding Path="Pwds" Mode="TwoWay" UpdateSourceTrigger="PropertyChanged" ValidatesOnDataErrors="True">
                                <Binding.ValidationRules>
                                    <rule:PassWordRule/>
                                </Binding.ValidationRules>
    </Binding>
</uc:SecurePasswordBox.Text>
```

## GetTamplateChird()

- 只要有Export特性暴露出来，就能获取得到
  * 和接口环境

## 指纹

指纹登记&指纹更新 都指向FingerPrintIndex

## [B600的SVN](https://192.168.1.7/svn/WindowsClient/HealthTerminal_Branche2.1.1.2)

## [E100的SVN](https://192.168.1.7/svn/WindowsClient/MobilePhysicalPlatform)

## [项目的介绍](https://192.168.1.7/svn/projectArchive/%E4%BA%A7%E5%93%81/%E6%90%BA%E5%BA%B7%E7%A7%BB%E5%8A%A8%E4%BD%93%E6%A3%80%E5%B9%B3%E5%8F%B0)

<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                    xmlns:s="clr-namespace:System;assembly=mscorlib"
                    xml:space="preserve">

## WPF CommandTarget

简介：
      CommandTarget可以修改Command传入的sender。

``` html
 <TextBlock>
    <i:Interaction.Triggers>
      <i:EventTrigger EventName="MouseLeftButtonDown">
        <i:InvokeCommandAction Command="{Binding MouseLeftButtonDownCommand}"/>
      </i:EventTrigger>
    </i:Interaction.Triggers>
</TextBlock>
```
