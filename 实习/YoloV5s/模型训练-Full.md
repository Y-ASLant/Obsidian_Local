# InFo
> 仅在本实验中使用以下 IP

> [!important] AI-Box
> User：user
> IP：192.168.110.105
> Password：123456

> [!info] ROS 小车
> User：user  
> IP：192.168.110.131
> Password：123456

# 解压 yolov5_5.0 压缩包

> [!NOTE] 环境已装好，解压即可

```sh
curl -k -L -o yolov5-5.0.tar https://aslant.top/Cloud/E5/yolo/yolov5-5.0.tar
```
**或**
```sh
curl -kLo yolov5-5.0.tar https://aslant.top/Cloud/E5/yolo/yolov5-5.0.tar
```

```sh
tar -xvf yolov5-5.0.tar
```
# 构建数据集
### 数据采集
1. 连接小车, 密码 `123456`
   ```sh
   ssh user@192.168.110.131
   ```
2. 初始化小车所有节点
   ```sh
   roslaunch tarkbot_driver_yolo tarkbot_auto_driver.launch
   ```
3. 打开可视化工具
   ```sh
   rosrun rqt_image_view rqt_image_view
   ```
4. 创建目录,将图片以此格式放入 `train` 和 `val`
   ![[../../ASLant_Files/2024-07-27-10-24-48.png]]
   
5. 开始收集保存图片......
6. 文件保存文件夹
   ```sh
   images/train 下放训练集的图片，总图片的70%
   images/val 下放验证集的图片，总图片的15%
   images/test 下放测试集的图片，总图片的15%
   ```
   
   ```sh
   labels/train 下放训练集的标签，总标签的70%
   labels/val 下放验证集的标签，总标签的15%
   labels/test 不放东西
   ```
   ![[../../ASLant_Files/2024-07-27-14-00-36.png]]
7. 将分类好的图片发送到 AI-Box 上
   ```sh
   scp -r datasets/ user@192.168.110.105:~/
   ```

## 数据标注

> [!error] 在 AI-Box上进行标注
### 安装工具

```python
pip install labelImg
```
### 开始打标签
1. 启动工具
   ```sh
   labelImg
   ```
   或
   ```sh
   labelme
   ```
2. 选择图片位置
   ![[../../ASLant_Files/2024-07-27-10-37-01.png]]
3. 更改保存位置
   ![[../../ASLant_Files/2024-07-27-10-37-43.png]]
4. 注意格式为 `yolo`, 在顶部 `view` 处勾选自动保存
5. 开始标注...
6. 所需种类举例
   ```yaml
categories:
   [
     "Go_straight",
     "Turn_right",
     "whistle",
     "Sidewalk",
     "Limiting_velocity",
     "Shutdown",
     "School_decelerate",
     "Parking_lotB",
     "Parking_lotA",
     "Green_light",
     "Red_light",
   ]
   ```
# 训练模型
## 更改配置文件
1. 在 `data` 目录下找到 `coco128.yaml` ,复制一份, 改名为 `My-coco128.yaml`
   ![[../../ASLant_Files/2024-07-27-11-09-49.png]]
2. 种类数量以及种类名称，**以标注后为准** ![[../../ASLant_Files/2024-07-27-11-22-01.png]]
3. 修改 `My-coco128.yaml` 内容
   ```yaml
   # COCO 2017 dataset http://cocodataset.org - first 128 training images
   # Train command: python train.py --data coco128.yaml
   # Default dataset location is next to /yolov5:
   #   /parent_folder
   #     /coco128
   #     /yolov5
   
   
   # 路径修改 
   # train and val data as 1) directory: path/images/, 2) file: path/images.txt, or 3) list: [path1/images/, path2/images/]
   train: /home/user/Desktop/test-0727/datasets-test/images/train  # 128 images
   val: /home/user/Desktop/test-0727/datasets-test/images/val  # 128 images

   # 种类数量
   # number of classes
   nc: 6

   # 种类名称
   # class names
   names: [
     "Turn_right",
     "Sidewalk",
     "Limiting_velocity",
     "Shutdown",
     "School_decelerate",
     "Parking_lotB",
   ]
   ```
