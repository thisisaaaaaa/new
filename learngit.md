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

## 7.github

_git的服务器仓库_

* 下载此电脑的ssh
* 点击主页GitHub头像->settings->SSH and GPG keys(左侧)->将id_rsa.pub的内容添加进去即可

_设置双向仓库_

