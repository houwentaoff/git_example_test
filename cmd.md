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
