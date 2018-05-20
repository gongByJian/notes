##### 1.安装

​	注意在安装时勾选Add to explorer context menu，这样在右键单击文件时就可以直接使用Sublime Text打开。


		添加Sublime Text到环境变量
		使用Win + R运行sysdm.cpl打开“系统属性”。
		在“高级”选项卡里选择“环境变量”，编辑“Path”，增加Sublime Text的安装目录（例如D:Program FilesSublime Text 3）。
		接下来你就可以在命令行里面利用subl命令直接使用Sublime Text了：
		subl file :: 使用Sublime Text打开file文件
		subl folder :: 使用Sublime Text打开folder文件夹
		subl . :: 使用Sublime Text当前文件夹

###### 安装Package Control
		前文提到Sublime Text支持大量插件，如何找到并管理这些插件就成了一个问题，Package Control正是为了解决这个问题而出现的，利用它我们可以很方便的浏览、安装和卸载Sublime Text中的插件。
		进入Package Control的官网，里面有详细的安装教程。Package Control支持Sublime Text 2和3，本文只给出3的安装流程：
		使用Ctrl + `打开Sublime Text控制台。
		将下面的代码粘贴到控制台里：
		import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
	
		如果命令行安装失败，可以使用手动安装的方法.

##### 2.基本编辑

			Ctrl + Shift + P打开命令板
	
			Ctrl + Enter在当前行下面新增一行然后跳至该行；Ctrl + Shift + Enter在当前行上面增加一行并跳至该行。
			Ctrl + ←/→进行逐词移动，相应的，Ctrl + Shift + ←/→进行逐词选择。
	
			Ctrl + ↑/↓移动当前显示区域，Ctrl + Shift + ↑/↓移动当前行。
	
	选择（Selecting）
	
		Sublime Text的一大亮点是支持多重选择——同时选择多个区域，然后同时进行编辑。
		Ctrl + D选择当前光标所在的词并高亮该词所有出现的位置，再次Ctrl + D选择该词出现的下一个位置，在多重选词的过程中，使用Ctrl + K进行跳过，使用Ctrl + U进行回退，使用Esc退出多重编辑。
	
		有时我们需要对一片区域的所有行进行同时编辑，Ctrl + Shift + L可以将当前选中区域打散，然后进行同时编辑：
	
		有打散自然就有合并，Ctrl + J可以把当前选中区域合并为一行：

##### 3.Sublime Text 查找&替换

###### 快速查找&替换

		多数情况下，我们需要查找文中某个关键字出现的其它位置，这时并不需要重新将该关键字重新输入一遍然后搜索，我们只需要使用Shift + ←/→或Ctrl +D选中关键字，然后F3跳到其下一个出现位置，Shift + F3跳到其上一个出现位置，此外还可以用Alt + F3选中其出现的所有位置（之后可以进行多重编辑，也就是快速替换）。

###### 标准查找&替换

	另一种常见的使用场景是搜索某个已知但不在当前显示区域的关键字，这时可以使用Ctrl + F调出搜索框进行搜索：

###### 关键字查找&替换

		对于普通用户来说，常规的关键字搜索就可以满足其需求：在搜索框输入关键字后Enter跳至关键字当前光标的下一个位置，Shift + Enter跳至上一个位置，Alt + Enter选中其出现的所有位置（同样的，接下来可以进行快速替换）。
		Sublime Text的查找有不同的模式：Alt + C切换大小写敏感（Case-sensitive）模式，Alt + W切换整字匹配（Whole matching）模式，除此之外Sublime Text还支持在选中范围内搜索（Search in selection），这个功能没有对应的快捷键，但可以通过以下配置项自动开启。
			"auto_find_in_selection": true

##### 4.跳转到文件

		Ctrl + P会列出当前打开的文件（或者是当前文件夹的文件），输入文件名然后Enter跳转至该文件。
		需要注意的是，Sublime Text使用模糊字符串匹配（Fuzzy String Matching），这也就意味着你可以通过文件名的前缀、首字母或是某部分进行匹配：例如，EIS、Eclip和Stupid都可以匹配EclipseIsStupid.java。

###### 跳转到符号

		尽管是一个文本编辑器，Sublime Text能够对代码符号进行一定程度的索引。
		Ctrl + R会列出当前文件中的符号（例如类名和函数名，但无法深入到变量名），输入符号名称Enter即可以跳转到该处。此外，还可以使用F12快速跳转到当前光标所在符号的定义处（Jump to Definition）。
	
		比较有意思的是，对于Markdown，Ctrl + R会列出其大纲，非常实用。

###### 跳转到某行
		Ctrl + G然后输入行号以跳转到指定行：

###### 组合跳转

		在Ctrl + P匹配到文件后，我们可以进行后续输入以跳转到更精确的位置：
		@ 符号跳转：输入@symbol跳转到symbol符号所在的位置
		关键字跳转：输入#keyword跳转到keyword所在的位置
	
		: 行号跳转：输入:12跳转到文件的第12行。

###### 文件夹（Folders）

		Sublime Text支持以文件夹做为单位进行编辑，这在编辑一个文件夹下的代码时尤其有用。在File下Open Folder：
		你会发现左边多了一个侧栏，这个侧栏列出了当前打开的文件和文件夹的文件，使用Ctrl + K, Ctrl + B显示或隐藏侧栏，使用Ctrl + P快速跳转到文件夹里的文件。

##### 5.窗口&标签（Windows & Tabs）

		窗口（Window）
	
			使用Ctrl + Shift + N创建一个新窗口（该快捷键再次和搜狗输入法快捷键冲突，个人建议禁用所有搜狗输入法快捷键）。
			当窗口内没有标签时，使用Ctrl + W关闭该窗口。
			标签（Tab）
	
			使用Ctrl + N在当前窗口创建一个新标签，Ctrl + W关闭当前标签，Ctrl + Shift + T恢复刚刚关闭的标签。
			编辑代码时我们经常会开多个窗口，所以分屏很重要。Alt + Shift + 2进行左右分屏，Alt + Shift + 8进行上下分屏，Alt + Shift + 5进行上下左右分屏（即分为四屏）。
			Alt + Shift + 1 关闭分屏
	
		全屏（Full Screen）
	
			Sublime Text有两种全屏模式：普通全屏和无干扰全屏。
			个人强烈建议在开启全屏前关闭菜单栏（Toggle Menu），否则全屏效果会大打折扣。
			F11切换普通全屏.
			Shift + F11切换无干扰全屏.

##### 6.Sublime Text 风格

```
默认主题是Monokai Bright
```

##### 7.快捷键列表（Shortcuts Cheatsheet）

我把本文出现的Sublime Text按其类型整理在这里，以便查阅。

###### 通用（General）

		↑↓←→：上下左右移动光标，注意不是不是KJHL！
		Alt：调出菜单
		Ctrl + Shift + P：调出命令板（Command Palette）
		Ctrl + `：调出控制台

