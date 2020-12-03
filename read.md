Just For Test!

git add xxx

git commit -m "describe"  xxx

git status

git remote -v 查看当前所有远程地址别名

git remote add [别名] [远程地址]

git clone [远程地址]

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

git主要分为三部分 本地操作；远程操作；局域网操作。 本地操作：status add commit diff reflog reset --hard [局部索引值] 删除指向历史位置 commit -m "" [文件名] 分支操作： git branch [分支名] git branch -v git checkout [分支名] 合并分支： git checkout [被合并分支名] git merge [有新内容分支名] 远程操作： git remote -v push clone pull=fetch+merge 跨团队协作： fork;pull request;merge pull request;confirm merge

报错警告： $ git push githubtest master Logon failed, use ctrl+c to cancel basic credential prompt. To https://github.com/lmc1999/test.git ! [rejected] master -> master (non-fast-forward) error: failed to push some refs to 'https://github.com/lmc1999/test.git' hint: Updates were rejected because the tip of your current branch is behind hint: its remote counterpart. Integrate the remote changes (e.g. hint: 'git pull ...') before pushing again. hint: See the 'Note about fast-forwards' in 'git push --help' for details.

跨团队： fork pull request merge pull request

git导入，ecilipse忽略文件、推送、拉取、解决冲突。