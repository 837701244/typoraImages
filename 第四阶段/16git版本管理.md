# GIT配置



## 服务器注册

注册地址: https://gitee.com/ 
工具地址: https://git-scm.com/download/win

![](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/gengyahui/20220729170248.png)

## 运行 Git 前的配置

### 用户信息配置

第一个要配置的是你个人的用户名称和电子邮件地址。这两条配置很重要，每次 Git 提交时都会引用这两条信息，说明是谁提交了更新，所以会随更新内容一起被永久纳入历史记录：

```bash
$ git config --global user.name "shuke"
$ git config --global user.email xxxx@example.com
```

如果用了 --global 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的仓库都会默认使用这里配置的用户信息。如果要在某个特定的仓库中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前仓库的 .git/config 文件里。

如果你是使用 `https` 进行仓库的推拉，你可能需要配置客户端记住密码，避免每次都输入密码

```bash
$ git config --global credential.helper store
```

###  查看配置信息

要检查已有的配置信息，可以使用 git config --list 命令：

```bash
$ git config --list
```

也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：

```bash
$ git config user.name
```

##  现有仓库克隆

克隆仓库的命令格式为 **`git clone [url]`** 

```bash
$ git clone https://gitee.com/dashantu/web62pro.git
cd web62pro
```

## 代码更新

**git pull** 命令用于从远程获取代码并合并本地的版本。

```bash
$ git pull
# or
$ git pull origin master  #取回 origin/master 分支，再与本地的 master 分支合并。
```



# GUI 界面版

## 使用图形界面

![image-20220917001556880](K:\_woniu_shuke\web62\stage4\node\git版本管理.assets\image-20220917001556880.png)



![image-20220916235933325](K:\_woniu_shuke\web62\stage4\node\git版本管理.assets\image-20220916235933325.png)

### 右键: git GUI Here

| 功能                        | 说明                 | 命令                                 |
| --------------------------- | -------------------- | ------------------------------------ |
| Rescan                      | 扫描改动             | git status    /  git status -s       |
| Stage Changed               | 添加到暂存区         | git add .                            |
| Sign Off                    | 签名到结尾           | `git commit -m message --signoff`    |
| Commit                      | 暂存区提交版本到仓库 | git commit -m message                |
| push                        | 仓库推送上传到服务器 | git push                             |
| Stage Changeds(Will Commit) | 撤销暂存区           | git reset  / git restore --staged ./ |
| Unstaged changes            | 未加入暂存区         |                                      |
| Portions Staged for commit  | 部分文件修改信息     |                                      |

![](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/gengyahui/20220729170322.png)

# Bash 命令行 扩展

##  获取 Git 帮助

