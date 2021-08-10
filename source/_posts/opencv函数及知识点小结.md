---
title: opencv函数及知识点小结
date: 2020-07-24 21:41:52
description: 记录学过的一些opencv函数
cover: ../img/c6.jpg
tags:
---


# 图片
cv2.imread(‘图片位置’，读取的方式)-------------读入图像
cv2.imshow(‘名字’，‘图像’)-------------------------显示图像
cv2.waitKey()-------------------------------------键盘绑定函数
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724192806631.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
cv2.destroyAllWindows()-------------------可以轻易的删除任何我们建立的窗口
cv2.namedWindow(窗口名字，初始函数标签)----------创建窗口
> 标签为cv2.WINDOW_AUTOSIZE时不可调整大小，标签为cv2.WINDOW_NORMAL时可以调整窗口大小

cv2.imwrite(‘文件名’，图像)-----------------保存图像

# 视频
cv2.VideoCapture('参数')-----------------获取视频
> 参数为0---笔记本电脑的内置摄像头

xx.release()--------------停止捕获视频
xx.read()------------------返回一个布尔值和视频帧
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724194254328.png)
cv2.flip(frame,参数)--------------------翻转
> ‘0‘-----垂直翻转 ，’1‘-------------水平翻转

# 画图
cv2.rectangle(img,(384,0),(510,128),(0,255,0),3)----矩形
> 图像，左上角顶点，右下角顶点的坐标,颜色，厚度

cv2.putText(img,'OpenCV',(10,500), font, 4,(255,255,255),2)--------------在图片上添加文字

# 图像的基本操作
img.shape-----------------------获取图像的形状
>返回值是一个包含行数，列数，
通道数的元组

img.dtype------------------- 返回图像的数据类型.
b,g,r=cv2.split(img)-----------分割BGR通道
>cv2.split() 是一个比较耗时的操作，能用Numpy 索引索引就尽量用

img=cv2.merge(b,g,r)----------融合BGR
cv2.copyMakeBorder(src，top, bottom, left, right，borderType)---------------为图像扩边（填充）
OpenCV 中是按 BGR，matplotlib 中是按 RGB 排列

# 图像上的算术运算
cv2.add()-------------------两幅图像进行加法运算
> 两幅图像的大小，类型必须一致

cv2.addWeighted(第一幅图,权重,第二幅图,权重)------图像混合
AND，OR，NOT，XOR-----------按位操作
>当我们提取图像的
一部分，选择非矩形 ROI (感兴趣区域)时这些操作会很有用

 mask图像中黑色会被遮住，白色会显示出来
 cv2.getTickCount-----------返回从参考点到这个函数被执行的时钟数
# 图像处理
cv2.cvtColor(input_image，flag)----------颜色空间转换
> flag是转换类型,BGR↔Gray---cv2.COLOR_BGR2GRAY
> BGR↔HSV---cv2.COLOR_BGR2HSV

OpenCV 的 HSV 格式中,H（色彩/色度）的取值范围是 [0，179]，
S（饱和度）的取值范围 [0，255]，V（亮度）的取值范围 [0，255]。要记得归一化.

**找到要跟踪对象的 HSV 值**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724213602279.png)
> 现在就可以分别用 [H-100，100，100] 和 [H+100，255，255] 做上下阈值。

## 图像阈值
cv2.threshold（）-------------------------全局阈值
> 的第一个参数就是原图像，原图
像应该是灰度图。第二个参数就是用来对像素值进行分类的阈值。第三个参数就是当像素值高于（有时是小于）阈值时应该被赋予的新的像素值。第四个参数决定多种不同的阈值方法
> 返回值：第一个为 retVal，第二个就是阈值化之后的结果图像

cv2.adaptiveThreshold(灰度图,分类的阈值,方法,cv2.THRESH_BINARY,Block Size,常数)----------自适应阈值
> 阈值就等于的平均值或者加权平均值减去这个常
数。

## 图像平滑
低通滤波（LPF）帮助我们去除噪音，模糊图像。高通滤波
（HPF） 帮助我们找到图像的边缘
cv.filter2D()------------------------------对图像卷积操作
cv2.blur(img,卷积框的宽和高) ----------平均模糊
cv2.GaussianBlur(img,高斯核的宽和高,标准差)------高斯模糊
> 去除高斯噪音

