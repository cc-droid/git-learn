# 一.版本初始化

配置git：

git config --global user.name "xxx@xxx"

git config --global user.email "xxx@xxx"

进入文件夹 `git init`

# 二.版本管理基础

- 检查文件状态

  git status

  ```shell
  $ git status
  On branch master
  No commits yet
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          readme.md
          test.txt
  nothing added to commit but untracked files present (use "git add" to track)
  ```

- 文件加入版本管理

  git add filexxx

  ```shell
   $ git add .
   $ git status
  On branch master
  No commits yet
  Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
          new file:   readme.md
          new file:   test.txt
  ```

- 生成版本

  git commit -m "xxxxxx"

  ```shell
  $ git commit -m "v0.0"
  [master (root-commit) e198374] v0.0
   2 files changed, 31 insertions(+)
   create mode 100644 readme.md
   create mode 100644 test.txt
  ```

  ```shell
  $ git status
  On branch master
  Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
          modified:   readme.md
  no changes added to commit (use "git add" and/or "git commit -a")
  ```

# 三. git 三大区域

![img](images/三大区域.png)

 　上图显示了git中的三大区域：工作区，暂存区，版本库。

　　下面详细说一下两个命令：

```shell
git checkout
git reset HEAD
```

　　1、git checkout

　　当你修改了一个文件（demo.txt）之后，他会自动变红。此时输入命令git checkout - - demo.txt，他就会回到未修改的状态。

　　2、git reset HEAD

　　当你修改一个文件（demo.txt），然后git add之后，他就会变绿，进入暂存区，如果我想让他变红，回到工作区，输入命令git reset HEAD demo.txt 即可