
## 为计算机上的每个仓库设置 Git 用户名
1. 打开 Git Bash。
2. 设置 Git 用户名：
```
$ git config --global user.name "Mona Lisa"
```
3. 确认您正确设置了 Git 用户名：
```
$ git config --global user.name
> Mona Lisa
```

## 为一个仓库设置 Git 用户名
1. 打开 Git Bash。
2. 将当前工作目录更改为您想要在其中配置与 Git 提交关联的名称的本地仓库。
3. 设置 Git 用户名：
```
$ git config user.name "Mona Lisa"
```
4. 确认您正确设置了 Git 用户名：
```
$ git config user.name
> Mona Lisa
```

# 实战
## 为一个仓库设置 Git 邮箱
```c++
Admin@PS2020ABCDMFCF MINGW64 ~/Desktop/Note in git/Note (main)
$ git config user.email "xun73217496@qq.com"
```
查看 Git 邮箱
```c++
Admin@PS2020ABCDMFCF MINGW64 ~/Desktop/Note in git/Note (main)
$ git config user.email
xun73217496@qq.com
```