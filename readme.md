git主要分为三部分
本地操作；远程操作；局域网操作。
本地操作：status add commit diff reflog reset --hard [局部索引值] 删除指向历史位置
commit -m "" [文件名]
分支操作：
git branch [分支名]
git branch -v
git checkout [分支名]
合并分支：
git checkout [被合并分支名]
git merge [有新内容分支名]
远程操作：
git remote -v
push clone pull=fetch+merge
跨团队协作：
fork;pull request;merge pull request;confirm merge

报错警告：
$ git push githubtest master
Logon failed, use ctrl+c to cancel basic credential prompt.
To https://github.com/lmc1999/test.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/lmc1999/test.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

跨团队：
fork pull request merge pull request

git导入，ecilipse忽略文件、推送、拉取、解决冲突。
