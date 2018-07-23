
##### 查看用户
```
	git config user.name
```

##### 查看邮箱

```
	git config user.email
```

##### 配置或切换git用户名: 

```
	git config --global user.name "YOURUSERNAME"
```

##### 配置或切换git邮箱： 

```
	git config --global user.email "YOUREMAIL"
```

##### 检查是否已生成密钥 

```
cd ~/.ssh
	ls如果有3个文件，则密钥已经生成，id_rsa.pub就是公钥
如果没有生成，那么通过
	ssh-keygen -t rsa -C "youremail"
	来生成密钥
会提示生成秘钥的文件名及设置密码和确认密码  如果都不需设置 则直接三次回车
```
##### ssh测试连接

```
	ssh -T git@github.com
```

##### clone远程仓库

```
	git clone git@git.xxx.com:xxx.git
```

##### 常用命令:

```
//把这个目录变成Git可以管理的仓库
	git init 
//文件添加到仓库
	git add README.md 
//不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 
	git add . 
//把文件提交到仓库 引号内是备注
	git commit -m "first commit" 
//关联远程仓库
	git remote add origin https://github.com/xxx.git
//把本地库的所有内容推送到远程库上
	git push -u origin master
git查看远程仓库地址命令：
	git remote -v
```

##### 新建git项目

```
echo "# java-zookeeper" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/xxx.git
git push -u origin master
```

##### 版本回复

```
git reset --hard 1094a(版本号)
版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。
```

##### 其他

```
匹配远程仓库
	git fetch

alias自定义命令
	git ac 'add 1.txt'

强制push
	git push -f origin master

git checkout

commit修正  还是一次commit
	git commit --amend

打tag
	git tag
查看tag
	git show vx.x.x
```

#####  git解决冲突 

```
先commit到本地仓库  然后pull远程仓库
最后合并并提交
```

