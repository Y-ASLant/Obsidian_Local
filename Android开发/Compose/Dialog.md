# 弹窗
> [!error] Dialog

```kotlin
import android.widget.Toast
import androidx.compose.foundation.layout.Arrangement
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material3.AlertDialog
import androidx.compose.material3.Button
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.material3.Text
import androidx.compose.material3.TextButton
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.runtime.setValue
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.platform.LocalContext
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp

@Composable
fun Dialog() {
    val context = LocalContext.current
    var showDialog by remember { mutableStateOf(false) }

    Surface(
        modifier = Modifier.fillMaxSize(), color = MaterialTheme.colorScheme.background
    ) {
        Column(
            modifier = Modifier.fillMaxSize(),
            verticalArrangement = Arrangement.Center,
            horizontalAlignment = Alignment.CenterHorizontally
        ) {
            Button(
                shape = RoundedCornerShape(5.dp),
                onClick = { showDialog = true },
            ) {
                Text(
                    text = "弹窗",
                    fontSize = 16.sp,
                )
            }
        }

        if (showDialog) {
            AlertDialog(onDismissRequest = {
                showDialog = false
            }, title = {
                Text(
                    text = "ASLant",
                    fontSize = 16.sp
                )
            }, text = {
                Text(
                    "This is a simple alert dialog with Yes and No buttons.",
                    fontSize = 16.sp,
                )
            }, confirmButton = {
                TextButton(onClick = {
                    showDialog = false
                    Toast.makeText(
                        context, "Yes", Toast.LENGTH_SHORT
                    ).show()
                }) {
                    Text(
                        "Yes", fontSize = 16.sp
                    )
                }
            }, dismissButton = {
                TextButton(onClick = {
                    showDialog = false
                    Toast.makeText(
                        context, "No", Toast.LENGTH_SHORT
                    ).show()
                }) {
                    Text(
                        "No", fontSize = 16.sp
                    )
                }
            })
        }
    }
}
```
# 效果

![[../../ASLant_Files/2024-06-26-15-40-52.png]]