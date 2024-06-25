## Box

> [!NOTE] Box 是一个能够将里面的子项依次按照顺序堆叠的布局组件。

```kotlin
Box {
    Box(
        modifier = Modifier.size(150.dp).background(Color.Green)
    )
    Box(
        modifier = Modifier.size(80.dp).background(Color.Red)
    )
    Text(
        text = "世界"
    )
}
```
#### 效果
![[../../ASLant_Files/2024-06-25-14-11-11.png]]

## Row

> [!NOTE] Row 组件能够将里面的子项按照从左到右的方向水平排列。和 Column 组件一起配合，我们可以构建出很丰富的界面。




![[../../ASLant_Files/2024-06-25-14-13-04.png]]


## Card

```kotlin
Card(
        shape = RoundedCornerShape(8.dp),
        elevation = CardDefaults.cardElevation(4.dp),//阴影大小
        modifier = Modifier
            .padding(horizontal = 12.dp) // 设置 Card 的外边距
            .fillMaxWidth(),
    ){
        Column(
            modifier = Modifier.padding(12.dp) // 里面内容的外边距
        ) {
            Text(
                text = "Jetpack Compose 是什么？",
                fontSize = 24.sp
            )
            Spacer(Modifier.padding(vertical = 5.dp))
            Text(
                text = "Jetpack Compose 是用于构建原生 Android 界面的新工具包。它可简化并加快 Android 上的界面开发，使用更少的代码、强大的工具和直观的 Kotlin API，快速让应用生动而精彩。"
            )
            Row(
                modifier = Modifier.fillMaxWidth(),
                horizontalArrangement = Arrangement.SpaceBetween
            ) {
                IconButton(
                    onClick = { /*TODO*/ }
                ) {
                    Icon(Icons.Filled.Favorite, null)
                }
                IconButton(
                    onClick = { /*TODO*/ },
                ) {
                    Icon(Icons.Filled.Home, null)
                }
                IconButton(
                    onClick = { /*TODO*/ },
                ) {
                    Icon(Icons.Filled.Share, null)
                }
            }
        }
    }
}
```

#### 效果

![[../../ASLant_Files/2024-06-25-14-23-46.png]]

