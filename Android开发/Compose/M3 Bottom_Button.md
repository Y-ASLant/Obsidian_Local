### `Bottom_Bar.kt`

```kotlin
package compose.iot.ui.theme

import androidx.annotation.DrawableRes
import androidx.compose.foundation.layout.*
import androidx.compose.material3.*
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.platform.LocalContext
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import android.widget.Toast
import compose.iot.R

@Composable
fun Bottom_button(selected: Int, onSelectedChanged: (Int) -> Unit) {
    val context = LocalContext.current // 获取当前上下文

    NavigationBar(
        containerColor = Color.White,
        tonalElevation = 4.dp,
        modifier = Modifier.padding(bottom = 0.dp)
    ) {
        NavigationBarItem(
            selected = selected == 0,
            onClick = {
                Toast.makeText(context, "切换至首页", Toast.LENGTH_SHORT).show()
                onSelectedChanged(0)
            },
            icon = {
                Icon(
                    painter = painterResource(if (selected == 0) R.drawable.index else R.drawable.index_null),
                    contentDescription = "首页",
                    tint = if (selected == 0) Color.Red else Color.Black,
                    modifier = Modifier.size(24.dp)
                )
            },
            label = {
                Text("首页", color = if (selected == 0) Color.Red else Color.Black, fontSize = 12.sp)
            },
            alwaysShowLabel = true
        )
        NavigationBarItem(
            selected = selected == 1,
            onClick = {
                Toast.makeText(context, "切换至面板", Toast.LENGTH_SHORT).show()
                onSelectedChanged(1)
            },
            icon = {
                Icon(
                    painter = painterResource(if (selected == 1) R.drawable.dashboard else R.drawable.dashboard_null),
                    contentDescription = "面板",
                    tint = if (selected == 1) Color.Magenta else Color.Black,
                    modifier = Modifier.size(24.dp)
                )
            },
            label = {
                Text("面板", color = if (selected == 1) Color.Magenta else Color.Black, fontSize = 12.sp)
            },
            alwaysShowLabel = true
        )
        NavigationBarItem(
            selected = selected == 2,
            onClick = {
                Toast.makeText(context, "切换至关于", Toast.LENGTH_SHORT).show()
                onSelectedChanged(2)
            },
            icon = {
                Icon(
                    painter = painterResource(if (selected == 2) R.drawable.info else R.drawable.info_null),
                    contentDescription = "关于",
                    tint = if (selected == 2) Color.Blue else Color.Black,
                    modifier = Modifier.size(24.dp)
                )
            },
            label = {
                Text("关于", color = if (selected == 2) Color.Blue else Color.Black, fontSize = 12.sp)
            },
            alwaysShowLabel = true
        )
    }
}

@Composable
fun TabItem(
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
### 效果
![[ASLant_Files/4d13db31177bb7db76d3e81e0699827.jpg|500]]