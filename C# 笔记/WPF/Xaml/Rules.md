# Rule 规则验证

## Text 文本字符串验证
Text属性是string类型，绑定Path源。当Path的源更新，验证数据。
```cs
<uc:SecurePasswordBox.Text>
    <Binding Path="Pwds" Mode="TwoWay" UpdateSourceTrigger="PropertyChanged" ValidatesOnDataErrors="True">
        <Binding.ValidationRules>
            <rule:PassWordRule/>
        </Binding.ValidationRules>
    </Binding>
</uc:SecurePasswordBox.Text>
```