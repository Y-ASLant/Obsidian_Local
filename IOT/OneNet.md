# 准备

> [!success] [Download Token Tools](https://open.iot.10086.cn/college/video/onenet-portal/2024-04-19/17134946071850.exe)

![[../ASLant_Files/d5080ab26c71f5f92f8ba608ac18a570_MD5.jpg]]
![[../ASLant_Files/6238dd3b17383b08462ca7635cf2c463_MD5.jpg]]

# Token 获取
1. 更换自己的 Product_ID 和 Devices_ID
```c
products/Product_ID/devices/Devices_ID
```

2.  [获取时间戳](https://tool.lu/timestamp/)**时间必须大于当前时间建议直接 2050 年**
   
3.  填入密钥 Key

4. 生成 Token
   
   ![[../ASLant_Files/57f8adac1f4255015cfdb11cc8d2fa24_MD5.jpg]]

# OneNet_2

> [!ERROR] 需要更改
> - WiFi 信息
> - product_id
> - device_id
> - token
> - 以及 56 行 String topic = "$sys/**Product_ID**/**Devices_ID**/thing/property/post";

> [!success] [代码+库下载](https://aslant.top/Cloud/OneDrive/Other/sketch_may02a.7z)

```c
#include <Arduino.h>
#include <ESP8266WiFi.h>
#include "PubSubClient.h"
#include <Ticker.h>
#include <ArduinoJson.h>

#define LED 2

/*******************************************************************************************************************************************************/
#define product_id "XXXXX"
#define device_id "XXXXX"
#define token "XXXXXXXXXXXXXXXXXXXXXXXXXXXX"

char* ssid = "XXXXX";
char* password = "XXXXX";

/*******************************************************************************************************************************************************/
// 2
const char* mqtt_server = "mqtts.heclouds.com";
const int mqtt_port = 1883;
#define ONENET_TOPIC_PROP_POST "$sys/" product_id "/" device_id "/thing/property/post"
#define ONENET_TOPIC_PROP_SET "$sys/" product_id "/" device_id "/thing/property/set"
#define ONENET_TOPIC_PROP_POST_REPLY "$sys/" product_id "/" device_id "/thing/property/post/reply"
#define ONENET_TOPIC_PROP_SET_REPLY "$sys/" product_id "/" device_id "/thing/property/set_reply"
#define ONENET_TOPIC_PROP_FORMAT "\"id\":\"%u\",\"version\":\"1.0\",\"params\":%s}"
int postMsgId = 0;
// 3
float temp = 28.0;
int humi = 60;
bool led_Status = false;

WiFiClient espClient;
PubSubClient client(espClient);
Ticker ticker;
void LED_Flash(int time);
void WiFi_Connect();
void OneNet_Connect();
void OneNet_Prop_post();
void callback(char* topic, byte* payload, unsigned int length);

// 4
void setup() {
  pinMode(LED, OUTPUT);
  Serial.begin(115200);
  WiFi_Connect();
  ticker.attach(10, OneNet_Prop_Post);
}

void loop() {
  if (WiFi.status() != WL_CONNECTED) {
  }
  if (!client.connected()) {
    OneNet_Connect();
  }
  client.loop();
}
// 5
void LED_Flash(int time) {
  digitalWrite(LED, HIGH);  //
  delay(time);
  digitalWrite(LED, LOW);
  delay(time);
}

void WiFi_Connect() {
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    LED_Flash(500);
    Serial.println("\nConnecting  to  WiFi...");
  }
  Serial.println("Connected  to  the  WiFi  network");
  Serial.println(WiFi.localIP());
  digitalWrite(LED, HIGH);
}

// 6
void OneNet_Connect() {
  client.setServer(mqtt_server, mqtt_port);
  client.connect(device_id, product_id, token);
  if (client.connected()) {
    LED_Flash(500);
    Serial.println("connected to OneNet!");

  } else {
    Serial.println("Failed to connect to OneNet!");
  }
  client.subscribe(ONENET_TOPIC_PROP_SET);
  client.subscribe(ONENET_TOPIC_PROP_POST_REPLY);
  //client.setCallback(callback);//设置回调函数
}
// 7
void OneNet_Prop_Post() {
  if (client.connected()) {
    float temp = 26.6;
    float humi = 70.2;
    String message = "{\"id\":\"123\",\"params\":{\"temp\":{\"value\":";
    message += String(temp);
    message += "},\"humi\":{\"value\":";
    message += String(humi);
    message += "}}}";

    //8
    /*******************************************************************************************************************************************************/
    String topic = "$sys/XXXXX/XXXXX/thing/property/post";
    /*******************************************************************************************************************************************************/

    if (client.publish(topic.c_str(), message.c_str()))  //上报属性
    {
      LED_Flash(500);
      Serial.println("Post property success!");

    } else {
      Serial.println("Post property failed!");
    }
  }
}

```

# 问题 1 显示上传成功但是云平台数据上传不显示

![[../ASLant_Files/4ae5ec18f38e01f3a5e5bea0f513ac77_MD5.jpg]]

> [!BUG] 云平台必须添加两个物理模型否则不显示数据
![[ASLant_Images/1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg]]
[](../ASLant_Files/1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg)en: 1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg]]
[](../ASLant_Files/1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg)# 准备

> [!success] [Download Token Tools](https://open.iot.10086.cn/college/video/onenet-portal/2024-04-19/17134946071850.exe)

![[ASLant_Images/d5080ab26c71f5f92f8ba608ac18a570_MD5.jpg]]
![[ASLant_Images/6238dd3b17383b08462ca7635cf2c463_MD5.jpg]]

# Token 获取
1. 更换自己的 Product_ID 和 Devices_ID
```c
products/Product_ID/devices/Devices_ID
```

2.  [获取时间戳](https://tool.lu/timestamp/)**时间必须大于当前时间建议直接 2050 年**
   
3.  填入密钥 Key

4. 生成 Token
   
   ![[ASLant_Images/57f8adac1f4255015cfdb11cc8d2fa24_MD5.jpg]]

# OneNet_2

> [!ERROR] 需要更改
> - WiFi 信息
> - product_id
> - device_id
> - token
> - 以及 56 行 String topic = "$sys/**Product_ID**/**Devices_ID**/thing/property/post";

> [!success] [代码+库下载](https://aslant.top/Cloud/OneDrive/Other/sketch_may02a.7z)

```c
#include <Arduino.h>
#include <ESP8266WiFi.h>
#include "PubSubClient.h"
#include <Ticker.h>
#include <ArduinoJson.h>

#define LED 2

/*******************************************************************************************************************************************************/
#define product_id "XXXXX"
#define device_id "XXXXX"
#define token "XXXXXXXXXXXXXXXXXXXXXXXXXXXX"

char* ssid = "XXXXX";
char* password = "XXXXX";

/*******************************************************************************************************************************************************/
// 2
const char* mqtt_server = "mqtts.heclouds.com";
const int mqtt_port = 1883;
#define ONENET_TOPIC_PROP_POST "$sys/" product_id "/" device_id "/thing/property/post"
#define ONENET_TOPIC_PROP_SET "$sys/" product_id "/" device_id "/thing/property/set"
#define ONENET_TOPIC_PROP_POST_REPLY "$sys/" product_id "/" device_id "/thing/property/post/reply"
#define ONENET_TOPIC_PROP_SET_REPLY "$sys/" product_id "/" device_id "/thing/property/set_reply"
#define ONENET_TOPIC_PROP_FORMAT "\"id\":\"%u\",\"version\":\"1.0\",\"params\":%s}"
int postMsgId = 0;
// 3
float temp = 28.0;
int humi = 60;
bool led_Status = false;

WiFiClient espClient;
PubSubClient client(espClient);
Ticker ticker;
void LED_Flash(int time);
void WiFi_Connect();
void OneNet_Connect();
void OneNet_Prop_post();
void callback(char* topic, byte* payload, unsigned int length);

// 4
void setup() {
  pinMode(LED, OUTPUT);
  Serial.begin(115200);
  WiFi_Connect();
  ticker.attach(10, OneNet_Prop_Post);
}

void loop() {
  if (WiFi.status() != WL_CONNECTED) {
  }
  if (!client.connected()) {
    OneNet_Connect();
  }
  client.loop();
}
// 5
void LED_Flash(int time) {
  digitalWrite(LED, HIGH);  //
  delay(time);
  digitalWrite(LED, LOW);
  delay(time);
}

void WiFi_Connect() {
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    LED_Flash(500);
    Serial.println("\nConnecting  to  WiFi...");
  }
  Serial.println("Connected  to  the  WiFi  network");
  Serial.println(WiFi.localIP());
  digitalWrite(LED, HIGH);
}

// 6
void OneNet_Connect() {
  client.setServer(mqtt_server, mqtt_port);
  client.connect(device_id, product_id, token);
  if (client.connected()) {
    LED_Flash(500);
    Serial.println("connected to OneNet!");

  } else {
    Serial.println("Failed to connect to OneNet!");
  }
  client.subscribe(ONENET_TOPIC_PROP_SET);
  client.subscribe(ONENET_TOPIC_PROP_POST_REPLY);
  //client.setCallback(callback);//设置回调函数
}
// 7
void OneNet_Prop_Post() {
  if (client.connected()) {
    float temp = 26.6;
    float humi = 70.2;
    String message = "{\"id\":\"123\",\"params\":{\"temp\":{\"value\":";
    message += String(temp);
    message += "},\"humi\":{\"value\":";
    message += String(humi);
    message += "}}}";

    //8
    /*******************************************************************************************************************************************************/
    String topic = "$sys/XXXXX/XXXXX/thing/property/post";
    /*******************************************************************************************************************************************************/

    if (client.publish(topic.c_str(), message.c_str()))  //上报属性
    {
      LED_Flash(500);
      Serial.println("Post property success!");

    } else {
      Serial.println("Post property failed!");
    }
  }
}

```

# 问题 1 显示上传成功但是云平台数据上传不显示

![[ASLant_Images/4ae5ec18f38e01f3a5e5bea0f513ac77_MD5.jpg]]

> [!BUG] 云平台必须添加两个物理模型否则不显示数据
![[ASLant_Images/1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg]]
[[ASLant_Images/1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg|Open: 1caabccbde92d745a65f9c86cca2a8f9_MD5.jpg]]

# 问题 2 WiFi 连接不上&找不到

- 将手机热点改为 2.4 GHz
- 连接 2.4 GHz WiFi
- 不要连接需要认证的校园网