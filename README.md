## HERO

模仿zookeeper官网,实现一个分布式锁，分布式队列

使用技术:
 后台
使用Spring Boot 构建整个项目 去除 XML 配置
* 前台
使用angular5控制路由与数据请求 数据展示业务处理


## web地址(本机)
|名称|IP|完成情况|
|:---------------:|:---------------:|:---------------:|
| API    			|localhost:8081 |\|
| 架构搭建    			|localhost:8081 |\|

## ip地址(本机)
|名称|IP|完成情况|
|:---------------:|:---------------:|:---------------:|
| master    			|192.168.66.133:2181 |\|
| slave1    			|192.168.66.134:2181 |\|
| slave2    			|192.168.66.135:2181 |\|



## zookeeper整体实现过程
zookeeper版本为3.4.9 
现有三台服务器 分别为192.168.66.133(主) 134 135
zoo.cfg 配置为:
tickTime=2000
initLimit=5
syncLimit=2
dataDir=/work/zookeeper-3.4.9/var/zookeeper
dataLogDir=/work/zookeeper-3.4.9/logs  
clientPort=2181

server.1=master:2888:3888 #(主机名, 心跳端口、数据端口)
server.2=slave1:2888:3888
server.3=slave2:2888:3888

添加文件myid 至 dataDir 内容分别为1，2，3

/etc/hosts 修改域名映射
192.168.66.133 master
192.168.66.134 slave1
192.168.66.135 slave2

*功能点一实现分布式消息队列:
客户端连接shell :zkCli.sh -server master:2181
主zookeeper启动shell:zkServer.sh start

由客户端(本机)不断的访问
java -jar /Users/zengjie/work/rpc/target/rpc-jar-with-dependencies.jar  qTest master 100 c 
不断的产生consumer 

由 master 不断的提供消息队列
java -jar /work/rpc-jar-with-dependencies.jar qTest localhost 1000 p
不断的生成Producer

*功能点二实现分布式锁:(待完成)

## 常见问题

1. 编译失败
	
	编译不成功的都是缺少jar包 麻烦配置Nexus 然后更新整个项目去下载jar包 
	在继续编译 如还失败 **请查看本地maven仓库jar是否真正下载下来**
	
2. 编译成功启动失败

3.   


