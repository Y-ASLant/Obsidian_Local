# 解压 yolov5_5.0 压缩包

> [!NOTE] 环境已装好，解压即可

```sh
curl -k -L -o yolov5-5.0.tar https://aslant.top/Cloud/E5/yolo/yolov5-5.0.tar
```

```sh
tar -xvf yolov5-5.0.tar
```
# 构建数据集
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
   
5. 开始保存图片......

## 标记

### 安装工具

```python
pip install labelImg
```
### 开始打标签
1. 启动工具
   ```sh
   labelImg
   ```
2. 选择图片位置
   ![[../../ASLant_Files/2024-07-27-10-37-01.png]]

3. 更改保存位置
   ![[../../ASLant_Files/2024-07-27-10-37-43.png]]
4. 注意格式为 `yolo`, 在顶部 `view` 处勾选自动保存
5. 开始标注
6. 所需种类
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
2. 种类数量以及种类名称，以标注后为准 ![[../../ASLant_Files/2024-07-27-11-22-01.png]]
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
       parser.add_argument('--batch-size', type=int, default=1, help='total batch size for all GPUs')
       parser.add_argument('--img-size', nargs='+', type=int, default=[640, 640], help='[train, test] image sizes')
   ```

# 生成 `.pt` 模型
1. 开始训练
   ```sh
   python3 train.py
   ```
2. 等待即可
   ![[../../ASLant_Files/2024-07-27-12-52-31.png]]
3. 也可以通过 6006 端口查看
   ![[../../ASLant_Files/2024-07-27-12-51-56.png]]
4. 训练结束后会生成两个 `.pt` 文件, 在 `runs\train\exp*\weights` 目录下
   ![[../../ASLant_Files/2024-07-27-13-05-44.png]]
# TensorRT 优化模型

> [!Error] [[模型转换| 使用 TensorRT 优化模型]]
