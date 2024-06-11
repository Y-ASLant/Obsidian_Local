> [!BUG] ESP_01s 隶属于 ESP8266 系列
> ![[ASLant_Images/b96447f3f544a9a8fbb49452ea474cb9_MD5.jpg]]
[[ASLant_Images/b96447f3f544a9a8fbb49452ea474cb9_MD5.jpg|Open: b96447f3f544a9a8fbb49452ea474cb9_MD5.jpg]]
### ESP_01s工作模式

ESP_01s 支持 STA、AP、AP+STA **三种**工作模式。

- **STA 模式**（Station）

一般用于远距离传输。ESP_01s 通过路由器连接互联网，终端设备通过互联网实现对设备的远程控制。简单来说，此时的 ESP_01s 可以当作是一个客户端，可以向服务端进行数据的下载与传输。这就类似于，手机/平板/笔记本（客户端）可以通过 WIFI 连接到路由器进行上网。

- **AP 模式**（Access Point）

一般用于近距离传输。ESP_01s 作为热点，提供无线接入服务、数据访问，一般的无线路由/网桥工作在 AP 模式下，最多支持 4 台设备接入。简单来说，此时的 ESP01s 可以当作是一个服务端。这就类似于，ESP01s 变身为一个路由器，然后手机/平板/笔记本可以通过 WIFI 连接到 ESP01s 进行上网。

- **AP+STA** 模式

两种模式的共存模式，可以通过互联网控制可实现无缝切换，方便操作。简单来说，此时的 ESP_01s 可以当作是一个路由器既可以做服务端接收也可以当客户端连接路由器，进行联网传输和控制。
# STM 32 驱动
> [!BUG] Drivers

### `esp01s.h`

```c
#ifndef __ESP01S_H__
#define __ESP01S_H__

#include <stdint.h>
#include "stdio.h"
#include "string.h"
#include "delay.h"
#include "usart.h"
#include <stdarg.h> //可变数组

extern UART_HandleTypeDef g_uart_handle;

/* 引脚定义 */
#define ESP_01s_UART_TX_GPIO_PORT           GPIOA
#define ESP_01s_UART_TX_GPIO_PIN            GPIO_PIN_2
#define ESP_01s_UART_TX_GPIO_CLK_ENABLE()   do{ __HAL_RCC_GPIOA_CLK_ENABLE(); }while(0) /* PC口时钟使能 */

#define ESP_01s_UART_RX_GPIO_PORT           GPIOA
#define ESP_01s_UART_RX_GPIO_PIN            GPIO_PIN_3
#define ESP_01s_UART_RX_GPIO_CLK_ENABLE()   do{ __HAL_RCC_GPIOA_CLK_ENABLE(); }while(0) /* PD口时钟使能 */

#define ESP_01s_UART_INTERFACE              USART2
#define ESP_01s_UART_IRQn                   USART2_IRQn
#define ESP_01s_UART_IRQHandler             USART2_IRQHandler
#define ESP_01s_UART_CLK_ENABLE()           do{ __HAL_RCC_USART2_CLK_ENABLE(); }while(0) /* UART2时钟使能 */

/* UART收发缓冲大小 */
#define ESP_01s_UART_RX_BUF_SIZE            128
#define ESP_01s_UART_TX_BUF_SIZE            64

/* 错误代码 */
#define ESP_01s_EOK                         0   /* 没有错误 */
#define ESP_01s_ERROR                       1   /* 通用错误 */
#define ESP_01s_ETIMEOUT                    2   /* 超时错误 */
#define ESP_01s_EINVAL                      3   /* 参数错误 */

/* 工作模式 */
#define ESP_01s_STA_MODE                    1
#define ESP_01s_AP_MODE                     2
#define ESP_01s_STA_AP_MODE                 3

#define WIFI_SSID                           "ASLant"
#define WIFI_PWD                            "1234567890a"

#define TCP_SERVER_IP                       "47.120.13.41"
#define TCP_SERVER_PORT                     "1883"

uint8_t ESP_01s_init(uint32_t baudrate);
void ESP_01s_clear(void);
void ESP_01s_uart_printf(char *fmt, ...);
#endif

```
### `esp01s.c`

