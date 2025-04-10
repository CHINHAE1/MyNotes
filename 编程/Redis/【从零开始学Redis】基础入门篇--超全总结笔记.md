# 【从零开始学Redis】基础入门篇--超全总结笔记


链接：https://blog.csdn.net/2301_79819426/article/details/145501322

1. 初识Redis
Redis是一种键值型的NoSql数据库，这里有两个关键字：

键值型——键值对 key-value


NoSql

其中键值型，是指Redis中存储的数据都是以key、value对的形式存储，而value的形式多种多样，可以是字符串、数值、甚至json：


![img|775](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/c0a242773cc04e4bb2934b200d4929dd.png)

而**NoSql则是相对于传统关系型数据库而言，有很大差异的一种数据库**。



1.1 认识NoSQL
NoSql可以翻译做Not Only Sql（不仅仅是SQL），或者是No Sql（非Sql的）数据库。是相对于传统关系型数据库而言，有很大差异的一种特殊的数据库，因此也称之为非关系型数据库。

SQL：关系型数据库

Structured：结构化

1.1.1 结构化与非结构化
传统关系型数据库是结构化数据，每一张表都有严格的约束信息：字段名、字段数据类型、字段约束等等信息，插入的数据必须遵守这些约束：

结构化，一般不对表的结构进行修改![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/89842b8ccfd44b578aef37f95815c4c2.png)

而**NoSql则对数据库格式没有严格约束**，往往形式松散，自由。

- **非结构化**

可以是键值型：

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/b534ec6f422a4b38a133510fafe562a7.png)

也可以是文档型：以JSON的格式进行存储

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/e19d84efe19643249d193145ac5a1edb.png)

甚至可以是图格式：

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/14ddebe903cd42a1b1eacd5ad6507a08.png)

#### 1.1.2.关联和非关联

传统数据库的表与表之间往往存在关联，例如外键：

- order订单表将user和item关联起来，**表与表之间有关系**
- 关联的

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/ec70a5d7982749c78c94df06f1b46333.png)

而**非关系型数据库不存在关联关系**，要维护关系要么靠代码中的业务逻辑，要么靠数据之间的耦合（嵌套）：

无关联的

{
  id: 1,
  name: "张三",
  orders: [
    {
       id: 1,
       item: {
	 id: 10, title: "荣耀6", price: 4999
       }
    },
    {
       id: 2,
       item: {
	 id: 20, title: "小米11", price: 3999
       }
    }
  ]
}
此处要维护“张三”的订单与商品“荣耀”和“小米11”的关系，不得不冗余的将这两个商品保存在张三的订单文档中，不够优雅。还是建议用业务来维护关联关系。

1.1.3.查询方式
传统关系型数据库会基于Sql语句做查询，语法有统一标准；

而不同的非关系数据库查询语法差异极大，五花八门各种各样。![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/bc79f8f0f60c4c96baca402655165078.png)

#### 1.1.4.事务

**传统关系型数据库能满足事务ACID的原则。**

> ACID 原则
> A - 原子性 (Atomicity)
>
> 事务中的所有操作要么全部成功，要么全部失败。即使在事务的执行过程中出现问题，已执行的操作也会被回滚，不会有部分操作成功，部分操作失败的情况。
> 举例：银行转账操作，转出和转入必须一起成功，否则都不成功。
> C - 一致性 (Consistency)
>
> 事务执行前后，数据库的状态必须是一致的。也就是说，事务必须使数据库从一个一致的状态转变到另一个一致的状态。
> 举例：如果你有一个“账户”表和一个“余额”字段，执行转账操作前后，账户的余额必须符合预定规则，不能出现负数余额（除非允许透支）。
> I - 隔离性 (Isolation)
>
> 并发执行的事务之间是隔离的，一个事务的执行不应该受到其他事务的干扰。不同的隔离级别定义了事务如何相互隔离。
> 举例：如果两个用户同时向同一个账户转账，系统必须确保每个用户的操作不会互相干扰，最终结果是正确的。
> D - 持久性 (Durability)
>
> 一旦事务被提交，它对数据库的修改就是永久性的，即使发生系统崩溃，也能够恢复事务的结果。
> 举例：如果你成功提交了一个转账事务，即使在提交后发生了系统崩溃，数据库也应该能够在重启后恢复该事务的结果。



