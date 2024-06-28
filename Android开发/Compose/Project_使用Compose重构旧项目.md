# 简介 

> [!Error] 使用 Kotlin + Jetpack Compose 重构之前的项目 (XML + Java)

# Android Studio 导入 jar
### 下载 `org.eclipse.paho.client.mqttv3-1.2.5.jar `

> [!check] Download
> [官方地址](https://repo.eclipse.org/content/repositories/paho-releases/org/eclipse/paho/)
> [官方1.2.5版本](https://repo.eclipse.org/content/repositories/paho-releases/org/eclipse/paho/org.eclipse.paho.client.mqttv3/1.2.5/org.eclipse.paho.client.mqttv3-1.2.5.jar)

### 将jar 文件复制到项目的 `libs` 目录下
![[../../ASLant_Files/2024-06-23-14-05-33.png]]
### 加载 jar 文件
![[../../ASLant_Files/2024-06-23-14-07-57.png]]

### `build.gradle.kts` 文件会**自动**添加以下内容

```kotlin
implementation(files("libs/org.eclipse.paho.client.mqttv3-1.2.5.jar"))
```

# 重写 UI 界面

> [!NOTE] 因为 Compose 没有 XML 文件, 需要使用 kotlin 重写






# Metraial Design 3 动态取色

> [!box] Android 12L+ 的新特性
> 随着用户桌面壁纸变化，ui 整体颜色也随之变化
> 注意：Material 默认使用[基准](https://m3.material.io/styles/color/the-color-system/tokens)紫色配色方案。如果您未指定或自定义主题，Material 组件将采用基准主题。
### Material Design 主题生成器
[Material Theme 生成器](https://material-foundation.github.io/material-theme-builder/)




# 重构后代码

> [!success] [1.0 版本](https://aslant.top/Cloud/OneDrive/Android/Android%20Studio/AIOT_Compose_20240628_1.0.7z)


