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

#### Git仓库迁移

Git为当前最流行的分布式代码管理工具，由于地区时间等差异，代码的同步可能会存在问题，那么需要在本地搭建
局部Git仓库，定时进行同步远程仓库．从而保证本地的开发不受影响．采用Gogs工具进行Gig仓库迁移，下面为迁移的
命令操作，下面的第二步可以在Gogs的管理页面上进行操作，直接创建一个新的仓库名称new_project_name.git即可

1.从原地址克隆一份裸版本库，比如原本托管于GitHub
~~~
git clone --bare git://192.168.10.XX/git_repo/project_name.git
~~~
2.到新的Git服务器上创建一个新项目，比如 GitCafe，如192.168.20.XX
~~~
cd /path/to/path/
mkdir new_project_name.git
git init --bare new_project_name.git
~~~
3.以镜像推送的方式上传代码到 GitCafe 服务器上
~~~
进入本地的裸版本仓库
cd project_name.git
git push --mirror git@192.168.20.XX/path/to/path/new_project_name.git
~~~

### GitLab
[Gitlab开发模式](image/GitLab开发模式.png)
