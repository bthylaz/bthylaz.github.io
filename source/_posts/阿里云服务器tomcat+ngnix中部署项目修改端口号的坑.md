---
title: 阿里云服务器tomcat+ngnix中部署项目修改端口号的坑
date: 2021-08-23 20:02:27
description: 搭建网站自带的文章命令
---

## tomcat修改端口号:
1.编辑server.xml![在这里插入图片描述](https://img-blog.csdnimg.cn/73816e78a9f441e7b481751b4b988889.png)
2. 69行修改你想要的端口号计即可![在这里插入图片描述](https://img-blog.csdnimg.cn/9cc66df6dba0454a99fc64f60ac8a074.png)
3.重启tomcat

## nginx修改端口号
1. 编辑配置文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/bb822dac815d49e2ae70f3ef450df04a.png)

```c
//站点一
server {
        listen       8031;//访问端口
        server_name www.yy.cn;//访问地址
    
        location / {
            root  /home/dadada/h5/dd;//项目所在路径
            index index.html;//项目首页
        }
    }

//站点二
    server {
        listen       8030;
        server_name www.yy.cn;
    
        location / {
            root  /home/dadada/h5/dd_m;
            index index.html;
        }
    }
```
    2. 重启nginx
   
## 修改以后如果外网不能通过修改的端口号访问，则可能是以下部分没设置好
### 1. 检查实例安全组配置规则是否添加需要开放的端口，没有添加则配置规则
### 2.安全组配置了相关端口的规则还不可以从外网访问，检查ECS防火墙，是否防火墙拦截了端口
1、firewall-cmd --state（查看防火墙开启状态）
提示running则防火墙已启动
2、firewall-cmd --list-ports（查看防火墙）

如果是防火墙没有开启对应端口，可使用以下命令添加需要开放的端口
// 开放1024的端口
firewall-cmd --add-port=1024/tcp --permanent
// 重载生效刚才的端口设置
firewall-cmd --reload

firewall常用命令如下：
常用命令介绍
firewall-cmd --state ##查看防火墙状态，是否是running
firewall-cmd --reload ##重新载入配置，比如添加规则之后，需要执行此命令
firewall-cmd --get-zones ##列出支持的zone
firewall-cmd --get-services ##列出支持的服务，在列表中的服务是放行的
firewall-cmd --query-service ftp ##查看ftp服务是否支持，返回yes或者no
firewall-cmd --add-service=ftp ##临时开放ftp服务
firewall-cmd --add-service=ftp --permanent ##永久开放ftp服务
firewall-cmd --remove-service=ftp --permanent ##永久移除ftp服务
firewall-cmd --add-port=80/tcp --permanent ##永久添加80端口
iptables -L -n ##查看规则，这个命令是和iptables的相同的
man firewall-cmd ##查看帮助

### 3.查看端口号是否被其他程序占用



```bash
netstat -nultp（此处不用加端口号）该命令是查看当前所有已经使用的端口情况

1.查看端口是否被占用
netstat -anp |grep 端口号    看监控状态为LISTEN表示已经被占用

2.查看占用的进程
lsof -i:端口号

3.关闭进程
kill -9 进程PID
```

### 3. 浏览器访问：http://ip:8081