而非关系型数据库往往不支持事务，或者不能严格保证ACID的特性，只能实现基本的一致性。BASE

1.1.5.总结
除了上述四点以外，在存储方式、扩展性、查询性能上关系型与非关系型也都有着显著差异，总结如下：



存储方式

关系型数据库基于磁盘进行存储，会有大量的磁盘IO，对性能有一定影响

非关系型数据库，他们的操作更多的是依赖于内存来操作，内存的读写速度会非常快，性能自然会好一些

扩展性

关系型数据库集群模式一般是主从，主从数据一致，起到数据备份的作用，称为垂直扩展。

非关系型数据库可以将数据拆分，存储在不同机器上，可以保存海量数据，解决内存大小有限的问题。称为水平扩展。

关系型数据库因为表之间存在关联关系，如果做水平扩展会给数据查询带来很多麻烦

1.2.认识Redis
Redis诞生于2009年全称是Remote Dictionary Server 远程词典服务器，是一个基于内存的键值型NoSQL数据库。

特征：

键值（key-value）型，value支持多种不同数据结构，功能丰富

单线程，每个命令具备原子性——所有线程串行执行，线程是安全的，不会存在一个命令执行到一半，有其他命令插入进来的情况

低延迟，速度快（基于内存、IO多路复用（提高了吞吐量）、良好的编码）——内存和磁盘的读写速度差异太大了

支持数据持久化——定时将内存上的数据保存到磁盘中

支持主从集群（MySQL）、分片集群（水平扩展）

支持多语言客户端（任何语言都能用）

作者：Antirez

Redis的官方网站地址：Redis - The Real-time Data Platform

2.Redis常见数据结构及操作命令
Redis是典型的key-value数据库，key一般是字符串，而value包含很多不同的数据类型：

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/e7107bd508fc4698b1fc4f46f759916e.png)

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/644938f107b746819aefb6b84cf52857.png)

Redis为了方便我们学习，将操作不同数据类型的命令也做了分组，在官网（ [https://redis.io/commands ](https://redis.io/commands)）可以查看到不同的命令：

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/1c75581d65be430da7c05b493eef5368.png)

不同类型的命令称为一个group，我们也可以通过help命令来查看各种不同group的命令：

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/e65e2d93abc04727a14dc1b3629adc26.png)

### 2.1.Redis通用命令

通用指令是部分数据类型的，都可以使用的指令，常见的有：

KEYS：查看符合模板的所有key

DEL：删除一个指定的key

EXISTS：判断key是否存在

EXPIRE：给一个key设置有效期，有效期到期时该key会被自动删除

TTL：查看一个KEY的剩余有效期

通过help [command] 可以查看一个命令的具体用法

2.2.String类型
String类型，也就是字符串类型，是Redis中最简单的存储类型。

其value是字符串，不过根据字符串的格式不同，又可以分为3类：

string：普通字符串

int：整数类型，可以做自增、自减操作

float：浮点类型，可以做自增、自减操作

不管是哪种格式，底层都是字节数组形式存储，只不过是编码方式不同。字符串类型的最大空间不能超过512m.![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/47977d68fe2e4c9e8f59838f72a137c0.png)



#### 2.2.1.String的常见命令

String的常见命令有：

SET：添加或者修改已经存在的一个String类型的键值对

GET：根据key获取String类型的value

MSET：批量添加多个String类型的键值对

MGET：根据多个key获取多个String类型的value

INCR：让一个整型的key自增1

INCRBY:让一个整型的key自增并指定步长，例如：incrby num 2 让num值自增2

INCRBYFLOAT：让一个浮点类型的数字自增并指定步长

SETNX：添加一个String类型的键值对，前提是这个key不存在，否则不执行

SETEX：添加一个String类型的键值对，并且指定有效期



2.2.2.Key结构
Redis没有类似MySQL中的Table的概念，我们该如何区分不同类型的key呢？

例如，需要存储用户、商品信息到redis，有一个用户id是1，有一个商品id恰好也是1，此时如果使用id作为key，那就会冲突了，该怎么办？

我们可以通过给key添加前缀加以区分，不过这个前缀不是随便加的，有一定的规范：

