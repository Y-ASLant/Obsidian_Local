## 题目要求
---

> INT0中断触发 LED状态

<br/>   

## 仿真图	
---

![[ASLant_Images/47979164062823b5a79177534e0e68d9_MD5.jpg]]   

> [仿真源文件](/123pan/?d=N7orVv-spMV3.html)		


<br/>   

## 源代码   
---

```c
#include <reg52.h>
sbit LED = P0 ^ 0; // 定义端口名

void main()
{
    LED = 1;     // 初始P0^0口 高电平  灯泡熄灭状态
    EA = 1;      // 中断允许总开关  为1 允许所有中断请求
    EX0 = 1;     // 允许外部中断0
    TCON = 0x01; // 外部中断0的触发方式 为1 电平触发
    while (1)
    {
        ;
    }
}

External_Interrupt_0() interrupt 0
{
    LED = ~LED; // 灯泡状态反转
}

```
<br/>

## 效果预览
----
![[ASLant_Images/ae0df0eb02943dfc95e9af769a982e43_MD5.gif]]    