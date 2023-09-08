                        **肯定会用到这些东西**
* git配置
    + 修改提交时编辑器 `git config --global core.editor vim`
    + 修改`.gitconfig`
    ```conf
    cat ~/.gitconfig 
    [user]
        email = 544088192@qq.com
        name = Joy Hou
    [alias]
        st = status
    ```
* 移除库中的文件
  `git rm file1 file2 --cache` `git ls-files`
* 在当前分支上新建新分支，并提交
   + 在当前的develop分支上的修改暂存起来
    `git stash` 
   + 暂存修改后，在本地新建分支（add_feature1为新分支的名字）
     `git checkout -b add_feature1`
   + 将暂存的修改放到新建分支中
     `git stash pop`
   + 使用命令进行常规的add、commit步骤
     `git add file1 file2 file3`
      `git commit -a "修改内容"`
   + 将提交的内容push到远程服务器(在远程也同步新建分支add_feature1)
     `git push origin add_feature1`
     
* user-develop分支合并到master分支（受权限控制，网页上merge）
   + master分支 给user分支取名 `git checkout master` `git checkout -b user-develop`
   + 经过一段时间user-develop开发后，`git stash`  `git checkout master; git pull` 更新master
   + `git checkout user-develop;git stash pop` `git merge master` 合并master分支到user-develop上方便提交
   + `git push orgin user-develop`
   + 网页上 merge request（master）.
         
* 怎么合并分支到`master`
    - 在`.vim`中更新了`solarized`, 发现在`bundle/solarized`中存在2分支分别为`...5ce16744`和`master`，其中`744`为修改了本地文件，然后本地提交后的默认分支号,这时需要将该分支合并到`master`中并传到`github`上.
        + 切换到master分支 `git checkout master`
        + 给临时分支取名字 `git branch develop fb33f1a` (切换时，git会提示取名字的命令)
        + 同步远程和本地master分支代码 `git pull`
        + 合并临时分支 `git merge develop`
        + 删除临时分支 `git branch -d develop`
        + 上传github代码 `git push`

* 合并自己本地的多次提交为一个commit.
    + `git rebase -i [startpoint] [endpoint]` endpoint不填写则会默认为当前head指向的commit.
    + 合并多次提交的commit 在交互界面中 填写 `squash xxxx` (和前一个进行合并) 然后`:wq`保存
          退出会进入注释修改交互界面
    + 修改注释然后保存退出`:wq`
    + 合并多次commit已完成

* 获取主分支上部分更新(master中更新太频繁,全部更新担心影响其它功能)
    + 利用`rebase`

* 从指定版本生成到现在版本的patch文件(比如要上传修改代码的补丁包)
    `git format-patch 35e4f319eec77aa19d5b04cf1efa14a5624b74ae` ->生成`001-ptp-1588.patch` 名字是自动生成的
  
* 打tag和push tag  
     `git tag v1.0 -m "第一个tag." ; git push origin v1.0`
  
