进程里有很多线程，有内存（逻辑内存），指代内存的寻址空间，并不是真正分了4G，本质是给了寻址空间；文件/网络句柄，多个进程可以共用
线程里是调用栈，主线程调用会入栈，PC是下一个指令，存放在内存中。还有TLS，这里有独立内存空间。
进程是容器，线程是运行。
## 存储层次结构
硬盘、内存、缓存、寄存器，以此由慢到贵，由便宜到贵

## 寻址空间
进程指针取值范围，操作系统32位就是4G，目前大多数是64位的操作系统；64JVM没有指针的概念，可以使用更大的内容，迁移需要重新编译
指针——>逻辑内存——>物理内存——>虚拟内存分页（硬盘），保证数据进入物理内容。物理内存的数据取出来放到寄存器。
物理内存使用过多就会频繁分页


## 网络
在不可靠不安全的环境下如何传输数据
数据链路层（数据包，奇偶校验正确还是错误）
网络层（路由器，IP地址）
传输层（可靠传输， TCP/UDP）
应用层（HTTP）
七层协议、五层协议，很可能不是最优的网络方案。
在网络发展过程中，都在解决问题，所以在由一层一层叠加的，什么样的情况下提出的。是迭代进化的

## 网络传输
不可靠：丢包、重复、出错、乱序
不安全：中间人工具、窃取、篡改

## TCP解决可靠性问题的方案，滑动窗口
维持发送方和接收方的缓冲区，各自维护缓冲区来解决不可靠的问题。发一个确认一个，这样很浪费，慢慢改进。
滑动窗口的演示，正常情况，丢包情况
丢包情况，等ACK，这里有超时重传机制，一定要按顺利ACK


## 关系型数据库
基于关系代数理论
缺点：表结构不直观、实现复杂、速度慢
优点：健壮性高、社区庞大


## 事务
ACID
A原子性
C一致性
I隔离性
D持久性

## 事务的隔离级别
Read uncommitted
Read committed
Repeatable Read
Serializable

for update 加写锁，耗费资源
乐观锁：加一个版本保护，记录Timestamp，冲突机会不多的情况下使用

## 程序设计语言
类型检查分类
编译时：C、C++、Java、Go
运行时：Python、Perl、JavaScript
运行/编译：
直接编译为机器代码：C、C++
编译为中间代码：Java、C#
解释执行：Python、Perl
编范范式：
面向过程、面向对象、函数式

## 数据类型
boolean、byte、char
short、int、long、float、double
String、Enumerate、Array
Object

32为int的取值范围，主要是看符号位和数值位
补码：取反加1，为了便于和数学一致


## 浮点数

符号位|指数部分|基数部分

浮点数比较，有精度问题，差的绝对值看是否小于eps，具体分析
用BigDecimal算钱


## Java数据类型

值类型和对象类型
装箱和拆箱
显示装箱、隐式装箱
拆箱


## 数学归纳法

用于证明断言对所有自然数成立，这是个公理
证明N=1成立
如果N>1成立，则N成立

递归控制
严格定义递归含义的作用，包括参数、返回值、全局状态
先一般、后特殊，先写假设和推导，再写特殊情况
每次调用必须缩小问题的规模
每次问题规模缩小程序必须为1

递归的缺点
Stack
函数调用开销，Stack Overflow错误


循环控制
一般化的方法仍然需要栈，代码会变复杂（入栈出栈的代码），不能根本解决问题

循环不变式，是一句断言定义各变量所满足的条件


## 边界控制
主要还是看经验

二分查找有一个隐藏10年的bug

## 数据结构

树
容易理解、难度大、综合性强
二叉树的遍历（前序、中序、后续）
先遍历树根，
然后前序遍历左子树
再前序遍历右子树


## 设计模式

Singleton优缺点
确保全局至多只有一个对象
用于构造缓慢的对象，需要统一管理的资源
缺点，很多全局状态、线程安全性
双重锁模式/使用Java类的静态变量/使用框架提供的能力

继承关系，is a关系，不要用继承关系来实现复用，使用设计模式实现代码复用
状态模式
装饰器模式

创建对象：创建哪个类，参数不明确

抽象工厂模式
构建模式

## 多线程

死锁分析
synchronized关键字
在任何地方都可以线程切换，甚至在一句语句中心
要尽力设想对自己最不利的情况

死锁的四个条件：
互斥等待——一般无法破除
hold and wait——一次性获取所有资源
循环等待——按顺序获取资源
无法剥夺的等待——加入超时

线程池的演示

## 资源管理
不被引用的对象会被回收
垃圾回收包括Minor GC、Full GC
垃圾回收时所有运行暂停
Java和C++销毁对象


## 并行计算
如何排序10G个算法

扩展的归并排序，分左右两半排序后，将两个有序数据归并
用堆的数据结构，
堆——完全二叉树，根是最小的，PriorityQueue
最后还是10G的数据送进去
将一部分放进内存里

## 面向对象思想
类与对象
类的成员变量——对象状态
类的成员函数——对象行为
类的静态变量、静态函数——全局就一份
类的特殊函数
构造函数
Hashcode和equal 必要非充分的关系

接口
从用户角度看问题
是模块间协作的合约，无成员变量，没有实现
Java Interface关键字
C++ 一个全部是纯虚函数的类
python：依靠注释来生命

接口和抽象类：
从实现角度，抽象类可以有成员变量、部分实现
抽象类不可以多重继承，接口可以

为什么设计成这样：
从用户角度看问题、强调合约、、强制协作双方无法犯错
包装链表类，实现iteratable接口

继承（is-a）与封装
类内/包内/派生/外部
private
默认
protected
public
尽量只是用private、public

不可变对象
可以引用传递，可以缓存；线程安全
final关键字无法保证不可变性
通过final关键字声明，不能被继承、不能重写、不能指向其他对象
从接口定义，类的实现上保证不可变性
Collections.Unmodified
泛型
第一层是结构，第二层是类型，从List到List<T>
Java Type Erasure 
Covariance
基础知识：广度优先、在兴趣点深入