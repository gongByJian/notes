网络爬虫

大数据
	全文搜索服务器	
		solr 搜索

	搜索引擎
	    lucene
	    compass
		sphinx 基于SQL的全文检索引擎

前端框架
	ext	

前端编辑器
	FCKEditor	(浏览器不兼容)
	CKEditor
	kindeditor	

ireport 报表  快逸报表 jasperreports

饼状图 柱状图
	fusionCharts  JFreeChart

TREE
	JQUERY ZTREE
	DTree
	DXTree

jquery
	auto complete
	validate
	Form
	easyUI

工具
	bugfree    bug管理
	jenkins    持续集成
	svn
	UML建模、pd、visio、Enterprise Architect、rose、
	jira
	confluence

第三方网站
	短信发送  https://luosimao.com/service/sms   阿里大鱼
	聚合支付  ping++

概念
	OAuth（开放授权） --百度开放平台，腾讯开放平台等大部分的开放平台都是使用的OAuth 2.0协议作为支撑。
		是个安全相关的协议，作用在于，使用户授权第三方的应用程序访问用户的web资源，并且不需要向第三方应用程序透露自己的密码。
	restful   --环信API使用的是此种风格
		一种软件架构风格，设计风格而不是标准，只是提供了一组设计原则和约束条件。它主要用于客户端和服务器交互类的软件。
		URL定位资源，用HTTP动词（GET,POST,DELETE,DETC）描述操作。

poi、jxl
	jxl技术说明
		支持比较低版本的excel，比如Excel 95 ,97 ,2000，2003
		由于Excel版本比较低，导致最大行有限制，无法导出65535以上量级的数据
		对于内存，和时间的花费也比POI基于内存+磁盘的方式高。

		1. 读取Excel公式（可以读取Excel 97以后的公式）
		2. 生成Excel数据表（格式为Excel 97）
		3. 支持字体、数字、日期的格式化
		4. 支持单元格的阴影操作，以及颜色操作
		5. 修改已经存在的数据表
		6. 是最基础的excel api
		7. 小文件读取效率比较高
		8. 跨平台
	POI技术说明
		能保持Excel里原有的宏（但不能用它写新的宏）。
		不支持跨平台（主要就是Java语言）
		在一些业务场景中代码相对复杂，但是API丰富，支持多种模式的读写。
		支持比较新版本的excel.
		读写的时候比较占内存。
		读写的时候比较占内存。
		支持大数量大文件的读写操作。但是需要熟悉API。
		总体来说，对于简单的单表excel导入导出的需求，建议使用JXL。数据量稍微小点，占用内存少，速度快。
		对于报表类的，涉及月份数据量，多表数据聚合在一起建议使用POI。