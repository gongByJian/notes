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