# Printf() 串口重定向

> [!BUG] 重定向到 huart1

```c
int fputc(int ch, FILE *f)
{
  HAL_UART_Transmit(&huart1, (uint8_t *)&ch, 1, 0xffff);
  return ch;
}
```