4. 修改 `yolov5s.yaml` 文件
   ```yaml
   # parameters
   nc: 6  # number of classes
   depth_multiple: 0.33  # model depth multiple
   width_multiple: 0.50  # layer channel multiple
   
   # anchors
   anchors:
     - [10,13, 16,30, 33,23]  # P3/8
     - [30,61, 62,45, 59,119]  # P4/16
     - [116,90, 156,198, 373,326]  # P5/32
   
   # YOLOv5 backbone
   backbone:
     # [from, number, module, args]
     [[-1, 1, Focus, [64, 3]],  # 0-P1/2
      [-1, 1, Conv, [128, 3, 2]],  # 1-P2/4
      [-1, 3, C3, [128]],
      [-1, 1, Conv, [256, 3, 2]],  # 3-P3/8
      [-1, 9, C3, [256]],
      [-1, 1, Conv, [512, 3, 2]],  # 5-P4/16
      [-1, 9, C3, [512]],
      [-1, 1, Conv, [1024, 3, 2]],  # 7-P5/32
      [-1, 1, SPP, [1024, [5, 9, 13]]],
      [-1, 3, C3, [1024, False]],  # 9
     ]
   
   # YOLOv5 head
   head:
     [[-1, 1, Conv, [512, 1, 1]],
      [-1, 1, nn.Upsample, [None, 2, 'nearest']],
      [[-1, 6], 1, Concat, [1]],  # cat backbone P4
      [-1, 3, C3, [512, False]],  # 13
   
      [-1, 1, Conv, [256, 1, 1]],
      [-1, 1, nn.Upsample, [None, 2, 'nearest']],
      [[-1, 4], 1, Concat, [1]],  # cat backbone P3
      [-1, 3, C3, [256, False]],  # 17 (P3/8-small)
   
      [-1, 1, Conv, [256, 3, 2]],
      [[-1, 14], 1, Concat, [1]],  # cat head P4
      [-1, 3, C3, [512, False]],  # 20 (P4/16-medium)
   
      [-1, 1, Conv, [512, 3, 2]],
      [[-1, 10], 1, Concat, [1]],  # cat head P5
      [-1, 3, C3, [1024, False]],  # 23 (P5/32-large)
   
      [[17, 20, 23], 1, Detect, [nc, anchors]],  # Detect(P3, P4, P5)
     ]
   ```
5. 修改 `train.py` 文件
   ```python
   # 第456行
   if __name__ == '__main__':
       parser = argparse.ArgumentParser()
       # 基于yolov5s.pt模型
       parser.add_argument('--weights', type=str, default='./weights/yolov5s.pt', help='initial weights path')
       # 配置文件位置修改
       parser.add_argument('--cfg', type=str, default='./models/yolov5s.yaml', help='model.yaml path')
       parser.add_argument('--data', type=str, default='./data/My-coco128.yaml', help='data.yaml path')
       parser.add_argument('--hyp', type=str, default='./data/hyp.scratch.yaml', help='hyperparameters path')
       # 训练轮数
       parser.add_argument('--epochs', type=int, default=500)
       parser.add_argument('--batch-size', type=int, default=8, help='total batch size for all GPUs')
       parser.add_argument('--img-size', nargs='+', type=int, default=[640, 640], help='[train, test] image sizes')
   ```

# 生成 `.pt` 模型
#### 1. 开始训练
   ```sh
   python3 train.py
   ```
#### 2. 等待即可
   ![[../../ASLant_Files/2024-07-27-12-52-31.png]]
#### 3. 也可以通过 6006 端口查看
   ![[../../ASLant_Files/2024-07-27-12-51-56.png]]
4. 训练结束后会生成两个 `.pt` 文件, 在 `runs\train\exp*\weights` 目录下
   ![[../../ASLant_Files/2024-07-27-13-05-44.png]]
# TensorRT 优化模型

###### 需要在 ROS 小车中进行, 调用 `Nvidia` 显卡

