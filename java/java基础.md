    OOP:Object Oriented Programming

##### java常识
	Java语言前身叫Oak
	Java之父：James Gosling
	95年，Sun发布JDK1.0
	98年，JDK1.2,更名为Java2
	后续JDK1.3、1.4
	JDK1.5、更名为Java5.0

	J2SE - Java 2 Standard Edition
	(标准版) :用于创建典型的桌面与工作站应用的Java平台。 (ftp、聊天室之类)
	J2EE - Java 2 Enterprise Edition
	(企业版):用于创建可扩缩的企业应用的Java平台。(大型应用网站、EJB)
	J2ME - Java 2 Micro Edition
	(缩微版):用于创建嵌入式应用程序的Java平台(如PDA、仪表)

##### java特点
	开源
	免费
	简单
	安全
	强壮
	多线程
	跨平台

> Java具有“垃圾收集”机制，Java的运行环境周期地检测某个实体是否已不再被任何对象所引用，如果发现这样的实体，就释放实体占有的内存。因此，Java编程人员不必象C++程序员那样，要时刻自己检查哪些对象应该释放内存。当把变量t2中存放的引用赋给t1后，最初分配给对象t1的成员变量（实体）所占有的内存就会被释放。

##### java常用包
	java.io
	java.lang
	java.math
	java.sql
	java.text
	java.util

##### Java为我们提供了大约130多个包，如：
>   1. java.applet         包含所有的实现Java applet的类
>   2. java.awt            包含抽象窗口工具集中的图形、文本、窗口GUI类
>   3. java.awt.image      包含抽象窗口工具集中的图像处理类
>   4. java.lang           包含所有的基本语言类
>   5. java.io             包含所有的输入输出类
>   6. java.net            包含所有实现网络功能的类
>   7. java.until          包含有用的数据类型类

##### Java数据类型
	简单数据类型
		数值型
			整数类型
				byte    1字节
				short   2字节
				int     4字节
				long	8字节
			浮点类型
				float	4字节
				double	8字节
		字符型
		布尔型
	引用数据类型
		类（对象）
		接口
		数组

##### 数值型
	byte	1字节 	-128 ~ 127
	short	2字节 	-2 15 ~ 2 15-1 （-32768~32767）
	int 	4字节 	-2 31 ~ 2 31-1 (-2147483648~2147483647)
	long	8字节 	-2 63 ~ 2 63-1
	float	4字节 	-3.403E38~3.403E38
	double	8字节 	-1.798E308~1.798E308
	
##### 基本数据类型转换等级:
    byte,short ---> int ---> long
    float ---> double
    int ---> float
    long ---> double
    (小转大自动转换，大转小强制转换)

##### 两个核心命令
	javac A.java ->class 
	javac A.java -d .  按包自动生成目录
	java A

##### javadoc 文档生成
	javadoc Test.java -d dir//为Test.java生成文档，存在于dir目录内
	javadoc Test.java -d ./doc -author -version

	@author：作者
	@version：版本
	@docroot：表示产生文档的根路径
	@deprecated：不推荐使用的方法
	@param：方法的参数类型
	@return：方法的返回类型
	@see："参见"，用于指定参考的内容
	@exception：抛出的异常
	@throws：抛出的异常，和exception同义

##### 转义字符
	转义符	含义			Unicode值
	\b		退格（backspace）	\u0008
	\n		换行				\u000a
	\r		回车				\u000d
	\t		制表符（tab）		\u0009
	\“		双引号				\u0022
	\‘		单引号				\u0027
	\\		反斜杠				\u005c

##### 运算符优先级
	运算符说明		Java运算符
	分割符			. [] () , ;
	单目运算符		+ - ~ ! ++expr --expr
	创建或类型转换	New (type)expr
	乘法／除法		* / %
	加法／减法		+ -
	移位			<< >> >>>
	关系			< <= >= > instanceof
	等价			== !=
	按位与			&
	按位异或		^
	按位或			|
	条件与			&&
	条件或			||
	条件			?:
	赋值			=

##### 时间
	jdk optional Java VM Arguments加入
		-Duser.timezone=GMT+08

##### Java关健字
	synchronized  同步
	transient 序列化时，不被存储
	volatile 多线程共享又不要互斥
	native java调用非java代码的接口

##### jar打war包
	jar -cvf aa.war .    //.代表找包当前目录 aa.war代表打包的文件

##### jar运行
	java -jar f:\a.jar

##### URL转码
	URLEncoder.encode("中国")
	URLDecoder.decode("%D6%D0%B9%FA") 

##### 内部类调用
	com.Test.Af af = new Test().new Af();

##### arraylist和linkedlist
    arrayList
    有序 查询快 底层是个数组 默认大小10-->15-->22-->33  满了的时候  以一半的速度增加 增加速度跟jdk版本有关 不同版本增加速度不一样
    linkedList 
    增删改快 底层是个双向链表
    Map 
    底层是个数组 默认大小16个 new HashMap() 括号里传两个值

##### JNDI
    Java Naming and Directory Interface,Java命名和目录接口
    JNDI提供统一的客户端API，通过不同的访问提供者接口JNDI服务供应接口(SPI)的实现，由管理者将JNDI API映射为特定的命名服务和目录系统，使得Java应用程序可以和这些命名服务和目录服务之间进行交互。