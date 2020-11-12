
```cs
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                    xmlns:s="clr-namespace:System;assembly=mscorlib"
                    xml:space="preserve">
```
## WPF CommandTarget

简介：
      CommandTarget可以修改Command传入的sender。

# TextBlock组件 鼠标左键点击，触发 自定义Command
``` cs
 <TextBlock>
    <i:Interaction.Triggers>
      <i:EventTrigger EventName="MouseLeftButtonDown">
        <i:InvokeCommandAction Command="{Binding MouseLeftButtonDownCommand}"/>
      </i:EventTrigger>
    </i:Interaction.Triggers>
</TextBlock>
```
# WPF 不支持盒子模型 的margin（外边距） 交叉！