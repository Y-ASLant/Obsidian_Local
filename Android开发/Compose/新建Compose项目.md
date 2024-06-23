> [!bug] Android Studio 版本需要 >= 4.0
> Jetpack Compose 仅支持 Kotlin 语言

# 创建 Kotlin 项目
![[../../ASLant_Files/2024-06-22-23-02-07.png|600]]

![[../../ASLant_Files/2024-06-22-23-05-32.png|600]]

# 界面代码_单文件

> [!NOTE] 所有代码都在MainActivity.kt 中

```kotlin
package compose.iot

import androidx.compose.ui.graphics.Color
import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.annotation.DrawableRes
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.Row
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.size
import androidx.compose.material3.Icon
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import compose.iot.ui.theme.AIOT_ComposeTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            AIOT_ComposeTheme {
                Box(modifier = Modifier.fillMaxSize(), contentAlignment = Alignment.Center) {
                    // 创建一个 Column 并添加文本
                    Column {
                        Text(text = "Hello Kotlin", fontSize = 24.sp)
                    }
                }
                Box(modifier = Modifier.fillMaxSize(), contentAlignment = Alignment.BottomCenter) {
                    Bottom_button(0)
                }
            }
        }
    }

    @Composable
    private fun Bottom_button(selected: Int) {
        Row(
            Modifier
                .background(Color.White)
                .padding(bottom = 2.dp)
        ) {
            TabItem(
                if (selected == 0) R.drawable.index else R.drawable.index_null,
                "首页",
                if (selected == 0) Color.Red else Color.Black,
                Modifier.weight(1f)
            )
            TabItem(
                if (selected == 1) R.drawable.dashboard else R.drawable.dashboard_null,
                "面板",
                if (selected == 1) Color.Cyan else Color.Black,
                Modifier.weight(1f)
            )
            TabItem(
                if (selected == 2) R.drawable.info else R.drawable.info_null,
                "关于",
                if (selected == 2) Color.Blue else Color.Black,
                Modifier.weight(1f)
            )
        }
    }

    @Composable
    private fun TabItem(
        @DrawableRes iconId: Int,
        title: String,
        tint: Color,
        modifier: Modifier = Modifier
    ) {
        Column(
            modifier.padding(vertical = 8.dp),
            horizontalAlignment = Alignment.CenterHorizontally
        ) {
            Icon(painterResource(iconId), title, Modifier.size(28.dp), tint = tint)
            Text(title, fontSize = 12.sp, color = tint)
        }
    }
}

```

# 界面代码_分函数

> [!error] MainActivity.kt

```kotlin
package compose.iot

import android.os.Bundle
import compose.iot.ui.theme.*
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.material3.Text
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableIntStateOf
import androidx.compose.runtime.setValue
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.sp
import compose.iot.ui.theme.AIOT_ComposeTheme

class MainActivity : ComponentActivity() {
    var selected by mutableIntStateOf(0)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            AIOT_ComposeTheme {
                Box(modifier = Modifier.fillMaxSize(), contentAlignment = Alignment.Center) {
                    // 创建一个 Column 并添加文本
                    Column {
                        Text(text = "Hello Kotlin", fontSize = 24.sp)
                    }
                }
                Box(modifier = Modifier.fillMaxSize(), contentAlignment = Alignment.BottomCenter) {
                    Bottom_button(selected)
                }
            }
        }
    }
}
```

> [!error] Bottom_Bar.kt

```kotlin
package compose.iot.ui.theme

import androidx.annotation.DrawableRes
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.Row
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.size
import androidx.compose.material3.Icon
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import compose.iot.R

@Composable
public fun Bottom_button(selected: Int) {
    Row(
        Modifier
            .background(Color.White)
            .padding(bottom = 2.dp)
    ) {
        TabItem(
            if (selected == 0) R.drawable.index else R.drawable.index_null,
            "首页",
            if (selected == 0) Color.Red else Color.Black,
            Modifier.weight(1f)
        )
        TabItem(
            if (selected == 1) R.drawable.dashboard else R.drawable.dashboard_null,
            "面板",
            if (selected == 1) Color.Cyan else Color.Black,
            Modifier.weight(1f)
        )
        TabItem(
            if (selected == 2) R.drawable.info else R.drawable.info_null,
            "关于",
            if (selected == 2) Color.Blue else Color.Black,
            Modifier.weight(1f)
        )
    }
}

@Composable
public fun TabItem(
    @DrawableRes iconId: Int,
    title: String,
    tint: Color,
    modifier: Modifier = Modifier
) {
    Column(
        modifier.padding(vertical = 8.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Icon(painterResource(iconId), title, Modifier.size(28.dp), tint = tint)
        Text(title, fontSize = 12.sp, color = tint)
    }
}
```
# 界面效果

![[ASLant_Files/d087c8137f7ecc710ea176cfc05e7d2 1.jpg\|450]]
# 源代码下载

> [!check] [Download](https://aslant.top/Cloud/OneDrive/Android/Android%20Studio/AIOT_Compose.7z)

# 注意

```kotlin
implementation("androidx.lifecycle:lifecycle-viewmodel:2.8.2")
```