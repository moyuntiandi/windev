### Git
#### 代码提交

1.暂存管理
git stash
git stash pop

2.回滚到上一个版本
git reset --soft HEAD^

3.将本地的状态回退到和远程的一样 
git reset –hard origin/master

4.回退到某个版本
git reset 057d
#### 分支管理
1.新建分支
~~~
git checkout -b {分支名}
例如git checkout -b test
~~~
2.推送到服务器
~~~
git push origin {分支名}
例如git push origin test:test
~~~
3.跟踪远程分支
~~~
git branch --set-upstream test origin/test
~~~
#### 冲突解决
1.合并工具beyong compare的配置
~~~
.gitconfig文件修改如下
[merge]
tool = bc3
[mergetool "bc3"]
cmd = \"c:/Program Files/Beyond Compare 4/bcomp.exe\" \""$PWD/$LOCAL"\" \""$PWD/$REMOTE"\" \""$PWD/$BASE"\" \""$PWD/$MERGED"\"
trustExitCode = false
path = c:/Program Files/Beyond Compare 4/bcomp.exe
[diff]
tool = bc3
[difftool "bc3"]
path = c:/Program Files/Beyond Compare 4/bcomp.exe
[mergetool]
keepBackup = false
~~~
2.test分支合并到master
~~~
git checkout master
git pull
git merge test
~~~
3.开始合并,此时会看到出现了冲突提示
~~~
git mergetool
按回车键,此时会弹出之前配置的beyong compare
左边的LOCAL字样是本地当前分支的代码(master)
右边的REMOTE是待合并分支的代码(test)
中间是两个分支父节点的代码
点击beyong compare上方的叉叉,退出程序，继续下一个冲突文件
提交修改,并push到服务器
~~~

### GitLab
[Gitlab开发模式](image/GitLab开发模式.png)
