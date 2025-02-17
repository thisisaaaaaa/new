# learngit

## 1.add && commit

```shell
git add readme.txt
git commit -m "the 1st version"
```

## 2.status && diff

```shell
git status #查看git目前在哪一个branch上，以及该branch的状态
git diff readme.txt #查看文件的变化
```

## 3.log && reset && reflog

```shell
git log
git log --pretty=oneline #可以看到每一个版本的id
git reset --hard HEAD^ #HEAD~10,往上数10个版本
#hard选项表明，这是回退到上个版本已经提交的状态
#当然也可以通过版本id恢复
不幸的是，你已经关闭终端...

```

```
在git中，总是有后悔药可以吃的。 ---廖雪峰
```

```shell
git reflog #追溯你的每一步动作
```

## 4.Repositoty(版本库)

![repo](D:\repo.png)

```shell
git 的优越性就在于其对每次修改的追踪而不是对每一个文件的追踪
换言之，一个文件的所有状态都可以被 git 感知，而不是只在乎当前的状态
```

## 5.checkout

```shell
git checkout -- readme.txt #修改之后没有再add的情况
git reset HEAD readme.txt #将当前缓存区的readme.txt文件舍弃到工作区
#适用于已经add的情况
```

## 6.rm

```shell
git rm <file>#在工作区删除文件后 
该命令等价于 git add <file>
git commit -m "delete sth." #难道是修改版本库的日志吗？
```

## 7.github(push && rm)

```bash
git remote add origin git@github.com:michaelliao/learngit.git
git branch -M main #分支改名
git push origin main #推送
git remote rm origin
#还有查看远程仓库信息，分支等等，文ai就对了
```



_git的服务器仓库_

* 下载此电脑的ssh
* 进入git bash

  ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@xx.com"
   cat ~/.ssh/id_rsa.pub
  ```
* 点击主页GitHub头像->settings->SSH and GPG keys(左侧)->将id_rsa.pub的内容添加进去即可
* create new repo.
* 根据提示，选择将已有的仓库与之关联（第二种，第一种笨人也没搞懂是在干嘛）

_设置双向仓库  √_

```
如果一切顺利的话...
```



### Q1.生成密钥对

现在大多数windows系统已经默认下载了OpenSSH，所以直接在git bash中生成ssh密钥即可

如果不能正常生成，设置->系统->可选功能->添加功能->添加OpenSSH应用

### Q2. remote origin already exists.

[解决方法](https://blog.csdn.net/u014712086/article/details/107005216?ops_request_misc=%7B%22request%5Fid%22%3A%2274f0f6579e34356ab7abd83a14cc157b%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=74f0f6579e34356ab7abd83a14cc157b&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-107005216-null-null.142^v101^control&utm_term= remote origin already exists.&spm=1018.2226.3001.4187)

### Q3.connect to host github.com port 22: Connection refused

笨人直接采用改端口的方法

详情请移步[here](https://blog.csdn.net/weixin_43200566/article/details/139920373?ops_request_misc=%7B%22request%5Fid%22%3A%2276a3207c51ba34f40922575031767f40%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=76a3207c51ba34f40922575031767f40&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-139920373-null-null.142^v101^control&utm_term=connect to host github.com port 22%3A Connection refused&spm=1018.2226.3001.4187)

**结果报错**

```bash
$ ssh -T git@github.com
/c/Users/shenqiuyu/.ssh/config line 1: no argument after keyword "\377\376h"
/c/Users/shenqiuyu/.ssh/config: terminating, 1 bad configuration options
```

```
确保文件是以 ASCII 或 UTF-8 编码保存的。如果您使用的是 Windows 系统，一些文本编辑器（如 Notepad++）允许您查看和更改文件的编码。---文心一言
```

**避免使用windows的自带文本编辑器！别忘了，我们的好朋友vscode编！辑！器！**

### Q4.error: src refspec master does not match any error: failed to push some refs to ‘github.com:github

说，我的master分支与origin仓库的分支不匹配

well，ok，fine

我改我改

```shell
 git branch -M main
 git push origin main
```



**<u>结论就是，珍惜每一次报错提示，多方搜索，而不是像笔者一样，反复回头重试已经行不通的路。</u>**



## 8.clone

```shell
git clone git@github.com:user_name/repository_name.git
#在code -> local中查看
```

## 9.branch && switch && merge 

```shell
git branch <name>
git switch <name>
git switch -c <name> #创建并切换
git merge <name> #合并某个分支到当前分支
git branch -d <name> #删除分支
```

**遇到同一文件在不同分支上被反复提交，注意手动修改**

## 10. --no-ff选项

保留dev指针及其单独指向的文件

```bash
git merge --no-ff -m "merge with on-ff" dev
```



## 11.bug分支

```bash
git stash #暂时移走工作区中不能commit的内容
git switch -c issue-101 #创建分支修bug
git add bug.txt
git commit -m "fix the bug"
git switch main
git merge issue-101
git stash pop #恢复现场
```



## 12.branch -D

```shell
git branch -D <name> #强行删除未合并的分支
```

## 13.合作

```shell
git clone git@github.com:user_name/repository_name.git
git checkout -b dev origin/dev
git branch --set-upstream-to=origin/dev dev #将本地分支与远程分支建立联系
git pull #手动合并
```



## 14.rebase

_变直_

## 15.tag

```shell
git tag <tagname> #用于新建一个标签，默认为HEAD，也可以指定一个commit id；
git tag -a <tagname> -m "blablabla..." #可以指定标签信息；
git tag #可以查看所有标签。

```



```shell
git push origin <tagname> #可以推送一个本地标签；
git push origin --tags #可以推送全部未推送过的本地标签；
git tag -d <tagname> #可以删除一个本地标签；
git push origin :refs/tags/<tagname> #可以删除一个远程标签
```





## 16.fork

## fork -> clone -> pull request(maybe) 

# git的尽头是SourceTree

移步[Sourcetree | Free Git GUI for Mac and Windows](https://www.sourcetreeapp.com/)