Redis的key允许有多个单词形成层级结构，多个单词之间用':'隔开，格式如下：

    项目名:业务名:类型:id

这个格式并非固定，也可以根据自己的需求来删除或添加词条。这样以来，我们就可以把不同类型的数据区分开了。从而避免了key的冲突问题。

例如我们的项目名称叫 heima，有user和product两种不同类型的数据，我们可以这样定义key：

user相关的key：heima:user:1

product相关的key：heima:product:1

如果Value是一个Java对象，例如一个User对象，则可以将对象序列化为JSON字符串后存储：
KEY	VALUE
heima:user:1	{"id":1, "name": "Jack", "age": 21}
heima:product:1	{"id":1, "name": "小米11", "price": 4999}
并且，在Redis的桌面客户端中，还会以相同前缀作为层级结构，让数据看起来层次分明，关系清晰：![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/82941bf0b51744a2b1d45d551a4703fa.png)

### 

### 2.3.Hash类型

Hash类型，也叫散列，其value是一个无序字典，类似于Java中的HashMap结构。

**String结构是将对象序列化为JSON字符串后存储，当需要修改对象某个字段时很不方便：**

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/6aea8cc0b3c94df6bb1fa4957d04dab1.png)

Hash结构可以**将对象中的每个字段独立存储，可以针对单个字段做CRUD：**

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/be438dbc639c418a9374ad611ae29e36.png)

Hash的常见命令有：

HSET key field value：添加或者修改hash类型key的field的值

HGET key field：获取一个hash类型key的field的值

HMSET：批量添加多个hash类型key的field的值

HMGET：批量获取多个hash类型key的field的值

HGETALL：获取一个hash类型的key中的所有的field和value

HKEYS：获取一个hash类型的key中的所有的field

HINCRBY:让一个hash类型key的字段值自增并指定步长

HSETNX：添加一个hash类型的key的field值，前提是这个field不存在，否则不执行



2.4.List类型
Redis中的List类型与Java中的LinkedList类似，可以看做是一个双向链表结构。既可以支持正向检索和也可以支持反向检索。

特征也与LinkedList类似：

有序

元素可以重复

插入和删除快

查询速度一般

常用来存储一个有序数据，例如：朋友圈点赞列表，评论列表等。



List的常见命令有：

LPUSH key element ... ：向列表左侧插入一个或多个元素

LPOP key：移除并返回列表左侧的第一个元素，没有则返回nil

RPUSH key element ... ：向列表右侧插入一个或多个元素

RPOP key：移除并返回列表右侧的第一个元素

LRANGE key star end：返回一段角标范围内的所有元素

BLPOP和BRPOP：与LPOP和RPOP类似，只不过在没有元素时等待指定时间，而不是直接返回nil



2.5.Set类型

Redis的Set结构与Java中的HashSet类似，可以看做是一个value为null的HashMap。因为也是一个hash表，因此具备与HashSet类似的特征：

无序

元素不可重复

查找快

支持交集、并集、差集等功能

Set的常见命令有：

SADD key member ... ：向set中添加一个或多个元素

SREM key member ... : 移除set中的指定元素

SCARD key： 返回set中元素的个数

SISMEMBER key member：判断一个元素是否存在于set中

SMEMBERS：获取set中的所有元素

SINTER key1 key2 ... ：求key1与key2的交集

例如两个集合：s1和s2:

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/6dbd45ca6cd342a087c90d1634a210e5.png)

求交集：SINTER s1 s2

求s1与s2的不同：SDIFF s1 s2

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/1d5b37e253784972852aa2d3f51ab9f6.png)

2.6.SortedSet类型
Redis的SortedSet是一个可排序的set集合，与Java中的TreeSet有些类似，但底层数据结构却差别很大。SortedSet中的每一个元素都带有一个score属性，可以基于score属性对元素排序，底层的实现是一个跳表（SkipList）加 hash表。

SortedSet具备下列特性：

可排序

元素不重复

查询速度快

因为SortedSet的可排序特性，经常被用来实现排行榜这样的功能。

SortedSet的常见命令有：

ZADD key score member：添加一个或多个元素到sorted set ，如果已经存在则更新其score值

