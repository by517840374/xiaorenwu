###  简介

软件，帮助我们做版本控制

如果你是windows用户，需要下载一个git应用程序，一路点就行，没有什么需要注意的地方 

安装完成后在任一文件夹内右键都有显示，单击git bash here即可

![1562137676568](img/1562137676568.png)

### 简易的命令行入门教程:

#### Git 全局设置:

```python
git config --global user.name "name"  # 上传者的用户名
git config --global user.email "you@email.com" # 上传者的邮箱 配置一次即可，后面无需配置 这样就知道是谁上传的
```

![](http://q1cw3e2d5.bkt.clouddn.com/QQ%E5%9B%BE%E7%89%8720191112154020.jpg)

#### 创建 git 仓库:

```python
mkdir git	# 创建一个git文件夹
cd git	  # 切换到git文件夹
git init  # 初始化仓库
touch README.md   # 创建一个README文档(可建可不建)
git add README.md   # 将README.md添加到暂时缓存区中
git status  # 查看暂时缓存区的文件，查看是否选上
git commit -m "first commit"  # 给这个上传过程添加注释，简要说明上传的原因 也可以输入git log 查看之前上传的日志
git remote add origin https://gitee.com/test/git.git  # 将你码云仓库的网址用origin代替
git push -u origin master  # 推送上去 这个步骤是将本地的上传到远程码云仓库中，第一会提示输入密码
```

#### 第二次及以后上传

~~~python
在之前上传过的目录上传，只需要输入3个命令
1. git add . 或 git add test.txt 
# 第一个是把全部文件添加到暂时缓存区，即上传全部，第二个就是单个上传
2. git commit -m "Third upload"
# 添加简要说明
3. git push -u origin master
# 将需要上传的文件传输上去
~~~

### 进阶功能

```python
1.git status 即时查看状态

2.git log 查看日志

3.git reset --hard (git 查看到的commit id)
  git reset --hard 0b3720b5ba291318e0da5c88ee461a6d16e91e2c 
  # 回滚到这个id时的状态，将此时id之后做的操作都删除

4.git reflog # 回滚到刚才删除的信息时候的commit
  git reset --hard commit_id # 直接回到刚才被删时候的状态

5.
```

http://www.cnblogs.com/wupeiqi/p/7295372.html

#### git stash

```python
git stash
# 将未提交的修改放在暂存区
git stash pop # 把未提交的修改拿回来继续修改
# pycharm中有bug，会一直修改.idea中的workspace.xml文件，不要用pycharm，要不然会冲突

git stash             # 将当前工作区所有修改过的内容存储到“某个地方”，将工作区还原到当前版本未修改过的状态
git stash list        # 查看“某个地方”存储的所有记录
git stash clear     # 清空“某个地方”
git stash pop       # 将第一个记录从“某个地方”重新拿到工作区（可能有冲突）
git stash apply     # 编号, 将指定编号记录从“某个地方”重新拿到工作区（可能有冲突） 
git stash drop      # 编号，删除指定编号的记录

```

#### git branch 分支

```python
git branch # 查看当前分支
git branch dev # 创建dev
git branch -d dev # 删除dev分支
git checkout dev # 切换dev
git merge dev # 在master中执行代码，将dev合并到master

```

问题：当在开发某个功能到1/2时，如果想要回到原来的状态修复原来的代码。

​	master

​	dev(开发)

​	当要紧急修复bug了	

  1. [dev]将dev中现在正在开发的功能提交到dev

     git add .

     git commit -m "xxx"

		2. 切换回主分支

     git checkout master

		3. 创建并切换到bug分支

     git branch bug

     git checkout bug

     在bug分支上进行修复。。。

     git add .

     git commit -m "bug修复"

		4. git checkout master

     git merge bug（git merge --no-ff bug)

     git branch -d bug

		5. git branch 展示已有的环境

回答：创建一个bug分支，进行修复，修复完成后合并到master上

 6. 切换到dev继续开发

    git checkout dev 

    ......

    git add .

    git commit -m "开发完毕"

	7. git checkout master

    git merge dev

### git rebase 

```
git rebase -i c80dc1e, -i代表交互模式
git rebase 合并+将提交记录合并到一条主线->提交记录整洁
如果产生冲突：
	解决完冲突后，再执行
	git rebase --skip
rebase和merge都是提交的，但是rebase可以使提交线整洁

面试题：
```

### git log

```python
git log --oneline --graph --all # 显示分支图
```

### git clone

```
git clone https://gitee.com/test/xx.git
```



### git pull

```
git pull origin dev # 把dev拉下来 
# 在任何地方任何地点，只要公司的仓库能联网，就把它拉下来开发
git 
```

### 多人协同开发:每个人创建一个分支

公司是否做代码的review？谁来做？怎么做？

```
master
dev
	- review(组长做代码review)
	- kouxl
	- hen
一般：小功能1/2/3天一次merge

面试题：邀请其他人一起开发
	- 项目合作者。
	- 创建组织，邀请成员
	
	
面试题:fork  代码
		- fork代码到自己目录
		- 修改代码
		- 创建pull request
```

### git之gitignore文件

```
创建.gitignore文件，编写git忽略一些你想忽略的文件名
例如在里面写上100.md,不管你对100.md文件做了什么修改，都不会被检测到，git status不会检测到它

```

用于定义v1 v2 等版本

### git tag

作业：

	- 模拟自己创业
 - 协同开发
   	- 组长，创建仓库；合作者模式邀请成员
      	- master/dev/review
      	- 创建自己分支
- 切换到review分支，将个人分支上的代码合并到review
- 再将review分支push到代码仓库【可能报错】
  - 如果报错：有人已经在这段时间先提交了
  - 解决冲突
- 再提交
- 组长在review分支，看一看
- 在本地合并到dev分支
- 将本地dev推动到代码仓库
- 组内设置两个人同时修改一个文件，产生冲突。

### ContentType

#### CORS