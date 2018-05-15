###### 新建工作空间
    1. 首先设置导入项目编码
    2. 设置jdk
    3. 设置tomcat use installation 配置超时时间 
    4. 设置maven  更新本地仓库配置


###### eclipse设置右键菜单显示
    window -> Customize Perspective -> Shortcuts

###### eclipse配置tomcat后需配置 
    server locations -> use tomcat installation  配置启动超时时间

###### 编辑javadoc文档注释
    Windows -> Preference -> Java -> Code Style -> Code Templates -> Code->New Java file -> Edit 

###### 导入注释模板
    Windows -> Preference-> Java-> Code Style -> Code Templates -> import

###### 设置JDK
    window -> preference -> java -> install jres -> add -> standard vm -> 设置好相应的jre home

###### eclipse修改jsp编码为utf-8
    window -> preference -> Web -> JSP Files 

###### myeclipse修改jsp编码为utf-8
    window -> preference -> MyEclipse -> Files and Editors -> JSP

###### 修改字体
    window -> preference -> General -> Colors and Fonts -> Basic -> Text Font


###### dos下中文转成unicode命令
    native2ascii
    
    unicode转成中文直接System.out.print("unicode码")

#### 快捷键
    自动格式整齐快捷键  CTRL+SHIFT+F
    
    生成文档注释 ALT+SHIFT+J
    
    生成无参构造器 ALT+/
    
    生成SET跟GET方法   ALT+SHIFT+S 
    
    注释CTRL+/	块注释CTRL+SHIFT+/ --->撤销CTRL+SHIFT+\
    
    导包 CTRL+SHIFT+字母O
    
    查找 CTRL+F
    
    重命名 ALT+SHIFT+R
    
    查找包 CTRL+SHIFT+T
    
    快捷键组合可在Eclipse按下ctrl+shift+L查看。
    
    自动try-catch Alt+Shift+Z+回车
    
    alt+shift+l以及alt+shift+m：提取本地变量及方法
        源码处理还包括从大块的代码中提取变量和方法的功能。
        比如，要从一个string创建一个常量，那么就选定文本并按下alt+shift+l即可。如果同一个string在同一类中的别处出现，它会被自动替换。方法提取也是个非常方便的功能。将大方法分解成较小的、充分定义的方法会极大的减少复杂度，并提升代码的可测试性。
    
    ctrl+2，L：为本地变量赋值
        开发过程中，我常常先编写方法，如Calendar.getInstance()，然后通过ctrl+2快捷键将方法的计算结果赋值于一个本地变量之上。这样我节省了输入类名，变量名以及导入声明的时间。Ctrl+F的效果类似，不过效果是把方法的计算结果赋值于类中的域。
    
    ctrl+e：快速转换编辑器
        这组快捷键将帮助你在打开的编辑器之间浏览。使用ctrl+page down或ctrl+page up可以浏览前后的选项卡，但是在很多文件打开的状态下，ctrl+e会更加有效率。


###### 获取request response对象的类	

```
HttpServletRequest request = ServletActionContext.getRequest();
```


###### eclipse排除class目录里svn文件
    使用Eclipse编译文件后，classes文件中总是有.svn的文件夹，这些文件没有什么用，
	而且影响build的速度"Project->Properties->Java Build Path"，右侧的面板中的"Source"选项卡，
	在Excluded中加入"**/.svn/**"，就可以将所有的svn文件排除在编译路径中了。 


###### myeclipse10插件安装方式
	一、通过MyEclipse Configuration Center在线安装

	1. 打开MyEclipse10，在菜单栏选择MyEclipse→MyEclipse Configuration Center，即可进入到MyEclipse Configuration Center。

	2. 在MyEclipse Configuration Center界面中点击Software选项卡，在Software界面中点击add site，在弹出框输入信息
		Name : SVN
		URL : http://subclipse.tigris.org/update_1.8.x

	3. 等待一段时间，MyEclipse Configuration Center界面右上角会出现 Apply change，点击即可完成安装。

 
	二、解压安装

	下载SVN的zip文件 site-1.8.4.zip，直接把文件下的features目录和plugins目录解压到MyEclipse安装目录下的dropins目录即可(MyEclipse→MyEclipse 10→dropins)，重启即可。
 

	三、创建link文件指向插件位置（推荐）

	1. 同样下载SVN的zip文件 site-1.8.4.zip，把文件下的features目录和plugins目录解压到任意位置

	2. 在MyEclipse安装目录下的dropins目录创建.link文件，如svn.link。

	3. 编辑svn.link文件，输入 path=第一步解压的features文件夹和plugins文件夹所在的目录，如 path=D:/Plugin/SVN。重启即可。

###### myeclipse启动编码
	/myeclipse.ini
	-Dfile.encoding=UTF-8

###### eclipse启动可选工作目录
	eclipse-3.2.0\configuration\.settings\org.eclipse.ui.ide.prefs
		修改SHOW_WORKSPACE_SELECTION_DIALOG=false为SHOW_WORKSPACE_SELECTION_DIALOG=true
		
###### svn插件安装
    安装subclipse, MyEclipse9.0 SVN插件
    1、从官网下载site-1.6.10.zip文件,网址    是:subclipse.tigris.org,
    2、从中解压出features与 plugins文件夹，复制到E:\MyEclipse\myPlugin\svn里面
    
##### Eclipse默认还提供了很多代码模板。打开 
	Windows->Preferences->Java->Editor->Templates，可以看到所有已定义的代码模板列表。
	
###### 自定义代码模板
	Windows->Preferences->Java->Editor->Templates 点击New...，新建代码模板，创建一个名为“xinneng“的模板。
	(注意：所有“${}”都是模板变量，如${line_selection}表示当前光标选中的代码片段，${cursor}表示代码生成结束后光标所处的位置，还有很多参数大家可以参考Eclipse提供的帮助文档。)
	完成后，选中要测试的代码块，使用快捷键Alt+Shift+Z，可以看到菜单中多了一项xinneng
    
###### eclipse复制工作空间配置

	1、找到旧的工作空间的配置文件目录：\.metadata\.plugins\org.eclipse.core.runtime
	2、将该目录下的.settings文件复制到新的工作空间的配置文件目录下：
	      \.metadata\.plugins\org.eclipse.core.runtime


###### eclipse无法导入Java项目时常遇到的两种情况：
	1、Some projects cannot be imported because they already exist in the workspace
	2、Some projects were hidden because they exist in the workspace directory
	原因：workspace中已经存在了相同名字的项目，所以不能导入。
	解决：
	1、修改项目名：右击--- refactor --- rename 或 F2
	2、打开项目中.project文件 --- 修改<name>projectName</name>

	3、工作空间并不存在同名项目，定是还有地方记录了之前的工程信息，可能是。。。
	找到:\xxxxxxxx\workspace\.metadata\.plugins\org.eclipse.core.resources\.projects 文件夹，删除同名文件夹。
