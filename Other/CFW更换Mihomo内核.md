# CFW 更换 Mihomo 内核
> [!abstract] 文件下载
> -  [bat脚本](https://github.com/kayaladream/Clash-Core-Change/releases/download/v2.0/Clash-Core-Change-v2.0.bat)
> - [Mihomo内核](https://github.com/MetaCubeX/mihomo/releases)

![[../ASLant_Files/2024-07-23-08-55-47.png]]

```Windows
%LocalAppData%\Programs\Clash for Windows\resources\static\files\win\x64
```

![[../../../ASLant_Files/2024-07-23-08-52-17.png]]

# 脚本源代码
```bat
@echo off
setlocal enabledelayedexpansion

for %%F in (mihomo* clash.meta*) do (
    set "filename=%%~nF"
    set "extension=%%~xF"
    set "newname=mihomo!extension!"
    ren "%%F" "!newname!"
)

taskkill /F /IM "Clash for Windows.exe" > nul 2>&1

chcp 65001 > nul 2>&1
set var1=mihomo.exe
set var2=clash-win64.exe

set "tempfile=temp.exe"

rename "%var1%" "%tempfile%"
rename "%var2%" "%var1%"
rename "%tempfile%" "%var2%"

if exist "%USERPROFILE%\.config\mihomo\" (
    rmdir /s /q "%USERPROFILE%\.config\mihomo" > nul 2>&1
)

powershell -NoProfile -Command "Start-Process cmd -ArgumentList '/c mklink /d \"%USERPROFILE%\.config\mihomo\" \"%USERPROFILE%\.config\clash\"' -Verb RunAs -Wait"

for %%F in ("%var1%") do set "size_var1=%%~zF"
for %%F in ("%var2%") do set "size_var2=%%~zF"

if %size_var2% LSS %size_var1% (
    msg * 切换Premium内核成功！
) else if %size_var2% GTR %size_var1% (
    msg * 切换mihomo内核成功！
)

start "" "%LocalAppData%\Programs\Clash for Windows\Clash for Windows.exe"
```