> [!Error] [[TensorRT 模型转换| 使用 TensorRT 优化模型]]


# 使用优化后的模型

> [!NOTE] 在 ROS 小车中使用优化后的模型

1. 将优化后得到的 `.engine` 模型和 `libmyplugins.so` 文件复制到 `\ros_ws\src\tarkbot_demo\tarkbot_yolov5\param\nano4G` 目录下
2. 修改 `\ros_ws\src\tarkbot_demo\tarkbot_yolov5\param\` 下 `traffic.yaml` 代码为自己的模型位置以及自己的模型种类
   ```yaml
   PLUGIN_LIBRARY: libmyplugins.so # 插件库的文件名
   engine_file_path: yolov5s.engine # 深度学习模型的引擎文件路径
   CONF_THRESH: 0.5
   IOU_THRESHOLD: 0.4
   categories:     ["Go_straight","Turn_right","whistle","Sidewalk","Limiting_velocity","Shutdown","School_decelerate","Parking_lotB","Parking_lotA","Green_light","Red_light"]
   ```

3. 在 `/home/xtark/tarkbot/ros_ws/src/tarkbot_demo/tarkbot_driver_yolo/scripts/` 下修改逻辑代码文件 `mec_driver_way.py` 和 `mec_tarkbot_auto_run.py` 
   
> [!check]- mec_tarkbot_auto_run.py
> 
> ```python
> #!/usr/bin/env python
> # coding=utf-8
> 
> import rospy
> from sensor_msgs.msg import Image
> import cv2, cv_bridge
> import numpy
> from time import sleep
> from geometry_msgs.msg import Twist
> from std_msgs.msg import Int8
> from tarkbot_driver_yolo.msg import ControlWay
> 
> last_erro=0
> 
> mask_x_left = 1.0000
> mask_x_right = 1.0000
> mask_y_top = 1.0000
> mask_y_bot = 1.0000
> center_target = 0.5
> vel_x = 0.0000
> vel_y_P = 0.0000
> vel_y_D = 0.0000
> vel_z_P = 0.0000
> vel_z_D = 0.0000
> state = 0
> 
> def nothing(s):
>     pass
> hue_black = (0,0,0,180,255,46)# black
> hue_red = (0,50,60,14,255,255)# red
> hue_blue = (100,43,46,124,255,255)# blue
> hue_green= (35,43,46,77,255,255)# green
> hue_yellow = (10,70,50,40,255,255)# yellow
> 
> 
> 
> class Follower:
>     def __init__(self):
>         self.bridge = cv_bridge.CvBridge()
> 
>         self.image_sub = rospy.Subscriber("/image_raw", Image, self.image_callback)  #订阅usb摄像头
>         self.driver_mode_sub = rospy.Subscriber("/driver_mode", ControlWay, self.driver_mode_callback)  #订阅驾驶模式
>         self.cmd_vel_pub = rospy.Publisher("/cmd_vel", Twist, queue_size=1)  #速度话题
>         self.start_flag_pub = rospy.Publisher("/start_flag", Int8, queue_size=1)  #发布启动标志
>         self.go_outside_pub = rospy.Publisher("/outside_flag", Int8, queue_size=1)  #发布出圈标志
> 
>         self.twist = Twist()
>         self.flag = Int8()
>         self.outside = Int8()
>         self.flag.data = 1
>         self.outside.data = 0
> 
>     def image_callback(self, msg):
>         global last_erro
>         global mask_x_left
>         global mask_x_right
>         global mask_y_top
>         global mask_y_bot
>         global center_target
>         global vel_x
>         global vel_y_P
>         global vel_y_D
>         global vel_z_P
>         global vel_z_D
>         global state
> 		
>         image1 = self.bridge.imgmsg_to_cv2(msg, desired_encoding='bgr8')
>         image = cv2.resize(image1, (320,240), interpolation=cv2.INTER_AREA)
>         hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
> 
>         
>         lowerbH=hue_yellow[0]
>         lowerbS=hue_yellow[1]
>         lowerbV=hue_yellow[2]
>         upperbH=hue_yellow[3]
>         upperbS=hue_yellow[4]
>         upperbV=hue_yellow[5]
> 
>         mask1=cv2.inRange(hsv,(lowerbH,lowerbS,lowerbV),(upperbH,upperbS,upperbV))
>         mask2=cv2.inRange(hsv,(lowerbH+165,lowerbS,lowerbV),(upperbH+170,upperbS,upperbV))
>         mask = cv2.bitwise_or(mask1, mask2)
> 
>         h, w, d = image.shape       
>         search_top = h*mask_y_top
>         search_bot = h*mask_y_bot
>         mask[0:int(search_top), 0:w] = 0
>         mask[int(search_bot):h, 0:w] = 0
>         mask[0:h, 0:int(mask_x_left*w)] = 0
>         mask[0:h, int(mask_x_right*w):w] = 0
>         
>         # 计算mask图像的重心，即几何中心
>         M = cv2.moments(mask)
>         if M['m00'] > 0:
>             cx = int(M['m10']/M['m00'])
>             cy = int(M['m01']/M['m00'])
>             cv2.circle(image, (cx, cy), 10, (255, 0, 255), -1)
> 
>             if cv2.circle:
>             # 计算图像中心线和目标指示线中心的距离
>                 erro = cx - w*center_target
>                 d_erro=erro-last_erro
>                 
>                 #设置前进速度
>                 self.twist.linear.x = vel_x
> 
>                 if erro!=0 and state != 0:
> 
>                     # 计算PID转向速度
>                     self.twist.angular.z = -float(erro)*vel_z_P-float(d_erro)*vel_z_D
> 
>                     # # 出内道前不转弯
>                     # if cx < 40 and cy>170 and state == 4:
>                     #     self.twist.angular.z = 0
> 
>                     # 发布内道到头，准备出圈话题
>                     if cx>95 and cx<100 and cy>160 and cy<175 and state == 4:
>                         self.outside.data = 1
>                         self.go_outside_pub.publish(self.outside)
> 
>                 elif erro == 0 and state != 0:
>                     self.twist.angular.z = 0
>                     self.twist.linear.y = 0 
> 
>                 last_erro=erro
>                 #rospy.loginfo("Point is cx%d "%cx)  
>                 #rospy.loginfo("Point is cy%d "%cy)
>                 # rospy.loginfo("Point outside is %d"%self.outside.data) 
>                 # rospy.loginfo("point state_last is %d"%state_last)
>                 # rospy.loginfo("point state is %d"%state)
>                 # rospy.loginfo("Point HSV is %s"%hsv[int(hsv.shape[0]/2),int(hsv.shape[1]/2)]) 
>         else:
>             self.twist.angular.z = 0
>         
>         if state > 0:
> 
>             #发布速度控制话题
>             self.cmd_vel_pub.publish(self.twist)
>             
>             if state == 1:  # 外部车道行驶
>                 cv2.putText(mask, "out_way", (0,30),cv2.FONT_HERSHEY_SIMPLEX, 0.7, (255,255,255),1)
>             elif state == 4:  #内部车道行驶
>                 cv2.putText(mask, "in_way", (0,30),cv2.FONT_HERSHEY_SIMPLEX, 0.7, (255,255,255),1)
>         else :
>             cv2.putText(mask, "no_line_init", (0,30),cv2.FONT_HERSHEY_SIMPLEX, 0.7, (255,255,255),1)
> 
>         cv2.imshow("watch_line", mask)
>         cv2.waitKey(1)
>         self.start_flag_pub.publish(self.flag)
> 
>     def driver_mode_callback(self, msg): 
>         global mask_x_left
>         global mask_x_right
>         global mask_y_top
>         global mask_y_bot
>         global center_target
>         global vel_x
>         global vel_y_P
>         global vel_y_D
>         global vel_z_P
>         global vel_z_D
>         global state
>         mask_x_left = msg.mask_x_left
>         mask_x_right = msg.mask_x_right
>         mask_y_top = msg.mask_y_top
>         mask_y_bot = msg.mask_y_bot
>         center_target = msg.center_target
>         vel_x = msg.vel_x
>         vel_y_P = msg.vel_y_P
>         vel_y_D = msg.vel_y_D
>         vel_z_P = msg.vel_z_P
>         vel_z_D = msg.vel_z_D
>         state = msg.en
> 
> rospy.init_node("opencv")
> follower = Follower()
> rospy.spin()
> 	```
> 

   > [!tip]- mec_driver_way.py
>    ```python
>    #!/usr/bin/env python
>    # coding=utf-8
>    
>    import rospy
>    from std_msgs.msg import Int8
>    from sensor_msgs.msg import Image
>    from std_msgs.msg import String
>    import cv2, cv_bridge
>    import numpy
>    import os
>    import sys
>    from tarkbot_driver_yolo.msg import ControlWay
>    import threading
>    import time
>    from geometry_msgs.msg import Twist
>    from tarkbot_yolov5.msg import *
>    
>    from dynamic_reconfigure.server import Server
>    from tarkbot_driver_yolo.cfg import paramsConfig
>    
>    # 巡线行驶参数
>    ring_image_x_left = 0
>    ring_image_x_right = 0.6
>    ring_image_y_top = 0.6
>    ring_image_y_bot = 0.85
>    ring_center_target = 0.20
>    ring_vel_x = 0.15
>    ring_vel_y_P = 0
>    ring_vel_y_D = 0
>    ring_vel_z_P = 0.01
>    ring_vel_z_D = 0.001
>    
>    # 启动巡线行驶标志
>    start_flag = 0
>    
>    # 内部出边标志
>    go_outside_flag = 0
>    
>    # 识别标牌标志
>    turn_flag = 0  # 左转标识
>    stop_flag = 0  # 停止标志
>    park_flag = 0  # 自动泊车标志
>    wait_flag = 0  # 停车等待标志
>    slow_flag = 0  # 降速行驶标志
>    go_straight_flag = 0  # 启动
>    
>    # 启动命令
>    stop_restart = 0  # 停止后启动
>    park_restart = 0  # 泊车后启动
>    
>    # 驾驶模式话题
>    driver_mode_pub = rospy.Publisher("/driver_mode", ControlWay, queue_size=1)
>    
>    
>    def thread_job():
>        rospy.spin()
>    
>    
>    # 开始回调
>    def start_flag_callback(msg):
>        global start_flag
>        start_flag = msg.data
>    
>    
>    # 内道转外圈回调
>    def outside_flag_callback(msg):
>        global go_outside_flag
>        go_outside_flag = msg.data
>        rospy.loginfo("Received message( %d )" % go_outside_flag)
>    
>    
>    # 泊车启动消息回调
>    def park_restart_callback(msg):
>        global park_restart
>        rospy.loginfo("Received message:%s" % msg.data)
>        if msg.data == "park_start":
>            park_restart = 1
>    
>    
>    # 停车启动消息回调
>    def stop_restart_callback(msg):
>        global stop_restart
>        rospy.loginfo("Received message:%s" % msg.data)
>        if msg.data == "stop_start":
>            stop_restart = 1
>    
>    
>    # 图像识别回调
>    def side_flag_callback(msg):
>        global turn_flag
>        global stop_flag
>        global park_flag
>        global wait_flag
>        global slow_flag
>        global go_straight_flag  # 充当绿灯
>    
>        if msg.data == []:
>            pass
>        elif msg.data[0].frame_id == "Go_straight":  # 直行_增加
>            if msg.data[0].ptx > 450 and msg.data[0].pty > 175 and msg.data[0].disth > 47: 
>                go_straight_flag = 1
>        elif msg.data[0].frame_id == "Turn_right":  # 右转标志
>            if msg.data[0].ptx > 450 and msg.data[0].pty > 175 and msg.data[0].disth > 47:
>                turn_flag = 1
>        elif msg.data[0].frame_id == "Parking_lotB" or msg.data[0].frame_id == "Parking_lotA":  # 自动泊车
>            if msg.data[0].ptx > 450 and msg.data[0].pty > 165 and msg.data[0].disth > 47:
>                park_flag = 1
>        elif msg.data[0].frame_id == "Shutdown":  # 停车标志
>            if msg.data[0].ptx > 450 and msg.data[0].pty > 175 and msg.data[0].disth > 47:
>                stop_flag = 1
>        elif msg.data[0].frame_id == "Sidewalk" or msg.data[0].frame_id == "School_decelerate":  # 学校或人行道礼让
>            if msg.data[0].ptx > 450 and msg.data[0].pty > 175 and msg.data[0].disth > 47:
>                wait_flag = 1
>        elif msg.data[0].frame_id == "Limiting_velocity":  # 限速标志，降速行驶
>            if msg.data[0].ptx > 450 and msg.data[0].pty > 175 and msg.data[0].disth > 47:
>                slow_flag = 1
>    
>    
>    def ctrl_data(tarkbot_driver_way):
>        global ring_image_x_left
>        global ring_image_x_right
>        global ring_image_y_top
>        global ring_image_y_bot
>        global ring_center_target
>        global ring_vel_x
>        global ring_vel_y_P
>        global ring_vel_y_D
>        global ring_vel_z_P
>        global ring_vel_z_D
>    
>        drivermode = ControlWay()
>    
>        # 外圈车道寻左线行驶
>        if tarkbot_driver_way == 1:
>            drivermode.mask_x_left = ring_image_x_left
>            drivermode.mask_x_right = ring_image_x_right
>            drivermode.mask_y_top = ring_image_y_top
>            drivermode.mask_y_bot = ring_image_y_bot
>            drivermode.center_target = ring_center_target
>            drivermode.vel_x = ring_vel_x
>            drivermode.vel_y_P = ring_vel_y_P
>            drivermode.vel_y_D = ring_vel_y_D
>            drivermode.vel_z_P = ring_vel_z_P
>            drivermode.vel_z_D = ring_vel_z_D
>            drivermode.en = 1
>    
>        # 内部车道寻左线行驶
>        elif tarkbot_driver_way == 2:
>            drivermode.mask_x_left = ring_image_x_left
>            drivermode.mask_x_right = ring_image_x_right
>            drivermode.mask_y_top = ring_image_y_top
>            drivermode.mask_y_bot = ring_image_y_bot
>            drivermode.center_target = ring_center_target
>            drivermode.vel_x = ring_vel_x
>            drivermode.vel_y_P = ring_vel_y_P
>            drivermode.vel_y_D = ring_vel_y_D
>            drivermode.vel_z_P = ring_vel_z_P
>            drivermode.vel_z_D = ring_vel_z_D
>            drivermode.en = 4
>        return drivermode
>    
>    
>    def reconfigCB(config, level):
>        global ring_center_target
>        global ring_vel_z_P
>        global ring_vel_z_D
>    
>        # 动态参数配置
>        ring_center_target = config.ring_center_target
>        ring_vel_z_P = config.ring_vel_z_P
>        ring_vel_z_D = config.ring_vel_z_D
>    
>        return config
>    
>    
>    def control_drive():
>        tarkbot_driver_way = 0
>        global start_flag
>        global go_outside_flag
>    
>        global turn_flag
>        global stop_flag
>        global stop_restart
>        global park_flag
>        global park_restart
>        global wait_flag
>        global slow_flag
>        global go_straight_flag
>    
>        global ring_center_target
>        global ring_vel_z_P
>        global ring_vel_z_D
>    
>        drivermode_pub = ControlWay()
>        msg = Int8()
>    
>        # 初始化节点
>        rospy.init_node("control_drive")
>    
>        # 添加进程
>        add_thread = threading.Thread(target=thread_job)
>        add_thread.start
>    
>        # 发布和订阅的话题
>        cmdvel_pub = rospy.Publisher("/cmd_vel", Twist, queue_size=1)
>        side_flag_sub = rospy.Subscriber("Yolov5object", ObjectArray, side_flag_callback)
>        start_flag_sub = rospy.Subscriber("/start_flag", Int8, start_flag_callback)
>        outside_flag_sub = rospy.Subscriber("/outside_flag", Int8, outside_flag_callback)
>        park_restart_flag_sub = rospy.Subscriber("/park_restart_flag", String, park_restart_callback)
>        stop_restart_flag_sub = rospy.Subscriber("/stop_restart_flag", String, stop_restart_callback)
>    
>        # 动态参数配置
>        dynamic_reconfigure_server = Server(paramsConfig, reconfigCB)
>        ring_center_target = rospy.get_param('~ring_center_target', 0.26)
>        ring_vel_z_P = rospy.get_param('~ring_vel_z_P', 0.01)
>        ring_vel_z_D = rospy.get_param('~ring_vel_z_D', 0.001)
>    
>        # 设置控制频率
>        rate = rospy.Rate(100)
>    
>        while not rospy.is_shutdown():
>            # 等待赛道识别完成
>            if start_flag == 1:
>                # 初始巡线
>                if tarkbot_driver_way == 0:
>                    tarkbot_driver_way = 1
>                    drivermode_pub = ctrl_data(tarkbot_driver_way)
>                    driver_mode_pub.publish(drivermode_pub)
>                    rospy.loginfo("Robot travels along the outer circle")
>    
>                # 外圈车道运行
>                elif tarkbot_driver_way == 1:
>    
>                    # 右转标识 动作
>                    if turn_flag == 1:
>                        rospy.loginfo("Robot turn right .......")
>    
>                        # 停止巡线行驶，执行右转动作
>                        car_stop = ControlWay()
>                        driver_mode_pub.publish(car_stop)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0.15
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(1.6)
>    
>                        carmove.linear.x = 0
>                        carmove.angular.z = -1.5
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(1.10)
>    
>                        carmove.linear.x = 0.15
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        park_flag = 0
>                        time.sleep(2.4)
>    
>                        rospy.loginfo("Robot turn right over, inner drivering")
>                        tarkbot_driver_way = 2  # 转入内道
>                        drivermode_pub = ctrl_data(tarkbot_driver_way)
>                        driver_mode_pub.publish(drivermode_pub)
>                        turn_flag = 0
>    
>                    # 停止标识 动作
>                    if stop_flag == 1:
>                        if stop_restart == 0 and go_straight_flag == 0:
>                            car_stop = ControlWay()
>                            driver_mode_pub.publish(car_stop)
>    
>                            carmove = Twist()
>                            carmove.linear.x = 0
>                            carmove.linear.y = 0
>                            carmove.angular.z = 0
>                            cmdvel_pub.publish(carmove)
>                            time.sleep(0.5)
>                            rospy.loginfo("停止,等待命令中...")
>    
>                        if go_straight_flag == 1:
>                            stop_restart = 0
>                            rospy.loginfo("开始直行...")
>    
>                            carmove = Twist()
>                            carmove.linear.x = 0.15
>                            carmove.linear.y = 0
>                            carmove.angular.z = 0
>                            cmdvel_pub.publish(carmove)
>                            time.sleep(2)
>    
>                            rospy.loginfo("直行信号通过...")
>    
>                            # 进入自动驾驶
>                            rospy.loginfo("进入自动驾驶...")
>                            drivermode_pub = ctrl_data(tarkbot_driver_way)
>                            driver_mode_pub.publish(drivermode_pub)
>                            stop_restart = 0
>                            stop_flag = 0
>                            go_straight_flag = 0
>                            rospy.loginfo("自动驾驶中...")
>                            tarkbot_driver_way == 0
>                            turn_flag == 0
>                            time.sleep(3)
>    
>    
>    
>                    # 学校或人行道 等待标识动作
>                    if wait_flag == 1:
>                        rospy.loginfo("Robot wait a minute")
>                        car_stop = ControlWay()
>                        driver_mode_pub.publish(car_stop)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(5)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0.15
>                        carmove.linear.y = 0
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(2.5)
>    
>                        # 进入自动驾驶
>                        rospy.loginfo("Robot travels along the outer circle")
>                        drivermode_pub = ctrl_data(tarkbot_driver_way)
>                        driver_mode_pub.publish(drivermode_pub)
>                        wait_flag = 0
>    
>                    # 降速行驶动作
>                    if slow_flag == 1:
>                        rospy.loginfo("Robot slow down driving")
>                        car_stop = ControlWay()
>                        driver_mode_pub.publish(car_stop)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0.07
>                        carmove.linear.y = 0
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(5)
>    
>                        # 进入自动驾驶
>                        rospy.loginfo("Robot travels along the outer circle")
>                        drivermode_pub = ctrl_data(tarkbot_driver_way)
>                        driver_mode_pub.publish(drivermode_pub)
>                        slow_flag = 0
>    
>                # 内部车道运行
>                elif tarkbot_driver_way == 2:
>    
>                    # 顶部右转动作
>                    if go_outside_flag == 1:
>                        # 转入外圈
>                        rospy.loginfo("Robot go outside, outer running")
>                        car_stop = ControlWay()
>                        driver_mode_pub.publish(car_stop)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0.15
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(2.6)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0
>                        carmove.angular.z = -1.5
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(0.75)
>    
>                        # 外圈行驶模式
>                        tarkbot_driver_way = 1
>                        drivermode_pub = ctrl_data(tarkbot_driver_way)
>                        driver_mode_pub.publish(drivermode_pub)
>                        go_outside_flag = 0
>    
>                    # 自动泊车动作
>                    if park_flag == 1:
>                        rospy.loginfo("Robot enters parking space")
>                        car_stop = ControlWay()
>                        driver_mode_pub.publish(car_stop)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0.15
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(2.0)
>    
>                        carmove.linear.x = 0
>                        carmove.linear.y = -0.15
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(2.1)
>    
>                        # 静止在泊车位
>                        carmove.linear.x = 0
>                        carmove.linear.y = 0
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>    
>                        rospy.loginfo("Robot is waiting for start ... ")
>                        park_flag = 0
>    
>                    # 出泊车位动作
>                    if park_restart == 1:
>                        rospy.loginfo("Robot received start,exit pack ")
>                        carmove = Twist()
>                        carmove.linear.x = 0
>                        carmove.linear.y = 0.15
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(2.6)
>    
>                        carmove = Twist()
>                        carmove.linear.x = 0.15
>                        carmove.linear.y = 0
>                        carmove.angular.z = 0
>                        cmdvel_pub.publish(carmove)
>                        time.sleep(1.2)
>    
>                        # 进入外圈行驶
>                        tarkbot_driver_way = 1
>                        drivermode_pub = ctrl_data(tarkbot_driver_way)
>                        driver_mode_pub.publish(drivermode_pub)
>                        park_restart = 0
>                        park_flag = 0
>    
>            else:
>                rospy.loginfo("Robot waiting for init ...")
>            rate.sleep()
>    
>    
>    if __name__ == '__main__':
>        try:
>            control_drive()
>        except rospy.ROSInterruptException:
>            pass
>    ```

# 小车运动
#### 1. ssh 连接小车
   ```sh
   ssh user@192.168.110.131
   ```
#### 2. 初始化小车
   ```sh
   roslaunch tarkbot_driver_yolo tarkbot_auto_driver.launch
   ```
#### 3. 等待小车初始化完毕，显示车道线弹窗后，查看图像（可省略此步）
   ```sh
   rosrun rqt_image_view rqt_image_view
   ```
#### 4. 启动小车
   ```sh
   roslaunch tarkbot_robot robot.launch
   ```
#### 5. 遇到 <font color="#00b050">Stop</font> 后，发送该话题继续行驶
   ```sh
   rostopic pub /stop_restart_flag std_msgs/String "stop_start"
   ```
#### 6. 遇到 <font color="#00b050">Park</font> 后，发送该话题将驶出车位
   ```sh
   rostopic pub /park_restart_flag std_msgs/String "park_start"
   ```

# 关机
<font color="#00b050">执行命令后，等待 20 秒，关闭电源</font>
```sh
sudo off
```


