# 基于openCV的简易人脸识别系统

> 20组 - Project_1

### 小组概况：

小组成员：王绎豪、孙达、孙博辰、刘开鹏、刘培翔

小组导师：赵永瑞（赵导yyds）

---

### 项目介绍：

本项目通过**调用 openCV 的开源人脸识别AI模型**，利用其API接口，连接起电脑默认摄像头的视频流，从而借助该人脸识别模型完成了几个简易的小功能：

- 识别视频内的人脸，并返回人脸个数，显示在UI界面中：

![Alt pic](https://github.com/Yukiiceeee/Pictures/blob/master/%E5%8A%9F%E8%83%BD1%E7%A4%BA%E4%BE%8B.jpg?raw=true "功能1示例")

- 在第一步识别人脸的基础上，加入“换脸”功能（用图像覆盖人脸矩形框，实现简易的“换脸”）：

![Alt pic](https://github.com/Yukiiceeee/Pictures/blob/master/%E5%8A%9F%E8%83%BD2%E7%A4%BA%E4%BE%8B.jpg?raw=true "功能2示例")

- 在第一步人脸识别的基础上，加入“打马赛克”功能。（这里比较丑陋，就不展示啦，有兴趣的可以自己装一下试试看）

**怎么样？是不是觉得还有那么点意思呢？**

---

### 代码思路：

这里介绍一下构建本项目的代码设计思路，有兴趣的可以借助我们的源代码一起简要看一下。

**原型构建思路：**

1. **连接视频流：**通过`cv2.VideoCapture`方法获取视频流，参数`0`表示使用默认摄像头。

2. **调用人脸识别AI模型：**设置一个`face_detector`变量，利用openCV的人脸识别模型，创建一个`cv2.CascadeClassifier`对象，加载用于人脸识别的分类器模型文件。

3. **呈现视频：**利用一个无限的`while`循环，在这个循环里：

   首先使用`window.read(timeout=0)`来读取窗口事件和值。如果关闭了窗口，则循环结束。

   然后，调用`video.read()`方法读取一帧视频。将帧进行镜像翻转，以避免水平翻转的感觉。然后将帧转换为灰度图像，以便后续进行人脸检测。

   使用`face_detector.detectMultiScale`方法对灰度图像进行人脸检测，返回检测到的人脸位置和大小。

4. **反映人脸识别结果：**将检测到的人脸位置和大小通过绘制矩形框的形式来呈现出来。

5. **反映人脸个数：**利用`face_detector.detectMultiScale`方法，传递方法的`len`值以表示人脸个数，并在画面中呈现出来。

6. **更新界面：**最后，更新界面中的图像显示区域和文本框的内容。如果点击了停止按钮(`event == '-STOP-'`)，则循环结束，并关闭窗口。

**功能实现思路：**

​		在原型的基础上，对矩形框内的内容进行小修改，以实现简易的“打马赛克”和“换脸”功能。

---

### 项目安装：

本项目由于调用了openCV的开源AI模型，因此在使用该项目时，有几个需要注意的地方：

- 直接克隆项目仓库到本地。首先在选择要克隆的文件夹下打开`cmd`命令行；

  然后输入以下克隆指令：`git clone + 仓库地址`

​		其中，仓库地址直接复制github仓库里的SSH然后黏贴在上述位置。

![Alt pic](https://github.com/Yukiiceeee/Pictures/blob/master/%E5%85%8B%E9%9A%86%E4%BB%93%E5%BA%93.jpg?raw=true "github仓库")

- 接着，需要先下载安装openCV自带的python库与PySimpleGUI库。

  `win + R`打开`cmd`命令行，输入以下指令：

  `pip install cv2` 与 `pip install PySimpleGUI`

​		注意：1.必须先确保电脑上有正确的python路径，并保证pip更新到最新。

​					2.OPENCV的模型库为3.4.7，一定要解压到D盘的主目录，要不然配置起来可能很麻烦，因为调模型库需要绝对地址，所以这样是最快可以将这个代码跑起来的方法。（牛逼的大佬当我没说）

---

### 项目想法：

> 教室目前存在的一些问题：

尽管目前的空教室查询系统能够查询到空教室，但是也仅仅是“没有申请借用”的教室。

实际上，由于目前学校图书馆尚未建成，有大量的同学们前往教室进行自习。因此，尽管一些教室是“空教室”，但是仍有很大可能教室内存在着在此自习的同学。如果要找一个“空教室”开一个小型会议或小型集体活动，在不借用教室的前提下还是很难找到“没有人的教室”的。

况且，学校申请空教室的审批需要不少时间批下来，这给同学们实际找真正的“没有人的教室”来进行小型会议等活动带来了困扰。

> 项目后续的一些打算：

本项目目前实现了基本的功能，做出了一个demo原型。

后续小组设想能够进一步开发与完善对应功能，与学校教室的摄像头进行对接，并能够通过识别教室内的人脸个数或其它变量来反映出教室的现有人数。

这样，就能够实时显示教室人数，并在文理楼大屏幕上呈现出来，从而帮助同学们快速找到“真正没有人”的教室啦！

---

#### 如有相应想法或者提议意见，欢迎随时联系！

王绎豪

联系方式：13336340366

微信：wangyihao8020978

孙博辰

联系方式：15701307665

微信：Micheal024
