---
title: bat脚本命令
date: 2026-03-24 21:48:17
tags:
  - 命令行
cover: /images/裨田阿求_1600x1000.png
categories: 学习
---
### 前言：
bat 脚本是 Windows 自带的脚本，非常适合用来**自动化重复性操作**，比如一键备份文件、批量重命名、启动多个程序等；它的语法简单，无需安装任何额外环境，用记事本就能写。

### 常用命令
| 命令                  | 作用            |
| ------------------- | ------------- |
| echo                | 输出信息 / 开启回显   |
| @echo off           | 关闭回显          |
| pause               | 暂停，显示“按任意键继续” |
| rem(::)             | 注释（不执行）       |
| set                 | 定义/显示变量       |
| %变量名%               | 使用变量          |
| if                  | 条件判断          |
| for                 | 循环            |
| cd                  | 切换目录          |
| dir                 | 列出文件          |
| copy/xcopy/robocopy | 复制文件/目录       |
| del                 | 删除文件          |
| md/mkdir            | 创建目录          |
| rd/rmdir            | 删除目录          |
| start               | 启动程序或文件       |
| call                | 调用另一个 .bat    |
| exit                | 退出            |

### 示例：
1.清理临时文件（C盘爆满时）

```
@echo off
echo 正在清理系统临时文件...
del /f /s /q %temp%\*.*
echo 清理完成！
pause
```

2.批量重命名

```
@echo off
set /p prefix=请输入要添加的前缀：
for %%i in (*.txt) do (
    ren "%%i" "%prefix%%%i"
)
echo 重命名完成！
pause
```

3.自动备份

```
@echo off
set source=C:\Users\你的用户名\Documents
set target=D:\backup\docs_backup
set datestr=%date:~0,4%%date:~5,2%%date:~8,2%

xcopy "%source%" "%target%\%datestr%\" /E /I /Y
echo 备份完成，保存至 %target%\%datestr%
pause
```

4.一键打开

```
@echo off
start "" "C:\Program Files\Google\Chrome\Application\chrome.exe"
start "" "C:\Program Files\Microsoft Office\root\Office16\WINWORD.EXE"
start "" "C:\Windows\System32\notepad.exe"
echo 已启动常用软件
pause
```
