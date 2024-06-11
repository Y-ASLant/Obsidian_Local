> [!BUG] 核心代码

```c
uint8_t Buff[32] = "Hello World";
while (1)
{
    HAL_UART_Transmit(&huart1, Buff, sizeof(Buff), 0xFFFF);
    HAL_UART_Transmit(&huart1, (uint8_t *)"\r", 4, 0xFFFF); // 换行
}
```


# 串口中断输出 Hello World

### 全局变量
```c
unsigned char  data_1;
```
### 开启中断
```c
HAL_UART_Receive_IT(&huart1,&data_1,1);
```

### 重写中断回调函数
```c
void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart)
{
    printf("Hello World");
}
```

