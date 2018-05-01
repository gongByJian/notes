##### Freemarker操作字符串

##### 1. substring（start,end）从一个字符串中截取子串
	start:截取子串开始的索引，start必须大于等于0，小于等于end
	end: 截取子串的长度，end必须大于等于0，小于等于字符串长度，如果省略该参数，默认为字符串长度。
	例子：
	${'str'?substring(0)} 结果为str
	${'str'?substring(1)} 结果为tr
	${'str'?substring(2)} 结果为r
	${'str'?substring(3)} 结果为
	${'str'?substring(0,0)} 结果为
	${'str'?substring(0,1)} 结果为s
	${'str'?substring(0,2)} 结果为st
	${'str'?substring(0,3)} 结果为str

##### 2. cap_first 将字符串中的第一个单词的首字母变为大写。
	${'str'？cap_first} 结果为Str
##### 3. uncap_first将字符串中的第一个单词的首字母变为小写。
	${'Str'？uncap_first} 结果为str
##### 4.  capitalize将字符串中的所有单词的首字母变为大写
	${'str'？ capitalize} 结果为STR

##### 5.  date,time，datetime将字符串转换为日期
	例如：
	<#assign date1="2009-10-12"?date("yyyy-MM-dd")>
	<#assign date2="9:28:20"?time("HH:mm:ss")>
	<#assign date3=" 2009-10-12 9:28:20"?time("HH:mm:ss")>
	${date1} 结果为2009-10-12
	${date2} 结果为9:28:20
	${date3} 结果为2009-10-12 9:28:20
	注意：如果指定的字符串格式不正确将引发错误。

##### 6. ends_with 判断某个字符串是否由某个子串结尾，返回布尔值。
	${"string"?ends_with("ing")?string} 返回结果为true
	注意：布尔值必须转换为字符串才能输出

##### 7. html 用于将字符串中的<、>、 &和"替换为对应得
	&lt;&gt;&quot:&amp

##### 8. index_of（substring,start）在字符串中查找某个子串，返回找到子串的第一个字符的索引，如果没有找到子串，则返回-1。
	Start参数用于指定从字符串的那个索引处开始搜索，start为数字值。
	如果start大于字符串长度，则start取值等于字符串长度，如果start小于0， 则start取值为0。
	${"string"?index_of("in")  结果为3
	${"string"?index_of("ab")  结果为-1

##### 9. length返回字符串的长度 
	${"string"?length} 结果为6

##### 10. lower_case将字符串转为小写
	${"STRING"?lower_case} 结果为string

##### 11. upper_case将字符串转为大写
	${"string"?upper_case} 结果为STRING

##### 12. contains 判断字符中是否包含某个子串。返回布尔值
	${"string"?contains("ing")?string}  结果为true
	注意：布尔值必须转换为字符串才能输出

##### 13. number将字符串转换为数字
	${"111.11"?number} 结果为111.11

##### 14. replace用于将字符串中的一部分从左到右替换为另外的字符串。
	${"strabg"?replace("ab","in")}  结果为string

##### 15. split使用指定的分隔符将一个字符串拆分为一组字符串
	<#list "This|is|split"?split("|") as s>
	${s}
	</#list>
	结果为:
	This
	is
	split

##### 16.  trim 删除字符串首尾空格 ${" String "?trim}  结果为String
	<#if x == 1>
	  x is 1
	<#else>
	  x is not 1
	</#if>
	
	<#if x == 1>
	  x is 1
	<#elseif x == 2>
	  x is 2
	<#elseif x == 3>
	  x is 3
	</#if>