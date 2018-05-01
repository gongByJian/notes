##### 快捷键
    设置 ctrl+ alt+S 
    列出方法 CTRL+F12   
    自动提示代码实现接口方法 CTRL+1 = ALT+ENTER 
    在当前行上创建一行 CTRL+ENTER
    在当前行下创建一行 SHIFT+ENTER
    删除行 CTRL+X
    重命名 SHIFT+F6
    上下移动代码 CTRL + SHIFT + 上下键
    打开光标处的类或方法CTRL + B, CTRL + ALT + B 进入接口或者抽象类的实现类
    F3查找
    
##### 设置编码
    找到intellij idea安装目录，bin文件夹下面idea64.exe.vmoptions和idea.exe.vmoptions这两个文件，
    分别在这两个文件中添加：-Dfile.encoding=UTF-8
    
    第二步：找到intellij idea的file---settings---Editor---FileEncodings
    GlobalEncoding和ProjectEncoding和Default encoding for properties都配置成UTF-8
    
    第三步：在部署Tomcat的VM options项中添加：-Dfile.encoding=UTF-8
    
    第四步：重启Intellij idea即可解决乱码问题
    
    main函数控制台乱码
    同样是打开setting，找到 Build,Execution,Deployment > Compiler > Java Compiler， 
    设置 Additional command line parameters选项为 -encoding utf-8，然后rebuild下，重新运行
    
    控制台右下角有个设置编码
    
    最后一步：检查下是否原来输出的就是乱码,先输入中文后设置编码会将原中文变为乱码！

##### 更改代码快捷键
    设置-->editor-->code templates-->设置快捷键
    譬如main方法的快捷键在other, System.out.println();的快捷键在output

##### 设置自动代码提示
    设置-->keymap-->搜basic设置成ALT+/



##### Idea 与 Eclipse 快捷键的区别，上为Eclipse的快捷键，下为Idea的快捷键
	查找类名
	CTRL + SHIFT + R
	CTRL + N

	查找JAR包中的类
	CTRL + SHIFT + T
	两次 CTRL + N
	
	查找文件
	CTRL + SHEFT + R
	CTRL + SHEFT + N
	
	查找JAR包中的文件
	CTRL + SHIFT + T
	两次 CTRL + SHEFT + N
	
	查找类中的方法以及字段
	无
	CTRL + SHEFT + ALT + N
	
	查找那些类调用该资源（资源可能是字段、方法、类）
	CTRL + SHIFT + G
	ALT + F7 ，快速显示查找内容 CTRL + ALT + F7
	
	查找文件中的变量
	点击变量 CTRL + K ：移动
	点击变量 CTRL + SHEFT + F7 高亮显示 F3 ： 移动； SHEFT + F3 ： 反向移动
	
	定位行数
	CTRL + L
	CTRL + G
	
	快速生成get set、构造函数等
	ALT + SHIFT + S
	ALT + INSERT
	
	快速生成try cache
	SHIFT + ALT + Z
	CTRL + ALT + T 同时还能生成if else 等等其他的东西
	
	快速优化引用包
	CTRL + SHIFT + O
	CTRL + ALT + O
	
	快速格式化代码
	CTRL + SHIFT + F
	CTRL + ALT + L
	
	重构代码
	CTRL + F2
	SHIFT + F6
	
	显示类中的变量、方法
	CTRL + O
	CTRL + F12
	
	快速生产类、方法、字段注释 
	CTRL + SHEFT + J
	/** + ENTER
	
	代码行 上下移动
	ALT + 上下键
	CTRL + SHIFT + 上下键
	
	打开光标处的类或方法
	F3
	CTRL + B, CTRL + ALT + B 进入接口或者抽象类的实现类
	
#### 其他的快捷键： ####
	F4 查找变量来源
	CTRL + 空格 代码提示 (和系统输入法冲突，请在Settings->Keymap->mainmenu -> code ->Completion->basic，右键添加自己的快捷键)
	ALT + 回车  导入包,自动修正
	CTRL + H 查看类的继承关系。 
	CTRL + Q 显示注释文档（跟eclipse鼠标放到类、方法、字段显示的内容一样）
	CTRL + W 选中代码，连续按会有其他效果
	CTRL + U 查看当前类的父类以及接口，
	CTRL + ALT + U 查看类UML图
	CTRL + SHIFT + U 切换大小写
	CTRL + P 方法参数提示，可以看到这个方法有哪些多态方法
	SHIFT + ALT + INSERT 竖编辑模式


#### 智能提示忽略大小写 ####
	Editor --> Code Completion页里有个Case sensitive completion，可以设置只第一个字母敏感、完全敏感或者不敏感。

#### 设置JDK编译版本 ####
	Compiler --> Java Compiler页里有个Project bytecode version(leave blank for jdk default)设置JDK的版本，要不然编译的时候会出现各种问题。

#### 显示行号 ####
	Editor --> Appearence 页面中 Show Line Number 勾上。

#### 取消拼音检查 ####
	Spelling 页面中 Configure 'Spelling' inspection 点击然后取消 Spelling 选项。
	取消不使用对象的检查（搜索never used 关键字将其中的unused的检查去掉）

#### 取消自动保存文件功能 ####
	General 页面中
	勾掉 Synchronize file on frame activation 选项（同步文件功能，酌情考虑可以不取消）
	勾掉 Save files on framedeactivation 选项
	勾掉 Save files automatically 选项，并将自动保存时间间隔，设置为30秒

#### 编辑过的文件显示“*”标记 ####
	Editor –-> Editor Tabs 页面中勾上 Mark modifyied tabs with asterisk 选项，修改后的文件会跟elicpse一样显示“*”标记。

#### 让IntelliJ IDEA 启动的时候不打开工程文件  ####
	Settings --> General 页面中，勾掉 Reopen last project on startup 选项。

#### SVN添加项目报错（CreateProccess error=2 后面还有乱码） ####
	Version Control --> Subversion 页面中勾掉“Use commmand line client:”选项后，就可以了，然后会提示你选择svn 1.6、svn 1.7、svn 1.8等版本。（好像只有Idea 13 才有这个问题）