# 重置 PowerShell 环境
```powershell
$env:PSModulePath = [System.Environment]::GetEnvironmentVariable("PSModulePath", [System.EnvironmentVariableTarget]::Machine)
```