cv2.medianBlur((img,卷积核大小（奇数）)---------中值模糊
> 去除椒盐噪声

cv2.bilateralFilter()--------------------------双边滤波

## 形态学转换
cv2.erode()-----------------腐蚀（去除白噪声）
cv2.dilate()-------------------膨胀（增加图像中的白色区域)
cv2.morphologyEx((img, 方法, kernel))
> 方法：cv2.MORPH_OPEN--------开运算（先进性腐蚀再进行膨胀）-----------去除噪声
> MORPH_CLOSE----------闭运算（先膨胀再腐蚀）-------填充前景物体中的小洞
> MORPH_GRADIENT------------形态学梯度（前景物体的轮廓）
> MORPH_TOPHAT----------礼帽(原始图像与进行开运算之后得到的图像的差)
> .MORPH_BLACKHAT------黑帽(进行闭运算之后得到的图像与原始图像的差)

cv2.getStructuringElement(核形状，核大小)------------结构化元素

## 图像梯度
cv2.Sobel(img,图像的深度,参数,参数,核大小)------Sobel 滤波器
cv2.Schar()--------------------------------------Schar滤波器
cv2.Laplacian(img,图像的深度)-----------拉普拉斯滤波器

## Canny边缘检测
cv2.Canny(img,minVal,maxVal)-----------------边缘检测
cv2.pyrUp()-------------从一个低分辨率小尺寸的图像向下构建一个金子塔（尺寸变大，但分辨率不会增加）
cv2.pyrDown()-------------从一个高分辨率大尺寸的图像向上构建一个金子塔（尺寸变小，分辨率降低）
# 轮廓
cv2.findContours()-----------------查找轮廓
>第一个是输入图像(二值图像)，第二个是轮廓检索模式，第三个是轮廓近似方法。
>返回值有三个，第一个是图像，第二个是轮廓，第三个是（轮廓的）层析结构。轮廓（第二个返回值）是一个 Python列表，其中存储这图像中的所有轮廓。每一个轮廓都是一个 Numpy 数组，包含对象边界点（x，y）的坐标。

cv2.drawContours()---------------------绘制轮廓
>第一个参数是原始图像，第二个参数是轮廓，一个 Python 列表。第三个参数是轮廓的索引（在绘制独立轮廓是很有用，当设置为 -1 时绘制所有轮廓）接下来的参数是轮廓的颜色和厚度
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726162603543.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)

cv2.contourArea()------------------------轮廓面积（M['m00']）

# 直方图
cv2.calcHist(images, channels, mask, histSize, ranges[, hist[, accumulate]])---------------------统计直方图![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726163413457.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
```
#img.ravel() 将图像转成一维数组，这里没有中括号。
hist,bins = np.histogram(img.ravel(),256,[0,256])
```
matplotlib.pyplot.hist()---------------------绘制直方图
## 掩模
要统计图像某个局部区域的直方图只需要构建一副掩模图像。将要统计的
部分设置成白色，其余部分为黑色，就构成了一副掩模图像
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726164121381.png)
## 直方图均衡化
cv2.equalizeHist()---------------直方图均衡化
CLAHE均衡化
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726164617197.png)
## 2D 直方图
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726165014821.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
```
hist = cv2.calcHist([hsv], [0, 1], None, [180, 256], [0, 180, 0, 256])
```
np.histogram2d()---------------------np中得直方图绘制函数
> 第一个参数是 H 通道，第二个参数是 S 通道，第三个参数是 bins 的数目，第四个参数是数值范围。

## 直方图反向投影

# 模块匹配
cv2.matchTemplate()---------在一副大图中搜寻查找模版图像位置的方法
>返回的结果是一个灰度图像，每一个像素值表示了此区域与模板的匹配程度。
cv2.minMaxLoc()--------------来找到其中的最小值和最大值的位置了。第一个值为矩形左上角的点（位置）

# Hough 直线变换
cv2.HoughLines()
>第一个参数是一个二值化图像，所以在进行霍夫变换之前要首先进行二值化，或者进行Canny 边缘检测。第二和第三个值分别代表 ρ 和 θ 的精确度。第四个参数是阈值，只有累加其中的值高于阈值时才被认为是一条直线，也可以把它看成能检测到的直线的最短长度（以像素点为单位）。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726172302823.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)

cv2.HoughLinesP()
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072617243448.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726172455718.png)
# 分水岭算法图像分割
cv2.watershed()
cv2.connectedComponents()
# GrabCut 算法进行交互式前景提取
# 对象检测
首先我们要加载需要的 XML 分类器。然后以灰度格式加载输入图像或者是视频。