# WebServer
用C++实现的高性能web服务器，经过webbenchh压力测试可以实现上万的QPS

## 功能
1.利用IO复用技术epoll与线程池实现多线程的模拟Proactor高并发模型；

2.利用状态机解析HTTP请求报文，实现处理静态资源的请求

3.基于双链表实现的定时器，关闭超时的非活动连接；（TODO：小根堆）


## 压力测试

![Screenshot_20220825_213132](https://user-images.githubusercontent.com/82313079/186679723-070edc6a-6190-4037-b477-ae0577ea14ff.png)


Webbench 是 Linux 上一款知名的、优秀的 web 性能压力测试工具。它是由Lionbridge公司开发
> 测试处在相同硬件上,不同服务的性能以及不同硬件上同一个服务的运行状况。
展示服务器的两项内容:每秒钟响应请求数和每秒钟传输数据量。

基本原理:Webbench 首先 fork 出多个子进程,每个子进程都循环做 web 访问测试。

子进程把访问的结果通过pipe 告诉父进程,父进程做最终的统计结果。

```
webbench -c 1000 -t 30 http://192.168.110.129:10000/index.html
参数:
-c 表示客户端数
-t 表示时间
```
