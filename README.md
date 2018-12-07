# CollLog
这是一个电信日志改造项目，涉及hdfs+hive+flume+kafka+storm+ssm等技术

#项目架构分析：

## 项目描述：

将通话记录数据由原来的oracle系统改造成使用大数据架构解决方案。主要使用hbase做通话数据的存储方案。需要将原有oracle数据导入到hbase中，以及新生成数据通过flume收集到kafka，再通过消费者存储到hbase数据库。

## 项目的目标：

hadoop+hbase+flume+zookeeper实现电信级海量通话日志数据的存储，随机访问与实时读写。通过hash技术对rowkey进行分析处理，解决hbase的热点问题，协同coprocessor，解决系统的高吞吐量和查询负载问题以及如何避免中间结果导致通知风暴或死递归问题

### 项目要点难点

#### 使用hadoop+hbase+flume+kafka + zookeeper实现海量通话日志的存储、随机访问与实时读写功能。 

#### 采用hbase实现bigtable技术，通过盐析rowkey结合表区域的预切割，实现数据在集群上的均衡负载。

#### SSM实现前端web实现以及与后端HBase的交互架构方案

#### hive+oozie实现的周期任务调度

### 业务介绍

按照文档要求，实现hbase协处理器处理，以及rowkey的盐析处理按照部分统计分析设计要求，实现业务代码，例如按季度、年份、月份实现通话数据量的查询分析统计数据可视化

### 功能实现

flume集群实时收集记录—>kafka集群作为数据仓库高速缓存—>hbase以hadoop为基础作为数据库提供用户实时读写功能—>前台ssm web端展示

flume集群实时收集记录—>kafka集群作为数据仓库高速缓存—>storm进行实时处理操作（如拦截数据等）—>前台ssm web端展示 
