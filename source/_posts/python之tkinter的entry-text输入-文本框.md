---
title: 'python之tkinter的entry&text输入,文本框'
date: 2020-03-04 23:54:11
tags:
cover: ../img/c9.jpg
description: tkinter的entry&text输入,文本框
---
entry&text输入,文本框
```python
import tkinter as tk
window = tk.Tk()
window.title('my window')           #设置窗口的名字
window.geometry('240x173')          #设置窗口大小


e = tk.Entry(window,show=None) #创建一个输入框，输入的东西显示
e.pack()	#让e在window上显示

def insert_point():
	#定义一个变量，把e的值获取
	var = e.get()
	#'insert'表示光标的位置，将var插入t(文本框)
	t.insert('insert',var)


def insert_end():
	#定义一个变量，把e的值获取
	var = e.get()
	#'end'表示尾部，将var插入t(文本框
	t.insert('end',var)


#创建一个button，在window上显示，button的宽15，高2，执行hit_me命令
b1 = tk.Button(window,text='insert point',width = 15,height= 2,command = insert_point)
b1.pack()
b2 = tk.Button(window,text='insert end',command = insert_end)
b2.pack()
t= tk.Text(window,height=2)
t.pack()


window.mainloop()#不断的循环程序
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200304235356603.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1NjY2MjQ4,size_16,color_FFFFFF,t_70)


自己的小结代码，相关教程：莫烦python