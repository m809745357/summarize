# redis 五种常见使用场景下 PHP 实战

## 前言

redis 等 nosql 简单高效的解决了高并发场景下的一系列问题，并很大程度的解放了持久化 DB 的业务压力。

## 实战

- [基于 redis 字符串 string 类型的简单缓存实战](https://github.com/TIGERB/easy-tips/blob/master/redis/cache.php)
- [基于 redis 列表 list 类型的简单队列实战](https://github.com/TIGERB/easy-tips/blob/master/redis/queue.php)
- [基于 redis 字符串 setnx 的悲观锁实战](https://github.com/TIGERB/easy-tips/blob/master/redis/pessmistic-lock.php)
- [基于 redis 事务的乐观锁实战](https://github.com/TIGERB/easy-tips/blob/master/redis/optimistic-lock.php)
- [基于 redis 的发布订阅实战](https://github.com/TIGERB/easy-tips/blob/master/redis/subscribe-publish)

## 测试用例

5 种使用场景都提供测试用例，使用方法：

- 克隆项目： git clone git@github.com:TIGERB/easy-tips.git
- 运行脚本： php redis/test.php [实例名称]， 例如测试悲观锁： 运行 php redis/test.php p-lock

```
运行结果：

执行 count 加 1 操作～ 

count 值为： 1

```

```
运行 php redis/test.php 获取参数列表

参数列表：

参数有误，正确示例： php redis/test.php p-lock 
====================================== 
参数列表： 
Array
(
    [缓存] => cache
    [队列] => queue
    [悲观锁] => p-lock
    [乐观锁] => o-lock
    [消息订阅 /推送] => Array
        (
            [订阅] => sub
            [推送] => pub
        )

)


```

## 源码

> 源码地址 [https://github.com/TIGERB/easy-tips](https://github.com/TIGERB/easy-tips)

这是我的一个关于《一个 php 技术栈后端猿的知识储备大纲》的知识总结，目前只完成了“设计模式”。