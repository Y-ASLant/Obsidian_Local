# EXTI配置流程

-  [[../Excalidraw/Drawing 2024-05-18 15.38.46.excalidraw|EXTI流程图]]

> [!INFO] 中断配置
> 可直接使用 CUBEMX 生成代码手动复制

```c
#include "exti.h"

void exti_Init(void)
{
    GPIO_InitTypeDef GPIO_InitStruct;
    __HAL_RCC_GPIOA_CLK_ENABLE();

    GPIO_InitStruct.Pin = GPIO_PIN_0;
    GPIO_InitStruct.Mode = GPIO_MODE_IT_FALLING; // 下降沿触发
    GPIO_InitStruct.Pull = GPIO_PULLUP;          // 初始为高电平
    HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

    HAL_NVIC_SetPriority(EXTI0_IRQn, 2, 0);
    HAL_NVIC_EnableIRQ(EXTI0_IRQn);
}

void EXTI0_IRQHandler(void)
{
    HAL_GPIO_EXTI_IRQHandler(GPIO_PIN_0);
}

void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
    if (GPIO_Pin == GPIO_PIN_0) // 确保处理的是正确的引脚
    {
        HAL_Delay(10); // 消抖处理
        led_toggle();  // 切换LED状态
    }
}
```

# 单个外部中断 EXTI

![[ASLant_Images/9cdcd900cf7cb4acab9584615daf607b_MD5.jpg]]

![[ASLant_Images/b8a28917d1db2547a1142089144ac2bc_MD5.jpg]]

### 外部中断回调函数

```c
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{

}
```

# 多个外部中断线

![[../ASLant_Images/2024-06-01-20-51-07.png]]

```c
/*****************************************************************
*
* 若KEY1_Pin触发中断则执行 LED1_toggle函数
*
* 若KEY2_Pin触发中断则执行 LED2_toggle函数
*
****************************************************************/
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
  if (GPIO_Pin == KEY1_Pin)
  {
    LED1_toggle();
  }
  if (GPIO_Pin == KEY2_Pin)
  {
    LED2_toggle();
  }
}
```
