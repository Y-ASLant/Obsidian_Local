# ALT + F4 屏蔽和解除脚本

```bat
chcp 65001
@echo off
echo "请以管理员身份运行，无误后按任意键继续"
pause
title 屏蔽/允许 ALT-F4 组合键
cls
set rp=HKLM\SYSTEM\CurrentControlSet\Control\Keyboard Layout
set rv=Scancode Map
set /p ok=屏蔽或解除ALT-F4组合键 [Y-屏蔽 N-解除]:
if /i %ok%==Y (reg add "%rp%" /v "%rv%" /d 00000000000000000200000038e03e0000000000 /t reg_binary /f&&cls&&echo 已屏蔽ALT-F4组合键，重启计算机生效!)
if /i %ok%==N (reg delete "%rp%" /v "%rv%" /f&&cls&&echo 已解除ALT-F4组合键的屏蔽，重启计算机生效!)
echo.&&echo.&&pause
```
