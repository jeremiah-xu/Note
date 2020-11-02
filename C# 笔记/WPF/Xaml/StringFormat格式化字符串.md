# WPF中Binding使用StringFormat格式化字符串方法
```cs
货币格式
<TextBlock Text="{Binding Price, StringFormat={}{0:C}}" /> // $123.46
货币格式，一位小数
<TextBox Text="{Binding Price, StringFormat={}{0:C1}}" /> // $123.5
前文字
<TextBox Text="{Binding Price, StringFormat=单价：{0:C}}" /> //单价：$123.46
后文字
<TextBox Text="{Binding Price, StringFormat={}{0}元}" /> // 123.45678元
固定的位数，位数不能少于未格式化前，仅支持整形
<TextBox Text="{Binding Count, StringFormat={}{0:D6}}" /> // 086723
指定小数点后的位数
<TextBox Text="{Binding Total, StringFormat={}{0:F4}}" /> // 28768234.9329
用分号隔开的数字，并指定小数点后的位数
<TextBox Text="{Binding Total, StringFormat={}{0:N3}}" /> // 28,768,234.933
格式化百分比
<TextBox Text="{Binding Persent, StringFormat={}{0:P1}}" /> // 78.9 %
占位符
<TextBox Text="{Binding Price, StringFormat={}{0:0000.00}}" /> // 0123.46
<TextBox Text="{Binding Price, StringFormat={}{0:####.##}}" /> // 123.46
日期/时间
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:d}}" /> // 5/4/2015
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:D}}" /> // Monday, May 04, 2015
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:f}}" /> // Monday, May 04, 2015 5:46 PM
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:F}}" /> // Monday, May 04, 2015 5:46:56 PM
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:g}}" /> // 5/4/2015 5:46 PM
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:G}}" /> // 5/4/2015 5:46:56 PM
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:m}}" /> // May 04
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:M}}" /> // May 04
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:t}}" /> // 5:46 PM
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:T}}" /> // 5:46:56 PM
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:yyyy年MM月dd日}}" /> // 2015年05月04日
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:yyyy-MM-dd}}" /> // 2015-05-04
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:yyyy-MM-dd HH:mm}}" /> // 2015-05-04 17:46
<TextBox Text="{Binding DateTimeNow, StringFormat={}{0:yyyy-MM-dd HH:mm:ss}}" /> // 2015-05-04 17:46:56
或者

<TextBlock Text="{Binding Time,StringFormat='yyyy:MM:dd HH:mm:ss'}"/>
多重绑定
<TextBox.Text>
                        <MultiBinding StringFormat="姓名：{0}{1}">
                            <Binding Path="FristName" />
                            <Binding Path="LastName" />
                        </MultiBinding>
                    </TextBox.Text>
// 姓名：AAbb
多重绑定中的特殊字符
<TextBox.Text>
                        <MultiBinding StringFormat="姓名：{0}&#x09;{1}">
                            <Binding Path="FristName" />
                            <Binding Path="LastName" />
                        </MultiBinding>
                    </TextBox.Text>
                        <!--
                        \a  &#x07;  BEL
                        \b  &#x08;  BS - Backspace
                        \f  &#x0c;  FF - Formfeed
                        \n  &#x0a;  LF, NL - Linefeed, New Line
                        \r  &#x0d;  CR - Carriage return
                        \t  &#x09;  HT - Tab, Horizontal Tabelator
                        \v  &#x0b;  VT - Vertical Tabelator 
                        -->
// 姓名：AA    bb
```