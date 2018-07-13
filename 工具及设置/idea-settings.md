##### 设置编码
    第一步：找到intellij idea安装目录，bin文件夹下面
    idea64.exe.vmoptions和idea.exe.vmoptions这两个文件，
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

##### 设置样式

```
file->settingg->Appearance&Behavior->Appearance->Theme 
改为IntelliJ 背景为白色
默认Darcula 全黑色
```

##### 更改代码快捷键
    设置-->editor-->code templates-->设置快捷键
    譬如main方法的快捷键在other, System.out.println();的快捷键在output

##### 设置自动代码提示
    设置-->keymap-->搜basic设置成ALT+/

##### 智能提示忽略大小写 ####
	Editor --> Code Completion页里有个Case sensitive completion，
	可以设置只第一个字母敏感、完全敏感或者不敏感。

##### 设置JDK编译版本 ####
	Compiler --> Java Compiler页里有个
	Project bytecode version(leave blank for jdk default)设置JDK的版本，
	要不然编译的时候会出现各种问题。

##### 显示行号 ####
	Editor --> Appearence 页面中 Show Line Number 勾上。

##### 取消拼音检查 ####
	Spelling 页面中 Configure 'Spelling' inspection 点击然后取消 Spelling 选项。
	取消不使用对象的检查（搜索never used 关键字将其中的unused的检查去掉）

##### 取消自动保存文件功能 ####
	General 页面中
	勾掉 Synchronize file on frame activation 选项（同步文件功能，酌情考虑可以不取消）
	勾掉 Save files on framedeactivation 选项
	勾掉 Save files automatically 选项，并将自动保存时间间隔，设置为30秒

##### 编辑过的文件显示“*”标记 ####
	Editor –-> Editor Tabs 页面中勾上 Mark modifyied tabs with asterisk 选项，
	修改后的文件会跟elicpse一样显示“*”标记。

##### 让IntelliJ IDEA 启动的时候不打开工程文件  ####
	Settings --> General 页面中，勾掉 Reopen last project on startup 选项。

##### SVN添加项目报错（CreateProccess error=2 后面还有乱码） ####
	Version Control --> Subversion 页面中勾掉“Use commmand line client:”选项后，
	就可以了，然后会提示你选择svn 1.6、svn 1.7、svn 1.8等版本。（好像只有Idea 13 才有这个问题）

##### 关于Idea中右边的maven projects窗口找不到了如何调出来
	方法1.你点击一下你idea界面最左下角的那个小框，maven应该从里面找到
	
	方法2.点击菜单栏View->Tool  Windows->Maven projects 
	
	方法3.点击菜单栏Help->Find Action(Ctrl+Shift+A),输入Maven projects

##### idea 2018 license server

```
http://idea.congm.in
http://xdouble.cn:8888/
```

##### 取消 import * 星号导包
	Setting -- Editor -- Code Style -- Java -- Imports
	在【Class count to use import with '*':】后填入500
	
	在【Names count to use static import with '*':】后填入500
	具体数值自行填写，够大即可
