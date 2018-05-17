#### java环境变量配置 

##### windows下配置JDK环境变量：

```
1.安装JDK。安装过程中可以自定义安装目录等信息，例如我们选择安装目录为D:/java/jdk1.6.0_30；
2.安装完成后，右击“我的电脑”，点击“属性”，选择“高级”选项卡，点击“环境变量”； 
3.在“系统变量”中，设置3项属性，JAVA_HOME, PATH, CLASSPATH(大小写无所谓),若已存在则点击“编辑”，不存在则点击“新建”； 
4.JAVA_HOME指明JDK安装路径，就是刚才安装时所选择的路径 D:/java/jdk1.6.0_30
此路径下包括lib，bin，jre等文件夹（此变量最好设置，因为以后运行tomcat，eclipse等都需要依此变量）；
Path使得系统可以在任何路径下识别java命令，设为： 
%JAVA_HOME%/bin; %JAVA_HOME%/jre/bin; 
CLASSPATH为java加载类(class or lib)路径，只有类在classpath中，java命令才能识别，设为： 
.; %JAVA_HOME%/lib/dt.jar; %JAVA_HOME%/lib/tools.jar;
 (注意：第一个分号前是一个英文的“点”号，表示当前路径) 
以上 %JAVA_HOME% 就是引用前面指定的JAVA_HOME； 
5.“开始”－>;“运行”，键入“cmd”； 
6.键入命令“java -version”，“java”，“javac”几个命令，出现画面，说明环境变量配置成功； 
7.好了，打完收工。下面开始你的第一个java程序吧。
```




//////////////////////////////////////////////////////////////////////////////
以下可以不看
//////////////////////////////////////////////////////////////////////////////

##### 下面讲讲java几个环境变量的含义和linux下的配置方法：

```
通常，我们需要设置三个环境变量：JAVA_HOME、PATH 和 CLASSPATH。
JAVA_HOME：该环境变量的值就是 Java 所在的目录，一些 Java 版的软件和一些 Java 的工具需要用到该变量，设置 PATH 和 CLASSPATH 的时候，也可以使用该变量以方便设置。
PATH：指定一个路径列表，用于搜索可执行文件的。执行一个可执行文件时，如果该文件不能在当前路径下找到，则依次寻找 PATH 中的每一个路径，直至找到。或者找完 PATH 中的路径也不能找到，则报错。Java 的编译命令 (javac)，执行命令 (java) 和一些工具命令 (javadoc, jdb 等) 都在其安装路径下的 bin 目录中。因此我们应该将该路径添加到 PATH 变量中。
CLASSPATH：也指定一个路径列表，是用于搜索 Java 编译或者运行时需要用到的类。在 CLASSPATH 列表中除了可以包含路径外，还可以包含 .jar 文件。Java 查找类时会把这个 .jar 文件当作一个目录来进行查找。通常，我们需要把 JDK 安装路径下的 jre/lib/rt.jar (Linux: jre/lib/rt.jar) 包含在 CLASSPATH 中。
PATH 和 CLASSPATH 都指定路径列表，列表中的各项 (即各个路径) 之间使用分隔符分隔。在 Windows 下，分隔符是分号 (;)，而在 Linux 下，分隔符是冒号 (:)。
下面分别说明三个环境变量在 Windows 和 Linux 下如何设置，不过在此之前，我们需要做个假设。假设 JDK 在 Windows 下的安装路径是 C:/jdk/，在 Linux 下的安装路径是 /usr/local/jdk/。那么，安装后的 JDK 至少会包括如下内容：
C:/jdk (/usr/local/jdk)
|-- bin
|-- demo
|-- include
|-- jre
| |-- bin
| `-- lib
`-- lib
```



##### ***** 在 Windows 下设置

