
一个Java 攻城狮的笔记本
----



本库：
主要涉及java，数据结构，算法，前端，数据库的相关知识。
补充面试的相关知识。




### 书单




+ Java:
    + 深入理解Java虚拟机 第二版，周志明
    + 码出高效-Java开发手册， 阿里 孤尽，鸣莎
    + Java 并发编程实战
    + 自己动手写Java虚拟机，张秀宏

    + Spring 技术内幕：深入解析 Spring架构与设计原理 (第 2版)》

+ 数据库
    + Mysql技术内幕:Innodb 存储引擎第二版，姜承尧
    + Redis 设计与实现
+ 操作系统:
    + Linux 私房菜

+ 网络：
    + 计算机网络 ，第六版，谢希仁

+ 算法：
    + 编程珠玑
    + 剑指offer
+ 架构：
    + 大型网站技术架构：核心原理与案例分析

+ 字典书：
    + Spring 实战
    + 深入浅出Mysql
+ 高级内功心法：
    + 阿里巴巴Java开发手册
    + 重构
    + 人月神话
+ tool 
    + Git权威指南

### log:


#### 2019-03-06

+ 归纳整理Java 多线程的相关知识




参考：[【技术类】2019校招技术类岗位面经汇总](https://www.nowcoder.com/discuss/146655)











### java 的基本数据类的底层存储



|基本类型|底层长度bit|默认值|数据范围|
|:-:|:-:|:-:|:-:|
|byte   |8    |0    |$-2^{7} \to 2^{7}-1$|
|short  |16   |0    |$-2^{15} \to 2^{15}-1 $ |
|int    |32   |0    |$-2^{31} \to 2^31-1 $|
|long   |64   |0L   |$-2^{61} \to 2^{61} -1$
|char   |16   |\u0000|\u0000 ~ \uffff|
|float  |32   |0.0f |
|double |64   |0.0  |
|boolean|8    |false|true or false



#### 以 8 字节对齐


+ 一个空对象占用8字节（空对象：占8字节 64位bit）
+ 一个对象只含有一个boolean 占16字节
+ 以8字节为单位对齐




#### JVM内存对齐:

比如 ：boolean会占用一比特或者占用一个字节的第八位，但是HotSpot虚拟机会为每个Boolean字段分配`一个字节`(byte)的空间


在 Java 虚拟机中没有任何供 boolean 值专用的字节码指令，在 Java 语言之中涉及到 boolean 类型值的运算，在编译之后都使用 Java 虚拟机中的 `int` 数据类型来代替`boolean`。


Java 虚拟机直接支持 `boolean 类型的数组`，虚拟机的 newarray 指令可以创建这种数组。boolean 的数组类型的访问与修改`共用 byte 类型数组的 baload 和 bastore 指令`。

综上所述, `单个boolean型`是占`4字节`(因为变异后会用int来代替), 而`boolean数组`中的则占`1字节`(因为用byte来代替的)


 
#### 32和64位差距
32位64位操作系统基本数据类型字节大小,只要注意long：
+ 32位： long: 4个字节 
+ 64位： long: 8个字节


那64位和32位操作系统在读取上有什么区别呢：

+ 64bit CPU拥有`更大的寻址能力`，理论上最大支持到16TB内存，而32bit只支持4G内存
+ 64位 CPU`一次可提取64位数据`，32位的CPU一次只能提取32位数据， 所以64位比32位提高了一倍，理论上性能会提升1倍。但这是建立在64bit操作系统，64bit软件的基础上的






原文：https://blog.csdn.net/u010235716/article/details/79074598 







Linux,Java 线程进程消失


可能的原因：

+ OutOfMemoryError 




-XX:+HeapDumpOnOutOfMemoryError  内存溢出的时候dump内存，定期jmap记录一下内存情况也是有必要的


增加JVM参数 -XX:+HeapDumpOnOutOfMemoryError 让他在内存溢出的时候dump内存，定期jmap记录一下内存情况也是有必要的

增加 ulimit -c unlimited 如果是jdk崩溃的话，也会有core文件在


至于程序方面，关键地方还是要搞搞日志，即使是nohup也最好把输出流和错误流重定向到其他文件。更好的做法使用log4j之内的日志框架而不是System.out



-Xms\<n>: 内存池的初始化值（）

-Xmx\<n>： 内存池的最大值（maximum）


-Xssn：Set thread stack size.







TCP保证数据的有效性


MySQL 建表






