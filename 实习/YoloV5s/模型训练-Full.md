# 解压 yolov5 包

> [!NOTE] 环境已装好，解压即可

```sh
unzip yolov5.zip
```
# 制作数据集
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
4. 开始保存图片



# 打标签

### 安装工具

```python
pip install labelImg
```
