ssh-keygen -t rsa -C "2361883887@qq.com"


查看用户
	git config user.name
查看邮箱
	git config user.email
切换git用户名: 
	git config --global user.name "YOURUSERNAME"
切换git邮箱： 
	git config --global user.email "YOUREMAIL"

版本回复
git reset --hard 1094a(版本号)
版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。

新建git项目
echo "# java-zookeeper" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/zhuyizhuo/java-zookeeper.git
git push -u origin master


git fentch

git ac 'add 1.txt'

强制push
git push -f origin master

git checkout

commit修正  还是一次commit
git commit --amend 

打tag
git tag

git show vx.x.x


alias