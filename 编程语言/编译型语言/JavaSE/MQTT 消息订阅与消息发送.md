> [!BUG]  消息订阅&消息发送

# MQTT客户端之消息订阅者

```java
import org.eclipse.paho.client.mqttv3.*;
import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;

/**
 * 消息订阅者
 */
public class Subscribe {

    //代理服务器地址
    private static final String BROKER="tcp://47.120.13.41:1883";
    //客户端ID
    private static final String CLIENT_ID="Java-Client-01";

    public static void main(String[] args) throws MqttException {

        /*
            创建消息发布客户端对象
            第一个参数: 代理服务器地址
            第二个参数: 给客户端起一个唯一名字
            第三个参数: 使用MemoryPersistence进行动态消息存储,如果不给值,使用内部默认的类进行持久消息存储
         */
        MqttClient client = new MqttClient(BROKER, CLIENT_ID, new MemoryPersistence());

        //创建MQTT连接配置
        MqttConnectOptions connection = new MqttConnectOptions();
        /*
            是否清空会话session
            如果设置false那么就会保留历史session
            如果设置成true每次连接都是新的session
        */
        connection.setCleanSession(true);

        //将客户端和连接关联
        client.connect(connection);

        //设置回调函数(当发布者发布消息后被订阅者监听到,并且通过回调函数进行接收)
        client.setCallback(new MqttCallback() {
            //连接丢失
            @Override
            public void connectionLost(Throwable throwable) {
                System.out.println("连接已丢失..."+throwable.getMessage());
            }

            // 消息已送达
            @Override
            public void messageArrived(String s, MqttMessage mqttMessage) throws Exception {
                System.out.println("消息已送达...订阅的主题:"+s+" 收到的消息为:\n"+new String(mqttMessage.getPayload()));
            }

            // 消息接收完成
            @Override
            public void deliveryComplete(IMqttDeliveryToken iMqttDeliveryToken) {
                System.out.println("消息接受已完成...."+iMqttDeliveryToken.isComplete());
            }
        });

        /*
         * 订阅test主题的消息
         * subscribe消息订阅函数
         * 参数1: 要订阅的主题
         * 参数2: 服务质量,取值为 0、1、2
         */
        client.subscribe("ASLant",1); //订阅名为 ASLant 的主题
        System.out.println("消息监听开始.....");
    }
}
```

## 效果

![[../../../ASLant_Files/c268ef8deae42fb48473df16735f62ad_MD5.jpg]]

# MQTT客户端之消息发布者

```java
import org.eclipse.paho.client.mqttv3.MqttClient;
import org.eclipse.paho.client.mqttv3.MqttConnectOptions;
import org.eclipse.paho.client.mqttv3.MqttException;
import org.eclipse.paho.client.mqttv3.MqttMessage;
import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;

import java.io.UnsupportedEncodingException;
import java.nio.charset.StandardCharsets;

/**
 * 消息发布者
 */
public class Publish {
    //代理服务器地址
    private static final String BROKER="tcp://47.120.13.41:1883";
    //客户端ID
    private static final String CLIENT_ID="Java-Client-02";
    public static void main(String[] args) throws MqttException, UnsupportedEncodingException {

        /*
            创建消息发布客户端对象
            第一个参数: 代理服务器地址
            第二个参数: 给客户端起一个唯一名字
            第三个参数: 使用MemoryPersistence进行动态消息存储,如果不给值,使用内部默认的类进行持久消息存储
         */
        MqttClient client = new MqttClient(BROKER, CLIENT_ID, new MemoryPersistence());

        //创建MQTT连接配置
        MqttConnectOptions connection = new MqttConnectOptions();
        /*
            是否清空会话session
            如果设置false那么就会保留历史session
            如果设置成true每次连接都是新的session
        */
        connection.setCleanSession(true);
        //将客户端和连接关联
        client.connect(connection);

        /*
            创建消息
            调用有参构造函数进行创建,参数传一个byte数组,数组中是要发布的消息(有效载荷)
         */
        MqttMessage message = new MqttMessage("我是要发布的消息".getBytes(StandardCharsets.UTF_8));
        //设置服务质量
        message.setQos(1);
        /*
            消息发布
            第一个参数: 消息发送到哪一个主题
            第二个参数: 发送的消息对象
         */
        client.publish("ASLant",message);

        //断开连接
        client.disconnect();
        //关闭
        client.close();
    }
}
```

## 效果

![[../../../ASLant_Files/c90a097f17bca78c36419411eb716532_MD5.jpg]]

