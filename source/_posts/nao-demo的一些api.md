---
title: nao_demo的一些api
date: 2020-08-07 17:20:09
description: 记录nao机器人demo用到的一些api
cover: ../img/c4.png
tags:
---

## 红球

### angleinterpolationwithspeed
插值一个或多个关节到一个目标角度，使用一个最大速度的分数。每个关节只允许一个目标角。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807103055475.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### setactivecamera
为系统设置当前默认的活动摄像头。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807111810719.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### subscribe
这个函数允许从ALSoundExtractor类继承的模块订阅ALAudioDevice模块。一旦订阅模块，模块的功能“进程”(模块需要包含一个)将自动和定期调用原始数据从麦克风作为输入。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807112437771.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### getdate
获取存储在内存中的键值对的值
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807144135581.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### ALRedBallDetected
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807195642546.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)

### getangles
得到关节的角度![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807144853318.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### 构造
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080715061015.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### headpitch&headyaw
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080715111262.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807194511469.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)

### setMoveArmsEnabled
获取在移动过程中是否启用臂动作。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807171759421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
### moveTo
使机器人相对于 FRAME _ robot 在地面上移动到给定的位置，这是一个阻塞调用。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807171911868.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
## mark
### isinstance
isinstance() 函数来判断一个对象是否是一个已知的类型,类似 type()


### getTransform
获取相对于 FRAME 的齐次转换。轴的定义: x 轴对于机器人的前面是正的，y 轴从右到左，z 轴是垂直的。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200807173805346.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)
## 流程
### WakeUp
如果机器人是醒着的，返回为真。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200813095927303.png#pic_center)
