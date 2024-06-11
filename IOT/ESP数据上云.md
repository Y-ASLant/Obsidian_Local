> [!BUG] 云平台 EMQX
> mqtt_id 必须唯一不能重复!!!

> [!question] 连接成功后：
发送 LED：0 关闭 WiFi 芯片 LED
发送 LED：1 开启 WIFI 芯片 LED

>[!success] 支持 ESP32/8266/01S 等模块
# 连接 MQTT 服务器
```c
#include <PubSubClient.h>
#include <ESP8266WiFi.h>

WiFiClient espClient;
PubSubClient client(espClient);

// WiFi连接信息
const char *wifissid = "ASLant";      // SSSID
const char *password = "1234567890a"; // Password

// MQTT服务器信息
const char *mqtt_server = "47.120.13.41";         // aslant-api.cn
const char *mqtt_id = "ESP_8266";                 // MQTT客户端ID,唯一
const char *Mqtt_sub_topic = "ESP_01s_Sub_Topic"; // 订阅消息
const char *Mqtt_pub_topic = "ESP_01s_Pub_Topic"; // 发布消息

long lastMsg = 0; // 记录上一次发布消息的时间

void setup()
{
    pinMode(2, OUTPUT);
    Serial.begin(115200);
    setup_wifi();
    client.setServer(mqtt_server, 1883);
    client.setCallback(callback);
}

void setup_wifi()
{
    Serial.println();
    Serial.print("Connecting to ");
    Serial.println(wifissid);
    WiFi.begin(wifissid, password);

    while (WiFi.status() != WL_CONNECTED)
    {
        delay(500);
        Serial.print(".");
    }

    Serial.println("");
    Serial.println("WiFi connected");
    Serial.println("IP address: ");
    Serial.println(WiFi.localIP());
}

void callback(char *topic, byte *payload, unsigned int length)
{
    String msg = "";
    String LED_set = "";

    Serial.print("Message arrived [");
    Serial.print(topic);
    Serial.print("] ");

    for (int i = 0; i < length; i++)
    {
        msg += (char)payload[i];
    }

    Serial.println(msg);

    // 检查消息中是否包含 "led"
    if (msg.indexOf("led") != -1)
    {
        // 提取LED设置数据
        int colonIndex = msg.indexOf(":");
        if (colonIndex != -1)
        {
            LED_set = msg.substring(colonIndex + 1);
            // 执行相应的命令
            if (LED_set.equals("0"))
            {
                digitalWrite(2, HIGH);
            }
            else
            {
                digitalWrite(2, LOW);
            }
        }
    }
}

void reconnect()
{
    while (!client.connected())
    {
        Serial.print("Attempting MQTT connection...");

        if (client.connect(mqtt_id))
        {
            Serial.println("connected");
            // 连接成功以后就开始订阅
            client.subscribe(Mqtt_sub_topic, 1);
        }
        else
        {
            Serial.print("failed, rc=");
            Serial.print(client.state());
            Serial.println(" try again in 5 seconds");
            delay(5000);
        }
    }
}

void loop()
{
    // 判断是否是否与服务器连接
    if (!client.connected())
    {
        reconnect(); // 连接服务器
    }
    client.loop(); // 保持通讯
}

```

# 发送指定数据到云平台
```c
#include <PubSubClient.h>
#include <ESP8266WiFi.h>

WiFiClient espClient;
PubSubClient client(espClient);

// WiFi连接信息
const char *wifissid = "ASLant";
const char *password = "1234567890a";

// MQTT服务器信息
const char *mqtt_server = "47.120.13.41";          // aslant-api.cn
const char *mqtt_id = "ESP_8266";                   // MQTT客户端ID,唯一
const char *Mqtt_sub_topic = "ESP_01s_Sub_Topic";  // 订阅消息
const char *Mqtt_pub_topic = "ESP_01s_Pub_Topic";  // 发布消息

long lastMsg = 0;  // 记录上一次发布消息的时间
char msg[50];
int value = 0;

void setup() {
  pinMode(2, OUTPUT);
  Serial.begin(115200);
  setup_wifi();
  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
}

void setup_wifi() {
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(wifissid);
  WiFi.begin(wifissid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}

void callback(char *topic, byte *payload, unsigned int length) {
  String msg = "";
  String LED_set = "";

  Serial.print("Message arrived [");
  Serial.print(topic);
  Serial.print("] ");

  for (int i = 0; i < length; i++) {
    msg += (char)payload[i];
  }

  Serial.println(msg);

  // 检查消息中是否包含 "led"
  if (msg.indexOf("led") != -1) {
    // 提取LED设置数据
    int colonIndex = msg.indexOf(":");
    if (colonIndex != -1) {
      LED_set = msg.substring(colonIndex + 1);
      // 执行相应的命令
      if (LED_set.equals("0")) {
        digitalWrite(2, HIGH);
      } else {
        digitalWrite(2, LOW);
      }
    }
  }
}

void reconnect() {
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");

    if (client.connect(mqtt_id)) {
      Serial.println("connected");
      // 连接成功以后就开始订阅
      client.subscribe(Mqtt_sub_topic, 1);
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      delay(5000);
    }
  }
}

void loop() {
  // 判断是否是否与服务器连接
  if (!client.connected()) {
    reconnect();  // 连接服务器
  }
  client.loop();  // 保持通讯

  long now = millis();
  if (now - lastMsg > 2000) {  // 每2秒发布一次消息
    lastMsg = now;
    ++value;
    snprintf (msg, 50, "humi:50%% \ntemp:27℃");
    Serial.print("Publish message: ");
    Serial.println(msg);
    client.publish(Mqtt_pub_topic, msg);

  }
}
```

