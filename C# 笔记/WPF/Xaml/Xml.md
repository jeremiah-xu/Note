# Xml在xaml中的使用

## 如何:绑定到XDocument, XElement，或LINQ为XML查询结果

Xml中XElement本质是XmlElement对象，隐式的转化为string类型。

``` cs
<TabControl>
    <TabItem>
        <TabControl>
            <TabItem.Header>
                <Binding Converter="{StaticResource XmlElementToStringConverter}"   Source="{StaticResource Lang}" XPath="resource[@key='Auscultation.LungSoundFormForechest']" />
            </TabItem.Header>
        </TabControl>
    </TabItem>
</TabControl>
```

``` cs
<xmlns:s="clr-namespace:System;assembly=mscorlib">

<UserControl.Resources>
    <s:String x:Key="str">resource[@key='Auscultation.Forechest']</s:String>
</UserControl.Resources>
 
<TabControl>
    <TabItem>
        <TabControl  Header="{Binding XPath={StaticResource 'str'}, Source={StaticResource Lang}, Converter={StaticResource XmlElementToStringConverter}}">
    </TabItem>
</TabControl>
```