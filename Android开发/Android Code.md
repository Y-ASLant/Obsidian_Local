> [!info] Android Studio
> 关键性代码

# 状态栏沉浸、全屏_Java

```java
// Mainactivty.java
// 初始化 ImmersionBar 沉浸状态栏和底部导航栏
ImmersionBar.with(this)
        .transparentNavigationBar()  // 设置底部导航栏透明
        .statusBarColor(android.R.color.transparent)
        .statusBarDarkFont(true)
        .statusBarColor(android.R.color.transparent)  // 设置状态栏颜色
        .statusBarDarkFont(true)  // 设置状态栏字体为深色
        .init();
```

```java
//添加到builder.gradle.kts
dependencies {  
  
    implementation("com.geyifeng.immersionbar:immersionbar:3.2.2")  
    implementation("com.geyifeng.immersionbar:immersionbar-ktx:3.2.2")
    
}
```

# MQTT-V3

> [!success] Download
> [MQTT_V3-1.2.5.jar](https://aslant.top/Cloud/OneDrive/Encryption/Project/org.eclipse.paho.client.mqttv3-1.2.5.jar)

```java
//导入到Android Studio后会自动添加
//在builder. Gradle. Kts中
Dependencies {  
  
     implementation(files("libs/org.eclipse.paho.client.mqttv3-1.2.5.jar"))
    
}
```
# 状态栏沉浸、全屏_Compose
> [!INFO] 横屏沉浸，去除黑边占位

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <style name="Theme.AIOT_Compose" parent="android:Theme.Material.Light.NoActionBar">
        <!--        TODO:全屏显示-->
        <item name="android:windowTranslucentNavigation">true</item>
        <item name="android:windowLayoutInDisplayCutoutMode">shortEdges</item>
        <!--        <item name="android:windowFullscreen">true</item>-->
    </style>
</resources>
```