```c
#include "esp01s.h"

UART_HandleTypeDef g_uart_handle;
uint8_t g_uart_rx_buf[ESP_01s_UART_RX_BUF_SIZE];
uint8_t g_uart_tx_buf[ESP_01s_UART_TX_BUF_SIZE];
uint16_t ESP_01s_cnt = 0, ESP_01s_cntPre = 0;

/**
 * @brief       ESP_01s UART初始化
 * @param       baudrate: UART通讯波特率
 * @retval      无
 */
void ESP_01s_uart_Init(uint32_t baudrate)
{
    g_uart_handle.Instance          = ESP_01s_UART_INTERFACE;       /* ESP_01s UART */
    g_uart_handle.Init.BaudRate     = baudrate;                     /* 波特率 */
    g_uart_handle.Init.WordLength   = UART_WORDLENGTH_8B;           /* 数据位 */
    g_uart_handle.Init.StopBits     = UART_STOPBITS_1;              /* 停止位 */
    g_uart_handle.Init.Parity       = UART_PARITY_NONE;             /* 校验位 */
    g_uart_handle.Init.Mode         = UART_MODE_TX_RX;              /* 收发模式 */
    g_uart_handle.Init.HwFlowCtl    = UART_HWCONTROL_NONE;          /* 无硬件流控 */
    g_uart_handle.Init.OverSampling = UART_OVERSAMPLING_16;         /* 过采样 */
    HAL_UART_Init(&g_uart_handle);                                  /* 使能ESP_01s UART */
}

/**
 * @brief       ESP_01s UART中断回调函数
 * @param       无
 * @retval      无
 */
void ESP_01s_UART_IRQHandler(void)
{
    uint8_t receive_data = 0;
    if(__HAL_UART_GET_FLAG(&g_uart_handle, UART_FLAG_RXNE) != RESET) {
        if(ESP_01s_cnt >= sizeof(g_uart_rx_buf))
            ESP_01s_cnt = 0; //防止串口被刷爆
        HAL_UART_Receive(&g_uart_handle, &receive_data, 1, 1000);//串口2接收1位数据
        g_uart_rx_buf[ESP_01s_cnt++] = receive_data;
    }
    HAL_UART_IRQHandler(&g_uart_handle);
}

/**
 * @brief       ESP_01s 循环调用检测是否接收完成
 * @param       无
 * @retval      ESP_01s_EOK-接收完成ESP_01s_ERROR-接收超时未完成
 */
uint8_t ESP_01s_wait_receive(void)
{

    if(ESP_01s_cnt == 0) //如果接收计数为0 则说明没有处于接收数据中，所以直接跳出，结束函数
        return ESP_01s_ERROR;

    if(ESP_01s_cnt == ESP_01s_cntPre) {//如果上一次的值和这次相同，则说明接收完毕
        ESP_01s_cnt = 0;//清0接收计数
        return ESP_01s_EOK;//返回接收完成标志
    }

    ESP_01s_cntPre = ESP_01s_cnt;//置为相同
    return ESP_01s_ERROR;//返回接收未完成标志
}

/**
 * @brief       ESP_01s 清空串口接收缓存
 * @param       无
 * @retval      无
 */
void ESP_01s_clear(void)
{
    memset(g_uart_rx_buf, 0, sizeof(g_uart_rx_buf));
    ESP_01s_cnt = 0;
}

/**
 * @brief       ESP_01s 发送命令
 * @param       cmd-待发送的AT命令，res-期待接收到的字符串
 * @retval      ESP_01s_EOK-成功  ESP_01s_ERROR-失败
 */
uint8_t ESP_01s_send_command(char *cmd, char *res)
{

    uint8_t timeOut = 250;

    ESP_01s_clear();
    HAL_UART_Transmit(&g_uart_handle, (unsigned char *)cmd, strlen((const char *)cmd), 100);

    while(timeOut--) {
        if(ESP_01s_wait_receive() == ESP_01s_EOK) {//如果收到数据
            if(strstr((const char *)g_uart_rx_buf, res) != NULL)//如果检索到关键词
                return ESP_01s_EOK;
        }
        Delay_ms(10);
    }

    return ESP_01s_ERROR;

}

/**
 * @brief       ESP_01s恢复出厂设置
 * @param       无
 * @retval      ESP_01s_EOK  : 恢复出场设置成功
 *              ESP_01s_ERROR: 恢复出场设置失败
 */
uint8_t ESP_01s_restore(void)
{
    return ESP_01s_send_command("AT+RESTORE", "ready");
}

/**
 * @brief       ESP_01s AT指令测试
 * @param       无
 * @retval      ESP_01s_EOK  : AT指令测试成功
 *              ESP_01s_ERROR: AT指令测试失败
 */
uint8_t ESP_01s_at_test(void)
{
    return ESP_01s_send_command("AT\r\n", "OK");
}

/**
 * @brief       设置ESP_01s工作模式
 * @param       mode: 1，Station模式
 *                    2，AP模式
 *                    3，AP+Station模式
 * @retval      ESP_01s_EOK   : 工作模式设置成功
 *              ESP_01s_ERROR : 工作模式设置失败
 *              ESP_01s_EINVAL: mode参数错误，工作模式设置失败
 */
uint8_t ESP_01s_set_mode(uint8_t mode)
{
    switch (mode) {
    case ESP_01s_STA_MODE:
        return ESP_01s_send_command("AT+CWMODE=1\r\n", "OK");    /* Station模式 */

    case ESP_01s_AP_MODE:
        return ESP_01s_send_command("AT+CWMODE=2\r\n", "OK");    /* AP模式 */

    case ESP_01s_STA_AP_MODE:
        return ESP_01s_send_command("AT+CWMODE=3\r\n", "OK");    /* AP+Station模式 */

    default:
        return ESP_01s_EINVAL;
    }
}

/**
 * @brief       ESP_01s软件复位
 * @param       无
 * @retval      ESP_01s_EOK  : 软件复位成功
 *              ESP_01s_ERROR: 软件复位失败
 */
uint8_t ESP_01s_sw_reset(void)
{
    return ESP_01s_send_command("AT+RST\r\n", "OK");
}

/**
 * @brief       ESP_01s设置回显模式
 * @param       cfg: 0，关闭回显
 *                   1，打开回显
 * @retval      ESP_01s_EOK  : 设置回显模式成功
 *              ESP_01s_ERROR: 设置回显模式失败
 */
uint8_t ESP_01s_ate_config(uint8_t cfg)
{
    switch (cfg) {
    case 0:
        return ESP_01s_send_command("ATE0\r\n", "OK");   /* 关闭回显 */

    case 1:
        return ESP_01s_send_command("ATE1\r\n", "OK");   /* 打开回显 */

    default:
        return ESP_01s_EINVAL;
    }
}

/**
 * @brief       ESP_01s连接WIFI
 * @param       ssid: WIFI名称
 *              pwd : WIFI密码
 * @retval      ESP_01s_EOK  : WIFI连接成功
 *              ESP_01s_ERROR: WIFI连接失败
 */
uint8_t ESP_01s_join_ap(char *ssid, char *pwd)
{
    char cmd[64];

    sprintf(cmd, "AT+CWJAP=\"%s\",\"%s\"\r\n", ssid, pwd);

    return ESP_01s_send_command(cmd, "WIFI GOT IP");
}

/**
 * @brief       ESP_01s获取IP地址
 * @param       buf: IP地址，需要16字节内存空间
 * @retval      ESP_01s_EOK  : 获取IP地址成功
 *              ESP_01s_ERROR: 获取IP地址失败
 */
uint8_t ESP_01s_get_ip(char *buf)
{
    char *p_start;
    char *p_end;

    if (ESP_01s_send_command("AT+CIFSR\r\n", "STAIP") != ESP_01s_EOK)
        return ESP_01s_ERROR;

    p_start = strstr((const char *)g_uart_rx_buf, "\"");
    p_end = strstr(p_start + 1, "\"");
    *p_end = '\0';
    sprintf(buf, "%s", p_start + 1);

    return ESP_01s_EOK;
}

/**
 * @brief       ESP_01s连接TCP服务器
 * @param       server_ip  : TCP服务器IP地址
 *              server_port: TCP服务器端口号
 * @retval      ESP_01s_EOK  : 连接TCP服务器成功
 *              ESP_01s_ERROR: 连接TCP服务器失败
 */
uint8_t ESP_01s_connect_tcp_server(char *server_ip, char *server_port)
{
    char cmd[64];

    sprintf(cmd, "AT+CIPSTART=\"TCP\",\"%s\",%s\r\n", server_ip, server_port);

    return ESP_01s_send_command(cmd, "CONNECT");
}

/**
 * @brief       ESP_01s断开TCP服务器
 * @param       无
 * @retval      ESP_01s_EOK  : 断开TCP服务器成功
 *              ESP_01s_ERROR: 断开TCP服务器失败
 */
uint8_t ESP_01s_disconnect_tcp_server(void)
{
    return ESP_01s_send_command("AT+CIPCLOSE\r\n", "");

}

/**
 * @brief       ESP_01s进入透传
 * @param       无
 * @retval      ESP_01s_EOK  : 进入透传成功
 *              ESP_01s_ERROR: 进入透传失败
 */
uint8_t ESP_01s_enter_unvarnished(void)
{
    uint8_t ret;

    ret  = ESP_01s_send_command("AT+CIPMODE=1\r\n", "OK");
    ret += ESP_01s_send_command("AT+CIPSEND\r\n", ">");
    if (ret == ESP_01s_EOK)
        return ESP_01s_EOK;
    else
        return ESP_01s_ERROR;
}

/**
 * @brief       ESP_01s退出透传
 * @param       无
 * @retval      ESP_01s_EOK  : 退出透传成功
 *              ESP_01s_ERROR: 退出透传失败
 */
uint8_t ESP_01s_exit_unvarnished(void)
{
    return ESP_01s_send_command("+++", "");

}

/**
 * @brief       ESP_01s进入单连接
 * @param       无
 * @retval      ESP_01s_EOK  : 进入单连接成功
 *              ESP_01s_ERROR: 进入单连接失败
 */
uint8_t ESP_01s_single_connection(void)
{
    return ESP_01s_send_command("AT+CIPMUX=0\r\n", "OK");
}

/**
 * @brief       ESP_01s初始化
 * @param       baudrate: ESP_01s UART通讯波特率
 * @retval      ESP_01s_EOK  : ESP_01s初始化成功，函数执行成功
 *              ESP_01s_ERROR: ESP_01s初始化失败，函数执行失败
 */
uint8_t ESP_01s_init(uint32_t baudrate)
{
    char ip_buf[16];

    ESP_01s_uart_Init(baudrate);                /* ESP_01s UART初始化 */

    /* 让WIFI退出透传模式 */
    while(ESP_01s_exit_unvarnished())
        Delay_ms(500);

    printf("1.AT\r\n");
    while(ESP_01s_at_test())
        Delay_ms(500);

    printf("2.RST\r\n");
    while(ESP_01s_sw_reset())
        Delay_ms(500);
    while(ESP_01s_disconnect_tcp_server())
        Delay_ms(500);

    printf("3.CWMODE\r\n");
    while(ESP_01s_set_mode(ESP_01s_STA_MODE))
        Delay_ms(500);

    printf("4.AT+CIPMUX\r\n");  //设置单路连接模式，透传只能使用此模式
    while(ESP_01s_single_connection())
        Delay_ms(500);

    printf("5.CWJAP\r\n");      //连接WIFI
    while(ESP_01s_join_ap(WIFI_SSID, WIFI_PWD))
        Delay_ms(1000);

    printf("6.CIFSR\r\n");
    while(ESP_01s_get_ip(ip_buf))
        Delay_ms(500);

    printf("ESP_01s IP: %s\r\n", ip_buf);

//    printf("7.CIPSTART\r\n");
//    while(ESP_01s_connect_tcp_server(TCP_SERVER_IP, TCP_SERVER_PORT))
//        Delay_ms(500);
//
//    printf("8.CIPMODE\r\n");
//    while(ESP_01s_enter_unvarnished())
//        Delay_ms(500);

    printf("ESP_01s_Init OK\r\n");
    return ESP_01s_EOK;
}

/**
 * @brief       ESP_01s UART printf
 * @param       fmt: 待打印的数据
 * @retval      无
 */
void ESP_01s_uart_printf(char *fmt, ...)
{
    va_list ap;
    uint16_t len;

    va_start(ap, fmt);
    vsprintf((char *)g_uart_tx_buf, fmt, ap);
    va_end(ap);

    len = strlen((const char *)g_uart_tx_buf);
    HAL_UART_Transmit(&g_uart_handle, g_uart_tx_buf, len, HAL_MAX_DELAY);
}
```

# 测试 AT 指令

![[../ASLant_Images/2024-06-04-21-24-17.png]]