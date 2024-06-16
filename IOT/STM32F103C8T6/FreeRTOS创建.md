# 方式一、使用 cubeMX 创建 FreeRTOS 项目

### 创建基本项目
![[../../ASLant_Files/c753f49035c8e5295917dce4fc2cfb0e_MD5.jpg]]

![[../../ASLant_Files/0abdde44f1b050cd6ca127ddc6b09f9f_MD5.jpg]]

![[../../ASLant_Files/8d4259efe3b0abe539cf7a39ada7f6d2_MD5.jpg]]

![[../../ASLant_Files/11680523fa74ef41e6b588c8ae246bd4_MD5.jpg]]

![[../../ASLant_Files/d6989cafd0557e5d7bdac18f98b25c5f_MD5.jpg]]

### 增加 RTOS
![[../../ASLant_Files/3f86089aeeea8729728ab7241033ebeb_MD5.jpg]]

#### 创建第一个任务
![[../../ASLant_Files/87cef4a9af4bd8bc64140ee53031727b_MD5.jpg]]

#### 创建第二个任务
![[../../ASLant_Files/78065f0cfab0ad25b04093958aa7a7c1_MD5.jpg]]


![[../../ASLant_Files/4920fe5e53d995a7605479c931afd947_MD5.jpg]]


![[../../ASLant_Files/fba169d8cbda4f81393e4298c94261b1_MD5.jpg]]


![[../../ASLant_Files/789c67f4cc0709f62956194aea0d611c_MD5.jpg]]


![[../../ASLant_Files/2f5bf4dcd9af497959f3eb4fc25b5659_MD5.jpg]]

![[../../ASLant_Files/db7554fbbeff5f4f6b3c3920fe819393_MD5.jpg]]

![[../../ASLant_Files/7c7aab8c9e375905d7abfc7c0917dae0_MD5.jpg]]

![[../../ASLant_Files/445bfed20f350f2ff6ca8712045171dc_MD5.jpg]]

![[../../ASLant_Files/fee10e1f9570bf08c75cde3d93c21a83_MD5.jpg]]

![[../../ASLant_Files/9cdeffee024e5a29f168c4e83c018ec2_MD5.jpg]]

# END 
> [!SUCCESS] 带 RTOS 的 STM32 项目创建完成

# 实验

> [!INFO] 点灯
> LED 1 以 1000 ms 闪烁
> LED 2 以 100 ms 闪烁
### 编写任务代码位置

```c
在main.c文件中找到该函数 MX_FREERTOS_Init();
选中F12跳转到定义位置

然后往下翻，找到该函数
void StartTask02(void *argument)
{
  /* USER CODE BEGIN StartTask02 */
  /* Infinite loop */
  for(;;)
  {
    osDelay(1);
  }
  /* USER CODE END StartTask02 */
}
HAL库生成默认的任务名从StartTask02开始
在osDelay(1)处，编写任务一逻辑代码
```
### 增加 LED1、LED2 GPIO口
![[../../ASLant_Files/045eed57ecb85ea6eb6997e5398d2538_MD5.jpg]]

![[../../ASLant_Files/b70fe66b4e368e9ce2c92149b0af1b3a_MD5.jpg]]
#### 任务一代码
```c
HAL_GPIO_TogglePin(LED1_GPIO_Port,LED1_Pin);
HAL_Delay(1000);
```
##### 代码位置
```c
/* USER CODE END Header_StartTask02 */
void StartTask02(void *argument)
{
    /* USER CODE BEGIN StartTask02 */
    /* Infinite loop */
    for(;;)
    {
        HAL_GPIO_TogglePin(LED1_GPIO_Port,LED1_Pin);
        HAL_Delay(1000);
    }
    /* USER CODE END StartTask02 */
}
```
#### 任务二代码
```c
HAL_GPIO_TogglePin(LED2_GPIO_Port,LED2_Pin);
HAL_Delay(100);
```
##### 代码位置
```c
/* USER CODE END Header_StartTask03 */
void StartTask03(void *argument)
{
    /* USER CODE BEGIN StartTask03 */
    /* Infinite loop */
    for(;;)
    {
        HAL_GPIO_TogglePin(LED2_GPIO_Port,LED2_Pin);
        HAL_Delay(100);
    }
    /* USER CODE END StartTask03 */
}
```

# 最终效果
<div style="text-align: center;"><video src="https://s138.ananas.chaoxing.com/sv-w8/video/9d/9e/5b/29a123f1fbc3f2a60bf5af12eccf6c8f/sd.mp4" width="45%" height="100%" controls="controls" class="rounded-video"></video></div>

#  方式二、手动创建 FreeRTOS 项目
> [!BUG] [FreeRTOS](https://www.freertos.org/zh-cn-cmn-s/index.html)






