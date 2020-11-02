# 深入浅出-Binding的源与路径
## 1. 把控件作为Binding源与Binding标记扩展

```cs
<TextBox x:Name="textBox1" Text="{Binding Path=Value, ElementName=slider1}" />
或
<TextBox x:Name="textBox1" Text="{Binding Value, ElementName=slider1}" />
<Slider x:Name="slider1" Maximum="100" Minimum="0" Margin="5" />
```

Binding还支持多级路径

```cs
<TextBox x:Name="textBox1" Text="{Binding Path=Text.Length, ElementName=textBox1,Mode=OneWay}" />
```

## 2. 控制Binding的方向及数据更新

Binding的数据流向的属性BindingMode[TwoWay, OneWay, OnTime, OneWayToSource, Default]

## 3. 没有Path的Binding

```cs
<StackPannel.Resources>
   <sys:String x:Key="myString">喜欢美女</sys:String>
<StackPanel.Resources>

<TextBlock x:Name="textBlock1" Text="{Binding Paht=.,Source={StaticResource ResourceKey=myString}}"  />
或
<TextBlock x:Name="textBlock1" Text="{Binding Paht=.,Source={StaticResource ResourceKey=myString}}"  />
或
<TextBlock x:Name="textBlock1" Text="{Binding .,Source={StaticResource ResourceKey=myString}}"  />
或
<TextBlock x:Name="textBlock1" Text="{Binding Source={StaticResource ResourceKey=myString}}"  />
```

注意：

a. c#代码里进行绑定字符串时是不能省略path的.
```cs
string myString="fuckfuck";
this.textBlock1.setBinding(TextBlock.TextProperty,new Binding("."){Source=myString});
```
b. XAML代码里的这个path和"."可省略

## 4. 使用DataContext作为Binding的源
```cs
public class Student
{
   public int Id {get;set;}
   public string Name {get;set;}
   public int Age {get;set;}
}
```
```cs
xmlns:local="clr-namespace:WpfApplication1"  //命名空间下

<StackPanel>
   <StackPanel.DataContext>
        <local:Student Id="6" Age="29" Name="Tim" />   //数据
  </StackPanel.DataContext>
       <TextBox Text="{Binding Path=Id}" Margin="5" />
       <TextBox Text="{Binding Path=Name}" Margin="5" />
       <TextBox Text="{Binding Path=Age}" Margin="5" />
</StackPanel>

<Grid DataContext="6">
  <Grid>
       <Grid>
              <Button x:Name="btn" Content="OK" Click="btn_Click" />
       </Grid>
  </Grid>
</Grid>
```
```cs
private void btn_Click(object sender,RoutedEventArgs e)
{
     MessageBox.Show(btn.DataContext.ToString()); //会显示6，因为属性值沿UI元素树向下传递
}
```
注：其实DataContext是一个依赖属性，会向内层控件传递
```cs
<StackPanel>
   <StackPanel.DataContext>
        <sys:String>Hello DataContext </sys:string>   //数据
  </StackPanel.DataContext>
       <TextBox Text="{Binding}" Margin="5" />
</StackPanel>
```
 

## 5. 使用集合对象进行ItemsSource绑定

wpf中的列表式控件是派生自ItemsControl类，自然也就继承了ItemSource这个属性，每个ItemsControl的派生类都具有自己对应的条目容器（Item Container）,如ListBox的条目容器是ListBoxItem,ComboxBox的条目容器是ComboBoxItem

```cs
this.listBoxStudents.ItemsSource=stuList; //设置绑定数据源
this.listBoxStudents.DisplayMemberPath="Name"; //绑定要显示的属性

<ListBox x:Name="listBoxStudents">
　　<ListBox.ItemTemplate>
　　　　<DataTemplate>
　　　　　　<StackPanel Orientation="Horizontal">
　　　　　　　　<TextBlock Text="{Binding Path=Id}" Width="30" />
　　　　　　</StackPanel>
　　      </DataTemplate>
　　</ListBox.ItemTemplate>
</ListBox>
```

## 6. 使用ADO.NET对象作为Binding的源
```cs
DataTable dt=this.GetData();
this.listBoxStudents.DisplayMemberPath="Name";
this.listBoxStudents.ItemsSource=dt.DefaultView;

<ListView x:Name="listViewStudents" >
　　<ListView.View>
　　　　<GridView>
　　　　　　<GridViewColumn Header="Id" Width="60" DisplayMemberBinding="{Binding Id}" />
　　　　　　<GridViewColumn Header="Id" Width="60" DisplayMemberBinding="{Binding Name}" />
　　　　　　<GridViewColumn Header="Id" Width="60" DisplayMemberBinding="{Binding Age}" />
　　　　</GridView>
　　</ListView.View>
</ListView>
```
注：ListView是ListBox的派生类，GridView是ViewBase的派生类，ListView的View属性是一个ViewBase类型的对象，目前只有一个GridView可用于ListView。

## 7. XML数据作为Binding的源

假设xml文件存于D:\RawData.xml
```cs
<?xml version="1.0" encoding="utf-8">
<StudentList>
　　<Student Id="1">
　　　　<Name>Tim</Name>
　　</Student>

　　<Student Id="2">
　　　　<Name>Tom</Name>
　　</Student>
<StudentList>

<ListView x:Name="listViewStudents" >
　　<ListView.View>
　　　　<GridView>
　　　　　　<GridViewColumn Header="Id" Width="60" DisplayMemberBinding="{Binding XPath=@Id}" />
　　　　　　<GridViewColumn Header="Id" Width="60" DisplayMemberBinding="{Binding XPath=@Name}" />
　　　　　　<GridViewColumn Header="Id" Width="60" DisplayMemberBinding="{Binding XPath=@Age}" />
　　　　</GridView>
　　</ListView.View>
</ListView>
```

后台读取xml数据
```cs
XmlDocument doc=new XmlDocument();
doc.Load(@"D:\RawData.xml");

XmlDataProvider xdp=new XmlDataProvider();
xdp.Document=doc;
xdp.XPath=@"/StudentList/Student";
```
或
```cs
XmlDataProvider xdp=new XmlDataProvider();
xdp.Source=new Uri(@"D:\RawData.xml");
xdp.XPath=@"/StudentList/Student";

this.listViewStudents.DataContext=xdp;
this.listViewStudents.SetBinding(ListView.ItemsSourceProperty,new Binding());
```

LINQ查询绑定
```cs
this.listViewStudents.ItemsSource=from stu in stuList where stu.Name.StartsWith("T") select stu;
或
DataTable dt=this.GetDataTable();
this.listViewStudents.ItemsSource=
　　from row in dt.Rows.Cast<DataRow>()
　　where Convert.ToString(row["Name"]).StartsWith("T")
　　select new Student()
　　{
           Id=int.Parse(row["Id"].ToString()),
 　　　Name=row["Name"].ToString(),
　　　　Age=int.Parse(row["Age"].ToString())
　　};

this.listViewStudents.ItemsSource=
　　from element in xdoc.Descendants("Student")
　　where element.Attribute("Name").Value.StartsWith("T")
　　select new Student()
　　{
           Id=int.Parse(element.Attribute("Id").Value),
 　　　 Name=element.Attribute("Name").Value,
　　　  Age=int.Parse(element.Attribute("Age").Value),
　　};
```
 
分类: WPF笔记