```
Windows 下使用 set 命令设置环境变量，为了使每一次启动计算机都设置这些环境变量，应该在系统盘根目录下的 autoexec.bat 文件中进行设置，如：
set JAVA_HOME=C:/jdk
set PATH=%JAVA_HOME%/bin;C:/Windows;C:/Windows/Command
set CLASSPATH=%JAVA_HOME%/jre/lib/rt.jar;.
有些版本的 Windows 不能用 %变量名% 来替换环境变量的内容，那么就只好直接写 C:/jdk 而不是 %JAVA_HOME% 了。另外，C:/Windows 和 C:/Windows/Command 是 Windows 会自动加入路径的，所以可以从设置中去掉。如果在 autoexec.bat 中已经设置了 PATH，那只需要将 %JAVA_HOME%/bin 加到原来设置 PATH 的那条语句中就行了。
CLASSPATH 也可以根据需要设置或者加入其它的路径，比如你想把自己写的一些类放在 C:/java 中，就可以把 C:/java 也添加到 CLASSPATH 中去，set CLASSPATH=%JAVA_HOME%/jre/lib/rt.jar;C:/java;.。
注意，在 CLASSPATH 中包含了一个“当前目录 (.)”。包含了该目录后，就可以到任意目录下去执行需要用到该目录下某个类的 Java 程序，即使该路径并未包含在 CLASSPATH 中也可以。原因很简单：虽然没有明确的把该路径包含在 CLASSPATH 中，但 CLASSPATH 中的 “.” 在此时就代表了该路径，如：
假设在 C:/java 目录下有可运行的类 HelloJava.class，那么
C:/> set CLASSPATH=C:/jdk/jre/lib/rt.jar;. // 设置 CLASSPATH 环境变量，注意最后有一个 “.”
C:/> cd java // 转到 C:/java 目录
C:/java> java HelloJava // 运行 HelloJava
Hello, Java. // 运行结果
C:/java> _
```



##### **** 在 Linux 下设置

```
Linux 下使用“变量名=变量值”设置变量，并使用 export 命令将其导出为环境变量。为了使每一次登录都自动设置好这些变量，你需要在 ~/.bash_profile 里或者 ~./bashrc 里进行设置，如
export JAVA_HOME=/usr/local/jdk
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=$JAVA_HOME/jre/lib/rt.jar:.
设置 PATH 时用的 $是指替换变量的值到JAVA_HOME 是指替换变量 JAVA_HOME 的值到 $JAVA_HOME 所在位置。如上句实际就是 export PATH=/usr/local/jdk/bin:$。这句中PATH。这句中 $PATH 也是同样的作用，不过这里的 PATH 是指以前设置的 PATH 变量的值，而非本次设置 PATH 变量的值。
注意，在 CLASSPATH 中包含了一个“当前目录 (.)”。包含了该目录后，就可以到任意目录下去执行需要用到该目录下某个类的 Java 程序，即使该路径并未包含在 CLASSPATH 中也可以。原因很简单：虽然没有明确的把该路径包含在 CLASSPATH 中，但 CLASSPATH 中的 “.” 在此时就代表了该路径，例如
假设在 /home/fancy/java 目录下有可运行的类 HelloJava.class，那么
[fancy@matrix fancy]$ export CLASSPATH=/usr/local/jdk/jre/lib/rt.jar:. // 设置 CLASSPATH，注意最后的“.”
[fancy@matrix fancy]$ cd ~/java // 转到 /home/fancy/java
[fancy@matrix java]$ pwd // 显示当前目录
/home/fancy/java // 当前目录是 /home/fancy/java
[fancy@matrix java]$ java HelloJava // 运行 HelloJava
Hello, Java // 运行结果
[fancy@matrix java]$ _
析
```



##### ***** 实例分析

```
只是操作系统不同，略有差别。
两个例子都提到一个“可运行的类”，它是指包含了 public static void main(String[] args) 方法的类，这将在下一章 HelloJava 一节中详述。例中的 CLASSPATH 均未包含 HelloJava.class 所在的目录(C:/java, /home/fancy/java)，但是均包含了当前目录 (.)。因此转到包含 HelloJava.class 的目录下去执行 java HelloJava，在 Java 寻找到 CLASSPATH 中的“. (当前目录，C:/java, /home/fancy/java)”时，找到了 HelloJava.class，运行成功。
```