[git 命令](https://gitee.com/help/labels/79)想了解 Git 的各式工具该怎么用，可以阅读它们的使用帮助，方法有三：

```bash
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
# 比如，要学习 config 命令可以怎么用，运行：
$ git help config
```

## 查看git提交的日志

```
$ git log
```

## Commit message 编写指南

在 Git 中，每次提交代码，都要写 Commit message（提交说明），否则就不允许提交。这个操作将通过 git commit 完成。

```
git commit -m "add shuke.md"
```

> 上面代码的-m参数，就是用来指定 commit mesage 的。

## 代码冲突

冲突合并一般是因为自己的本地做的提交和服务器上的提交有差异，并且这些差异中的文件改动，Git不能自动合并，那么就需要用户手动进行合并

如我这边执行`git pull origin master`

退出之后，确保所有的冲突都得以解决，然后就可以使用

```
git add .
git commit -m "fixed ok"
git push  origin master`
```

##  回退指定版本

先在本地切换到远程仓库要回退的分支对应的本地分支，然后本地回退至你需要的版本，然后执行：

```
git reset --hard origin/master  //远程版本一样
git reset --hard 09a3175f069508424d345f39d6c7b44de04bce80
```

## 分支

| 命令                                                         | 解释                                         |
| ------------------------------------------------------------ | -------------------------------------------- |
| git branch                                                   | 列出所有本地分支                             |
| git branch -r                                                | 列出所有远程分支                             |
| git branch -a                                                | 列出所有本地分支和远程分支                   |
| git branch [branch-name]                                     | 新建一个分支，但依然停留在当前分支           |
| git checkout -b [branch]                                     | 新建一个分支，并切换到该分支                 |
| git branch [branch] [commit]                                 | 新建一个分支，指向指定commit                 |
| git branch --track [branch] [remote-branch]                  | 新建一个分支，与指定的远程分支建立追踪关系   |
| git checkout [branch-name]                                   | 切换到指定分支，并更新工作区                 |
| git checkout -                                               | 切换到上一个分支                             |
| git branch --set-upstream [branch] [remote-branch]           | 建立追踪关系，在现有分支与指定的远程分支之间 |
| git merge [branch]                                           | 合并指定分支到当前分支                       |
| git cherry-pick [commit]                                     | 选择一个commit，合并进当前分支               |
| git branch -d [branch-name]                                  | 删除分支                                     |
| git push origin --delete [branch-name]<br />git branch -dr [remote/branch] | 删除远程分支                                 |

## 其它信息扩展

| 命令                                                | 解释                                                       |
| --------------------------------------------------- | ---------------------------------------------------------- |
| git status                                          | 显示有变更的文件                                           |
| git log                                             | 显示当前分支的版本历史                                     |
| git log --stat                                      | 显示commit历史，以及每次commit发生变更的文件               |
| git log -S [keyword]                                | 搜索提交历史，根据关键词                                   |
| git log [tag] HEAD --pretty=format:%s               | 显示某个commit之后的所有变动，每个commit占据一行           |
| git log [tag] HEAD --grep feature                   | 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件 |
| git log --follow [file]<br />git whatchanged [file] | 显示某个文件的版本历史，包括文件改名                       |
| git log -p [file]                                   | 显示指定文件相关的每一次diff                               |
| git log -5 --pretty --oneline                       | 显示过去5次提交                                            |
| git shortlog -sn                                    | 显示所有提交过的用户，按提交次数排序                       |
| git blame [file]                                    | 显示指定文件是什么人在什么时间修改过                       |
| git diff                                            | 显示暂存区和工作区的差异                                   |
| git diff --cached [file]                            | 显示暂存区和上一个commit的差异                             |
| git diff HEAD                                       | 显示工作区与当前分支最新commit之间的差异                   |
| git diff [first-branch]...[second-branch]           | 显示两次提交之间的差异                                     |
| git diff --shortstat "@{0 day ago}"                 | 显示今天你写了多少行代码                                   |
| git show [commit]                                   | 显示某次提交的元数据和内容变化                             |
| git show --name-only [commit]                       | 显示某次提交发生变化的文件                                 |
| git show [commit]:[filename]                        | 显示某次提交时，某个文件的内容                             |
| git reflog                                          | 显示当前分支的最近几次提交                                 |
| git rm file                                         | 删除文件                                                   |

## 忽略上传文件

处理项目时，你可能不希望 git 跟踪某些文件夹；这些可以是 .env 文件、node_modules 文件夹等。

找到项目根目录下文件\.gitignore  忽略上传所有的  node_modules 文件

```text
# Build and Release Folders
bin-debug/
bin-release/
[Oo]bj/
[Bb]in/

# Other files and folders
.settings/

# Executables
*.swf
*.air
*.ipa
*.apk
node_modules
**/node_modules
# Project files, i.e. `.project`, `.actionScriptProperties` and `.flexProperties`
# should NOT be excluded as they contain compiler settings and other important
# information for Eclipse / Flash Builder.
```

## git 退出vim 编辑模式

```txt
1.先按下 esc；
2.输入 ：q
```



## 初始化新仓库

**git init** 命令用于在目录中创建新的 Git 仓库。

```
$ git init
```

可以看到在你的项目中生成了 **.git** 这个子目录，这就是你的 Git 仓库了，所有有关你的此项目的快照数据都存放在这里。

**.git** 默认是隐藏的.

## 将本地的仓库推送远程服务器

```bash
$ git push 
# or 
$ git push  https://gitee.com/***/test.git
```