###### 编辑（Editing）

		Ctrl + Enter：在当前行下面新增一行然后跳至该行
		Ctrl + Shift + Enter：在当前行上面增加一行并跳至该行
		Ctrl + ←/→：进行逐词移动
		Ctrl + Shift + ←/→进行逐词选择
		Ctrl + ↑/↓移动当前显示区域
		Ctrl + Shift + ↑/↓移动当前行
		Ctrl + KU 转为大写
		Ctrl + KL 转为小写

###### 选择（Selecting）

		Ctrl + D：选择当前光标所在的词并高亮该词所有出现的位置，再次Ctrl + D选择该词出现的下一个位置，在多重选词的过程中，使用Ctrl + K进行跳过，使用Ctrl + U进行回退，使用Esc退出多重编辑
		Ctrl + Shift + L：将当前选中区域打散
		Ctrl + J：把当前选中区域合并为一行
		Ctrl + M：在起始括号和结尾括号间切换
		Ctrl + Shift + M：快速选择括号间的内容
		Ctrl + Shift + J：快速选择同缩进的内容
		Ctrl + Shift + Space：快速选择当前作用域（Scope）的内容

###### 查找&替换（Finding&Replacing）

		F3：跳至当前关键字下一个位置
		Shift + F3：跳到当前关键字上一个位置
		Alt + F3：选中当前关键字出现的所有位置
		Ctrl + F/H：进行标准查找/替换，之后：
		Alt + C：切换大小写敏感（Case-sensitive）模式
		Alt + W：切换整字匹配（Whole matching）模式
		Alt + R：切换正则匹配（Regex matching）模式
		Ctrl + Shift + H：替换当前关键字
		Ctrl + Alt + Enter：替换所有关键字匹配
		Ctrl + Shift + F：多文件搜索&替换

###### 跳转（Jumping）

		Ctrl + P：跳转到指定文件，输入文件名后可以：
		@ 符号跳转：输入@symbol跳转到symbol符号所在的位置
		关键字跳转：输入#keyword跳转到keyword所在的位置
	
		: 行号跳转：输入:12跳转到文件的第12行。
		Ctrl + R：跳转到指定符号
		Ctrl + G：跳转到指定行号

###### 窗口（Window）

		Ctrl + Shift + N：创建一个新窗口
		Ctrl + N：在当前窗口创建一个新标签
		Ctrl + W：关闭当前标签，当窗口内没有标签时会关闭该窗口
		Ctrl + Shift + T：恢复刚刚关闭的标签

###### 屏幕（Screen）

		F11：切换普通全屏
		Shift + F11：切换无干扰全屏
		Alt + Shift + 2：进行左右分屏
		Alt + Shift + 8：进行上下分屏
		Alt + Shift + 5：进行上下左右分屏
		分屏之后，使用Ctrl + 数字键跳转到指定屏，使用Ctrl + Shift + 数字键将当前屏移动到指定屏