### 中断的优势

1. 速度匹配：可以解决快速CPU和慢速外设之间传送数据的矛盾
    
2. 分时操作：CPU可以分时为多个I/O设备服务，提高了计算机的利用率
    
3. 实时响应：CPU能够及时处理应用系统的随机事件，系统的实时性大大增强
    
4. 可靠性高：CPU具有处理设备故障及掉电等突发事件能力，从而使系统可靠性提高
    

### 中断优先级和中断嵌套

1. CPU同时接收到几个中断请求时，响应中断源的先后顺序
    
2. 首先响应优先级最高的中断请求
    
3. 正在进行的中断过程不能被新的同级或低优先级中断请求所中断
    
4. 正在进行的低优先级中断服务，能被高优先级中断请求所中断
    
5. 中断向量就是中断服务函数的入口地址
    

![[../../ASLant_Files/79fe996da09dc1e4c82d4307d023a5c5_MD5.gif]]

![[../../ASLant_Files/b8928ac89943ea66fb1e7a302b85f122_MD5.jpg|506]]

### STM32G431中断源

1. 71个可屏蔽中断通道（102个中断源）+16个 Cortex@M4 FPU中断通道
    微控制器片内集成了很多外设，对于单个外设而言，它通常具备若干个可以引起中断的中断源，而该外设的所有中断源只能通过指定的中断通道向内核申请中断
    
2. 16个可编程优先级（使用4位中断优先级）
    
3. NVIC与处理器内核接口紧密耦合，可实现低延迟中断处理和延迟到达中断的高效处理
    
4. STM32只使用中断优先级寄存器NVIC_IPR的高四位，并分成抢占优先级和子优先级两组
    多个中断同时提出申请时：先比较抢占优先级，再比较子优先级。谁的优先级高，先处理谁。
    
5. 0~15号外部中断线用于GPIO引脚的外部中断
    
6. 16~43号外部中断线用于RTC闹钟，USB事件等
    
7. 当对应GPIO引脚与外部中断线连接后，GPIO引脚才具备外部中断的功能，可以设置外部中断的触发方式（上升沿，下降沿）
    

### 优先级配置

分为两步：

1. 组优先级设置，先选择一个组，每个组代码对应一个优先级方案
    ![[../../ASLant_Files/20c61b92f3e30be6fe9d6b8d4a2e9387_MD5.jpg]]
    
2. 组确定后，再确定抢占优先级和子优先级
    ![[../../ASLant_Files/f8f194bf0e173696f701eb5200dabc9d_MD5.jpg]]

### 抢占优先级和响应优先级

STM32 的中断向量具有两个属性，一个为抢占优先级，另一个为响应优先级，其编号越小，表明它的优先级别越高。
抢占，是指打断其他中断的属性，即因为具有这个属性会出现嵌套中断（在执行中断服务函数A 的过程中被中断B 打断，执行完中断服务函数B 再继续执行中断服务函数A），抢占属性由NVIC_IRQChannelPreemptionPriority 的参数配置。
响应，则应用在抢占属性相同的情况下，当两个中断向量的抢占优先级相同时，如果两个中断同时到达， 则先处理响应优先级高的中断， 响应属性由NVIC_IRQChannelSubPriority 参数配置
如果不设置中断优先级，那么将按芯片的默认优先级响应，当默认优先级不能满足要求时，才需要人工设置中断优先级。
HAL库中初始化函数HAL_Init将优先级分组设置为第4组，即有0~15组，共16组抢占优先级，没有子优先级，编号越小，优先级越高

### 中断编程的顺序

1. 使能中断请求
    
2. 配置中断优先级分组
    
3. 配置NVIC寄存器，初始化NVIC_InitTypeDef
    
4. 编写中断服务函数
    

### GPIO 的外部中断配置

STM32 的每一个GPIO都能配置成一个外部中断触发源，这点也是 STM32 的强大之处。STM32 通过根据引脚的序号不同将众多中断触发源分成不同的组，比如：PA0，PB0，PC0，PD0，PE0，PF0，PG0为第一组，那么依此类推，我们能得出一共有16 组，STM32 规定，每一组中同时只能有一个中断触发源工作，那么，最多同时工作的也就是16个外部中断。

|GPIO引脚|中断标志位|中断处理函数|
|---|---|---|
|PA0~PG0|EXTI0|EXTI0_IRQHandler|
|PA1~PG1|EXTI1|EXTI1_IRQHandler|
|PA2~PG2|EXTI2|EXTI2_IRQHandler|
|PA3~PG3|EXTI3|EXTI3_IRQHandler|
|PA4~PG4|EXTI4|EXTI4_IRQHandler|
|PA5~PG5|EXTI5|EXTI9_5_IRQHandler|
|PA6~PG6|EXTI6|
|PA7~PG7|EXTI7|
|PA8~PG8|EXTI8|
|PA9~PG9|EXTI9|
|PA10~PG10|EXTI10|EXTI15_10_IRQHandler|
|PA11~PG11|EXTI11|
|PA12~PG12|EXTI12|
|PA13~PG13|EXTI13|
|PA14~PG14|EXTI14|
|PA15~PG15|EXTI15|

