### 1、ActivityResult问题

[告别onActivityResult](https://www.jianshu.com/p/62e4fd3f4f41)

### 2、java泛型擦除和签名

### 3、停止线程的方法

### 4、线程安全

* 内存模型

* 禁用共享资源 （共享不可变资源）

  #### 共享可变资源

* 保证可见性 final volatile 锁

* 保证原子性（CAS指令） Unsafe.compareAnd

* 禁止重排序

### 5、ConcurrentHashMap

jdk5:分段锁，必要时枷锁

jdk6:优化二次Hash算法

jdk7:段懒加载， volatile & cas

jsk8:摒弃段，基于HashMap

### 6、AtomicReference 和 AtomicReferenceFieldUpdater区别

### 7、如何在Android中写出优雅的异步代码

什么是异步

是否熟悉回调地狱

是否能够熟练使用RxJava

是否对Kotlin协程有了解

编写代码意识和能力

Rxjava

### 8、CPU架构适配需要注意哪些问题

-fvisibility=hidden

-fno-exceptions -fno-rtti

Android Log 替换 iostream 

gc-sections 去除无用代码

构架分包

### 9、Java Native 方法与Native怎么绑定的？

静态绑定

extern "C" JNIEXPORT void JNICALL

动态绑定

### 10、JNI如何实现数据传递

Bitmap nativeCompress

字符串操作

GetString UTFChars/ReleaseStringUTFChars

GetStringChars/ReleaseStringChars

GetStringUTFRegion/GetStringRegion

GetStringCritical/ReleaseStringCritical

DirectBuffer字节序问题

对象数组较大时 localRef

### 11、全局捕获Native异常

Linux信号（清理Native和java层资源）sigaction

Native任意位置获取jclass

地层线程与Java虚拟机关系

项目经验

### 12、只有C、C++可以编写Native库 么

理论上都可以

kotlin Native

### 13、Activity启动流程

与AMS交互过程

BInder通信机制

插件化框架HookActivity

参数传递

Activity转场动画实现机制

Activity窗口启动流程

Instrumentation

### 14、跨App启动Activity

防止自己的Activity被外部非正当启动

拒绝服务漏洞

开发时规避拒绝服务漏洞

### 15、如何解决Activity参数的类型安全及接口繁琐的问题

注解处理器

### 16、如何在代码的任意位置为Activity添加一个View

如何在任意位置获取当前Activity

是否对Activity的窗口有深入认识

潜在的内存泄漏的风险以及内存回收机制

深入评估技术合理性



内存回收机制

### 17、如何实现类似微信右滑返回的效果

熟练掌握手势和动画的运用

了解窗口绘制的内部原理

对Activity的窗口有深入认识

### 18、为什么非Ui线程不能更新UI

### 19、Handler发送消息的delay靠谱么

是否清楚UI时间相关的任务如动画的设计实现原理

是否对Looper的消息机制有深刻的理解

是否做过UI过度绘制或其他消息机制的优化

### 20、主线程为什么不会导致ANR

ANR产生原因

Looper空闲的时候阻塞原理

 ### 21、实现一个Handler Looper 框架

DelayQueue 内部原理

### 22、如何避免OOM的产生

java内存管理机制 堆内存限制

HashMap ArayMap

Enum int

Bitmap 选择合适分辨率，重采样和重用配置

不用帧动画

谨慎使用多进程

谨慎使用Large Heap

使用NDK



缩减

复用

回收

重构

重审



资料：Android 性能优化典范



### 23、如何对图片进行缓存

网络/磁盘/内存缓存

缓存算法分析 考虑：成本和价值（命中率）

LRU、LFU

LRUCache

熟悉的框架缓存机制分析

验证算法效果的意识

### 24、如何计算图片占用内存的大小

getByteCount()

getAllocationByteCount()

ARGB  RGB565

图片 / hdpi * 屏幕密度

inSampleSize 采样: 大图 -》小图

使用矩阵变化来放大图片 小图-》大图

使用RGB_565来加载不透明图片

使用9-patch图片做背景

不使用图片（动画）

使用VectorDrawable

索引模式(Indexed Color)

### 25、如何规避Android P对私有API的限制







### 25、如何开展优化工作

1、对目标有清晰认识

2、对重点问题拆解

3、是否有追求极致的技术功底和主观意愿

#### 如何开展？

1、定位关键问题

2、优先解决80%问题

3、业界横向对比

4、完善指标监控

5、项目收益

6、人力优化  



设计类题题目：

1、提出需求 ☆

2、可行性研究

3、需求分析☆

4、系统设计☆

5、系统开发

6、迭代维护

7、系统重审

### 1、设计网络请求框架

关键流程 

1、明确边界

2、优化细节 

3、打通流程

细节：

并发、线程调度、异步程序如何设计

网络接入 （链接池化）

数据安全性 是否需要加密 加密算法选择

​	对称加密

​	非对称加密

应用安全性



网络请求框架:

协议：http https websocket

1、连接管理

2、线程管理

3、缓存机制（淘汰策略）

4、重试机制

5、增加全局数据拦截

6、日志工具

7、注解配置请求

8、三方扩展

9、设计模式 （Builder） 拦截（责任链模式） 数据序列化（适配器模式）

注解、泛型、反射

10、DNS 增强



#### 热修复选型

方案选型：

是否要求立即生效？

是否要求新增修改类？

#### 插件化考虑体量

通常前期不需要，可以未雨绸缪

是否融合了多条业务线，多团队协作？

#### 性能问题

#### 监控

### 设计一个短视频App

重点：视频处理

视频服务?

视频来源？

是否建立用户关系链？

是否需要支持视频分享？

是否需要支付系统方便打赏？



网络框架：

播放器：

播放器可移植？



相机:

滤镜算法：

滤镜脚本化

安全性：