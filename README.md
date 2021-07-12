# loger
👋欢迎访问loger的主页, 这里的文章大部分都是利用闲暇时间记录一些Java知识点, 运维知识与实际工作中出现的问题的解决思路;

平时文章写的比较少,一些想到的地方都会记录在思维导图 [[点击跳转思维导图](https://www.processon.com/view/link/60e02e89e0b34d238be6cc98)] 中, 目前在逐步将思维导图转化为文章的形式;

有任何不懂得地方可以微信搜索 **logerJava** 或扫描下方二维码关注我的公众号,公众号内有私人联系方式, 欢迎技术交流;

<div align=center>
 <img src='https://raw.githubusercontent.com/LiuHanChao-loger/loger/main/image/qrcode_logerJava.png' width=200px height=200px />
</div>

<p align="center">
  <a href="https://github.com/LiuHanChao-loger"> <img src="https://badgen.net/badge/%E5%85%B3%E6%B3%A8/github/black"> </a>
  <a href="https://juejin.cn/user/2814381481807559"> <img src="https://badgen.net/badge/%E5%85%B3%E6%B3%A8/%E6%8E%98%E9%87%91/cyan"> </a>
  <a href="https://space.bilibili.com/20538970"> <img src="https://badgen.net/badge/%E5%85%B3%E6%B3%A8/bilibili/pink"> </a>
</p>

***

<div align=center>
 
 **Java篇指南**
 
</div>

<div align=center>
 
| 数据结构与算法 | 集合 | JVM | 设计模式 | 多线程 | Spring | 数据库| Redis | 消息队列 | 分布式 | 其他 |
| :---: | :----: | :---: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| [⬇](#数据结构与算法) | [⬇](#集合) | [⬇](#JVM) | [⬇](#设计模式) | [⬇](#多线程) | [⬇](#Spring) | [⬇](#数据库) | [⬇](#Redis) | [⬇](#消息队列) | [⬇](#分布式) | [⬇](#其他) |
 
</div>

<div align=center>
 
 **运维篇指南**
 
</div>

<div align=center>
 
| Docker | Jenkins | shell | Linux |
| :---: | :----: | :---: | :----: |
| [⬇](#Docker) | [⬇](#Jenkins) | [⬇](#shell) | [⬇](#Linux) |
 
</div>

## ⚡ Java篇

### 数据结构与算法
 - ... ...

### 集合
 - [List - 源码解析](https://mp.weixin.qq.com/s/KGWUsHNDb3fl0K-zupHnKw)
 - Map - 源码解析
 - Set - 源码解析
 - 线程安全的集合
 - ... ...

### JVM
 - [Java内存区域与垃圾收集算法](https://juejin.cn/post/6975816404314357796)
 - CMS与G1
 - 类的加载机制
 - ... ...

### 设计模式
 - [为什么要学习设计模式?](https://juejin.cn/post/6957355222788210696)
 - [工厂模式](https://juejin.cn/post/6957624699744419848)

### 多线程
 - 学习多线程,你不得不了解的基础知识
 - 多线程入门,你学会需要几分钟?
 - Java多线程中的那几把锁
 - ThreadLocal是个什么玩应?
 - 什么都用Synchronized?你确定不了解一下Atomic吗?
 - ... ...

### Spring
 - IOC,DI,AOP 都是啥?
 - bean 的生命周期
 - 循环依赖
 - Spring MVC 的工作流程
 - SpringBoot这么好,你还要配置MVC吗?
 - ... ...

### 数据库
 - 三分钟了解MySQL
 - 索引
 - 我的查询为什么这么慢?Explain分析
 - 脏读,幻读,不可重复读?
 - InnoDB的事务是怎么实现的?
 - ... ...

### Redis
 - 缓存在项目中的地位
 - Redis的数据结构
 - Redis常规操作3分钟扫盲
 - 单体,哨兵还是集群,你得Redis部署该怎么选?
 - Redis的分布式好像没那么简单
 - 深入探究,你所不知道的Redis
 - ... ...

### 消息队列
 - 什么是消息队列,在项目中处于什么地位
 - RocketMQ(火箭MQ),你想上天?
 - RocketMQ如何保证消费与高可用
 - RocketMQ一次完整的通信流程都做了什么?
 - 事务消息?
 - RocketMQ的常见问题
 - ... ...

### 分布式
 - ... ...

### 其他
 - [Swagger2生成接口文档](https://juejin.cn/post/6894950705136664589)
 - IntelliJ IDEA你不知道的小技巧
 - ......

## 📈运维篇

### Docker
 - [为什么要使用Docker](https://www.cnblogs.com/charon2/p/10423241.html)
 - [Docker的介绍](https://www.cnblogs.com/charon2/p/10423304.html)
 - [Docker的安装](https://www.cnblogs.com/charon2/p/10423511.html)
 - [Docker的三要素](https://www.cnblogs.com/charon2/p/10423565.html)
 - [Docker-阿里云加速配置](https://www.cnblogs.com/charon2/p/10423584.html)
 - [Docker-运行时的底层原理](https://www.cnblogs.com/charon2/p/10423650.html)
 - [Docker-帮助命令](https://www.cnblogs.com/charon2/p/10423659.html)
 - [Docker-镜像命令](https://www.cnblogs.com/charon2/p/10423807.html)
 - [Docker-容器命令](https://www.cnblogs.com/charon2/p/10425060.html)
 - [Docker-镜像原理](https://www.cnblogs.com/charon2/p/10425150.html)
 - [Docker-commit操作](https://www.cnblogs.com/charon2/p/10425472.html)
 - [关于CentOS7下Docker-ce无法删除镜像的问题](https://www.cnblogs.com/charon2/p/10425758.html)
 - [Docker容器数据卷](https://www.cnblogs.com/charon2/p/10428413.html)
 - [dockerfile的保留字指令](https://www.cnblogs.com/charon2/p/10464945.html)
 - [dockerfile自定义mycentos](https://www.cnblogs.com/charon2/p/10465021.html)
 - ... ...

### Jenkins
 - [jenkins的爱与恨](https://www.yuque.com/charon-nsjtq/zbziy3)
 - ... ...

### shell
 - [shell的爱与恨](https://www.yuque.com/charon-nsjtq/zyf2d7)
 - ... ...

### Linux
 - [运维刘工的Linux小记录](https://www.yuque.com/charon-nsjtq/va3fps)
 - ... ...

## ✒️后记
 转载文章请在开头明显处标明该页面地址，公众号等其它转载请添加公众号中私人联系方式或发送邮件到 mrliu6293@foxmail.com
 
 如果觉得本仓库对您有帮助,想要表示感谢,欢迎进行打赏,**金额不重要**,您的支持是我前进最大的动力
 
 <div align=center>
  <img src='https://raw.githubusercontent.com/LiuHanChao-loger/loger/main/image/aliPay.png' width=200px height=250px />
  <img src='https://raw.githubusercontent.com/LiuHanChao-loger/loger/main/image/wechatPay.png' width=200px height=250px />
 </div>
 
### 致谢
 此页所有运维文章均为老同事刘浩然提供，在此衷心感谢，也欢迎有意向的小伙伴添加联系方式。
