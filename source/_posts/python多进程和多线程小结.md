---
title: python多进程和多线程小结
date: 2020-07-28 15:55:48
cover: ../img/c8.jpg
tags:
---
# 多线程
## 创建新线程

```python
thread.start_new_thread ( function, args[, kwargs] )
thread.start_new_thread( print_time, ("Thread-1", 2, ) )
```
- . function - 线程函数。
- . args - 传递给线程函数的参数,他必须是个tuple类型。
- . kwargs - 可选参数。
## 线程函数
- threading.currentThread(): 返回当前的线程变量。
- threading.enumerate(): 返回一个包含正在运行的线程的list。正在运行指线程启动后、结束前，不包括启动前和终止后的线程。
- threading.activeCount(): 返回正在运行的线程数量，与len(threading.enumerate())有相同的结果。
- run(): 用以表示线程活动的方法。
- start():启动线程活动。
- join([time]): 等待至线程中止。这阻塞调用线程直至线程的join() 方法被调用中止-正常退出或者抛出未处理的异常-或者是可选的超时发生。
- isAlive(): 返回线程是否活动的。
- getName(): 返回线程名。
- setName(): 设置线程名。
## 线程同步
使用Thread对象的Lock和Rlock可以实现简单的线程同步，这两个对象都有acquire方法和release方法，对于那些需要每次只允许一个线程操作的数据，可以将其操作放到acquire和release方法之间。
## 线程优先级队列（Queue）
Python的Queue模块中提供了同步的、线程安全的队列类,这些队列都实现了锁原语，能够在多线程中直接使用。可以使用队列来实现线程间的同步。

# 多进程
跟多线程大同小异，以实践为主，先大概留个印象

ps:本篇博客  从其它网站收集整理而来，方便自己学习