# git-branch-tutorial

推荐一下好友的 Blog [FEILONG-Git 分支（branch）的使用整理](http://www.feilong.tech/2016/07/31/Git-%E5%88%86%E6%94%AF%EF%BC%88branch%EF%BC%89%E7%9A%84%E4%BD%BF%E7%94%A8%E6%95%B4%E7%90%86/)

## 方法摘录

6）创建一个新的分支，并且切换到新的分支上面。

```
$ git branch new
$ git checkout new
Switched to branch 'new'
## 提示已经切换到new分支
```

7）此时在本地项目做一些改动，然后提交到github上面。

```
# git add/commit等操作省略
$ git push
fatal: The current branch new has no upstream branch.
To push the current branch and set the remote as upstream, use
    git push --set-upstream origin new
```

在`git push`的时候会提示新的分支没有添加到分支流中，然后使用提示的命令push一下。然后输入用户名和密码。

```
$ git push --set-upstream origin new
git: 'credential-osxkeychain' is not a git command. See 'git --help'.
Username for 'https://github.com': tyl569
Password for 'https://tyl569@github.com':
git: 'credential-osxkeychain' is not a git command. See 'git --help'.
Counting objects: 3, done.
Writing objects: 100% (3/3), 283 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/tyl569/test.git
 * [new branch]      new -> new
Branch new set up to track remote branch new from origin.
```

8）查看github，会看到合并分支的请求

查看一下test.txt文件，发现内容并没有改变，这是因为github把master作为主分支，如果两个分支不合并的话，另外的用户pull或者clone的时候，只会得到master分支的项目，这样如果用户随意搞new分支的内容，都不会影响master分支。


9）如果功能在new分支上面开发完之后，合并分支。

```
$  git checkout master
$ git merge new
Updating 97b26e5..96d3fe8
Fast-forward
 test.txt | 5 ++++-
 1 file changed, 4 insertions(+), 1 deletion(-)
```

10）这个时候，就会把new分支的改动，合并到master分支了，然后push

## 分支合并的作用：
- 可以独立开发某个功能或者模块
- 如果功能没有搞完，也可以push，对项目没有影响