ZREM key member：删除sorted set中的一个指定元素

ZSCORE key member : 获取sorted set中的指定元素的score值

ZRANK key member：获取sorted set 中的指定元素的排名

ZCARD key：获取sorted set中的元素个数

ZCOUNT key min max：统计score值在给定范围内的所有元素的个数

ZINCRBY key increment member：让sorted set中的指定元素自增，步长为指定的increment值

ZRANGE key min max：按照score排序后，获取指定排名范围内的元素

ZRANGEBYSCORE key min max：按照score排序后，获取指定score范围内的元素

ZDIFF、ZINTER、ZUNION：求差集、交集、并集

注意：所有的排名默认都是升序，如果要降序则在命令的Z后面添加REV即可，例如：

升序获取sorted set 中的指定元素的排名：ZRANK key member

降序获取sorted set 中的指定元素的排名：ZREVRANK key memeber

3.Redis的Java客户端在Redis官网中提供了各种语言的客户端，地址：[https://redis.io/docs/latest/develop/clients/](https://redis.io/docs/clients/)

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/47163e3dfcc6446097db599997951a4d.png)

其中Java客户端也包含很多：

![img](https://picgo-q1uill.oss-cn-chengdu.aliyuncs.com/img-for-typora/ac3fc4b4c5ad45e3a825737f03104708.png)

Jedis和Lettuce：这两个主要是提供了Redis命令对应的API，方便我们操作Redis，而SpringDataRedis又对这两种做了抽象和封装，因此我们后期会直接以SpringDataRedis来学习。

Redisson：是在Redis基础上实现了分布式的可伸缩的java数据结构，例如Map、Queue等，而且支持跨进程的同步机制：Lock、Semaphore等待，比较适合用来实现特殊的功能需求。



### 3.1.Jedis客户端

Jedis的官网地址： https://github.com/redis/jedis

#### 3.1.1.快速入门

我们先来个快速入门：

1）引入依赖：

<!--jedis-->
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>3.7.0</version>
</dependency>
<!--单元测试-->
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <version>5.7.0</version>
    <scope>test</scope>
</dependency>
2）建立连接

新建一个单元测试类，内容如下：

BeforeEach

@BeforeEach 是 JUnit 5 测试框架中的一个注解，用于在每个测试方法执行之前运行一些初始化代码。

使用场景

初始化数据或状态。

重置某些对象的状态。

准备测试资源，比如数据库连接、文件等。

@BeforeEach 是一个非常有用的注解，可以让你专注于测试逻辑，而不用担心每次重复编写初始化代码，提高了测试代码的可维护性和清晰性。



private Jedis jedis;

@BeforeEach
void setUp() {
    // 1.建立连接
    // jedis = new Jedis("192.168.150.101", 6379);
使用连接池创建！！！！
    jedis = JedisConnectionFactory.getJedis();
    // 2.设置密码
    jedis.auth("123321");
    // 3.选择库
    jedis.select(0);
}



3）测试：

@Test
void testString() {
    // 存入数据
    String result = jedis.set("name", "虎哥");
    System.out.println("result = " + result);
    // 获取数据
    String name = jedis.get("name");
    System.out.println("name = " + name);
}

@Test
void testHash() {
    // 插入hash数据
    jedis.hset("user:1", "name", "Jack");
    jedis.hset("user:1", "age", "21");

    // 获取
    Map<String, String> map = jedis.hgetAll("user:1");
    System.out.println(map);
}
AfterEach和BeforeEach功能类似



4）释放资源

```java
@AfterEach



void tearDown() {



    if (jedis != null) {



        jedis.close();



    }



}
```



#### 3.1.2.连接池

Jedis本身是线程不安全的，并且频繁的创建和销毁连接会有性能损耗，因此我们推荐大家使用Jedis连接池代替Jedis的直连方式。

下面代码说明

定义了一个工具类—— JedisConnectionFactory

一个静态成员变量—— jedisPool

然后通过一个静态代码块（通常用于在类被加载时完成一些静态变量的初始化），对jedisPool初始化

提供一个静态方法，方便从连接池去获取Jedis对象——调用工具类的getJedis方法，从池子中去获取Jedis实例（对象），用完再还回去，避免频繁的创建和销毁

