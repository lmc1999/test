# git使用

## 设置签名（用户名或email地址）

git config user.name tom_pro 项目级别/仓库级别：仅在当前本地库范围内有效

git config --global user.name tom_glb 系统用户级别：登录当前操作系统的用户范围

### 级别优先级：

- 就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别 的签名
- 如果只有系统用户级别的签名，就以系统用户级别的签名为准
- 二者都没有不允许

git add xxx

git commit -m "describe"  xxx

git status

## 本地库的前进后退

- 基于索引值操作[推荐]

git reset --hard [局部索引值] 

git reset --hard a6ace91

- 使用^符号：只能后退

git reset --hard HEAD^

注：一个^表示后退一步，n 个表示后退 n 步

- 使用~符号：只能后退

git reset --hard HEAD~n

注：表示后退 n 步

### 删除文件找回

前提：删除前，文件存在时的状态提交到了本地库。

操作：git reset --hard [指针位置] 

删除操作已经提交到本地库：指针位置指向历史记录

删除操作尚未提交到本地库：指针位置使用 HEAD

## 分支

- 创建分支 git branch [分支名]
- 查看分支 git branch -v 
- 切换分支 git checkout [分支名]

### 合并分支

1. 第一步：切换到接受修改的分支（被合并，增加新内容）上 git checkout [被合并分支名]
2. 第二步：执行 merge 命令 git merge [有新内容分支名]

### 解决冲突

### 冲突的表现

### 冲突的解决

1. 第一步：编辑文件，删除特殊符号
2. 第二步：把文件修改到满意的程度，保存退出
3. 第三步：git add [文件名]
4. 第四步：git commit -m "日志信息"

注意：此时 commit 一定不能带具体文件名

## 远程库

git remote -v 查看当前所有远程地址别名

git remote add [别名] [远程地址]

对地址进行操作：

git clone [远程地址]

以下都是对分支进行操作

git push [别名] [分支名]

pull=fetch+merge

git fetch [远程库地址别名] [远程分支名] 

git merge [远程库地址别名/远程分支名] 

git pull [远程库地址别名] [远程分支名]

注意：

`fatal: refusing to merge unrelated histories`
（拒绝合并不相关的历史）

## 解决

出现这个问题的最主要原因还是在于本地仓库和远程仓库实际上是独立的两个仓库。假如我之前是直接clone的方式在本地建立起远程github仓库的克隆本地仓库就不会有这问题了。

查阅了一下资料，发现可以在pull命令后紧接着使用`--allow-unrelated-history`选项来解决问题（该选项可以合并两个独立启动仓库的历史）。

命令：

```git
$git pull origin master --allow-unrelated-histories
```

## 更新：

git主要分为三部分 本地操作；远程操作；局域网操作。 本地操作：status add commit diff reflog reset --hard [局部索引值] 删除指向历史位置 commit -m "" [文件名] 分支操作： git branch [分支名] git branch -v git checkout [分支名] 合并分支： git checkout [被合并分支名] git merge [有新内容分支名] 远程操作： git remote -v push clone pull=fetch+merge 跨团队协作： fork;pull request;merge pull request;confirm merge

报错警告： $ git push githubtest master Logon failed, use ctrl+c to cancel basic credential prompt. To https://github.com/lmc1999/test.git ! [rejected] master -> master (non-fast-forward) error: failed to push some refs to 'https://github.com/lmc1999/test.git' hint: Updates were rejected because the tip of your current branch is behind hint: its remote counterpart. Integrate the remote changes (e.g. hint: 'git pull ...') before pushing again. hint: See the 'Note about fast-forwards' in 'git push --help' for details.

跨团队： fork pull request merge pull request

git导入，ecilipse忽略文件、推送、拉取、解决冲突。