### EXTI

外部中断/事件控制器包含多达23个用于产生事件/中断请求的边沿检测器。每根输入线都可以单独进行配置，以选择类型和相应的触发事件（上升沿，下降沿或边沿触发）。每根输入线还可以单独屏蔽。挂起寄存器用于保持中断请求的状态线。
![[../../ASLant_Files/ac63aafbe918ddb4440295beb5290717_MD5.gif]]

#### 引脚分组

1. 尾号相同的引脚一组，接入1个外部中断线
    
2. 同组引脚只能有一个设置为外部中断功能
    

#### 中断通道

1. EXTI0~EXTI4分别具有独立的中断通道
    
2. EXTI5~EXTI9共享同一个中断通道
    
3. EXTI10~EXTI15共享同一个中断通道
    

#### 外部中断的触发方式

1. 上升沿触发
    
2. 下降沿触发
    
3. 双边沿触发
    

### 外部中断初始化

1. CubeMX 配置时钟和中断引脚
    PB0设置为GPIO_EXTI0（ PA0不能和PB0同时设置为外部中断，只能选一）
    PB1设置为GPIO_EXTI1
    PB2设置为GPIO_EXTI2
    
2. 设置中断触发条件，进入System Core->GPIO设置，GPIO mode设置为上升沿触发（松手检测），上拉
    
3. 设置NVIC使能，进行System Core->NVIC，三个中断线全部Enabled上打勾，设置中断优先级，这里由于选择的是第四组，所以只需要设置抢占优先级，不配置就按中断向量表的顺序来执行
    
4. 生成项目文件，点击stm32g4xx_it.c 编写中断处理函数 EXTI0_IRQHandler()等
    
5. 1
    

### 实验：B1，B2，B3按键分别控制LED，LED2，LED3，其它LED灯保持熄灭

中断处理函数在stm32g4xx_it.c中，其中又调用了 __weak void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)，此函数可以在其它地方，如main.c 中去掉__weak，重新定义并生效，原来的__weak函数自动失效
参考代码：
```c
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin) // 函数中不能使用
    HAL_Delay(10);
{
    switch (GPIO_Pin)
    {
    case GPIO_PIN_0:
    {
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_8, GPIO_PIN_RESET);
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_9 | GPIO_PIN_10 | GPIO_PIN_11 | GPIO_PIN_12 | GPIO_PIN_13 | GPIO_PIN_14 | GPIO_PIN_15, GPIO_PIN_SET);
        HAL_GPIO_WritePin(GPIOD, GPIO_PIN_2, GPIO_PIN_SET);
        HAL_GPIO_WritePin(GPIOD, GPIO_PIN_2, GPIO_PIN_RESET);
        break;
    }
    case GPIO_PIN_1:
    {
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_9, GPIO_PIN_RESET);
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_8 | GPIO_PIN_10 | GPIO_PIN_11 | GPIO_PIN_12 | GPIO_PIN_13 | GPIO_PIN_14 | GPIO_PIN_15, GPIO_PIN_SET);
        HAL_GPIO_WritePin(GPIOD, GPIO_PIN_2, GPIO_PIN_SET);
        HAL_GPIO_WritePin(GPIOD, GPIO_PIN_2, GPIO_PIN_RESET);
        break;
    }
    case GPIO_PIN_2:
    {
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_10, GPIO_PIN_RESET);
        HAL_GPIO_WritePin(GPIOC, GPIO_PIN_8 | GPIO_PIN_9 | GPIO_PIN_11 | GPIO_PIN_12 | GPIO_PIN_13 | GPIO_PIN_14 | GPIO_PIN_15, GPIO_PIN_SET);
        HAL_GPIO_WritePin(GPIOD, GPIO_PIN_2, GPIO_PIN_SET);
        HAL_GPIO_WritePin(GPIOD, GPIO_PIN_2, GPIO_PIN_RESET);
        break;
    }
    }
}
```

考试时如果需要使用4个铵键，那么不要用中断方式，还是用之前的扫描方式（即轮询，查看电平是否为低）
### 实践作业

\_按键，LCD，LED，蜂鸣器联合实验_
按键控制LED，蜂鸣器，同时显示屏显示哪个按键被按下，哪个设备开启