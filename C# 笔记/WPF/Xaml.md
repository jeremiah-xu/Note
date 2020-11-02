# xmal笔记-control template



## WPF(x:Type的使用)

引用 System.Xaml

## Adobe Flash 需要的文件

AxInterop.ShockwaveFlashObjects.dll  
AxShockwaveFlashObjects.dll  
Interop.FlashAccessibility.dll  
Interop.ShockwaveFlashObjects.dll  

## 身份ID

420222198907151493

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
