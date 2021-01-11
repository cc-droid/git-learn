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

# 四. 版本回退

当前状态

```shell
$ git log
commit bfc113f6790f6e7e730a679c44912ccaaca02ffc (HEAD -> master)
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:40:08 2021 +0800

    v0.2 version 0.2

commit ecb18e4b4bb3b4108a86c52d4708e0dc083417db
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:39:00 2021 +0800

    v0.1 version0.1

commit 1d2519296736004848b728f56563b40ecd7caeea
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:33:06 2021 +0800

    v0.0rc2 git三大区域

commit 16f005fa2931f677238b909ab7b0795def404050
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:04:28 2021 +0800

    v0.0r1 version init and add md doc

commit e198374300602fde86ae0c218f992e4e9f79c82e
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 13:49:33 2021 +0800

    v0.0
```

回退到 v0.1

```shell
$ git reset --hard ecb18e4b4bb3b4108a86c52d4708e0dc083417db
HEAD is now at ecb18e4 v0.1 version0.1

$ git log
commit ecb18e4b4bb3b4108a86c52d4708e0dc083417db (HEAD -> master)
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:39:00 2021 +0800

    v0.1 version0.1

commit 1d2519296736004848b728f56563b40ecd7caeea
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:33:06 2021 +0800

    v0.0rc2 git三大区域

commit 16f005fa2931f677238b909ab7b0795def404050
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:04:28 2021 +0800

    v0.0r1 version init and add md doc

commit e198374300602fde86ae0c218f992e4e9f79c82e
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 13:49:33 2021 +0800

    v0.0

```

回退到v0.2

```shell
$ git reflog
ecb18e4 (HEAD -> master) HEAD@{0}: reset: moving to ecb18e4b4bb3b4108a86c52d4708e0dc083417db
bfc113f HEAD@{1}: reset: moving to HEAD
bfc113f HEAD@{2}: reset: moving to HEAD
bfc113f HEAD@{3}: commit: v0.2 version 0.2
ecb18e4 (HEAD -> master) HEAD@{4}: commit: v0.1 version0.1
1d25192 HEAD@{5}: commit: v0.0rc2 git三大区域
16f005f HEAD@{6}: commit: v0.0r1 version init and add md doc
e198374 HEAD@{7}: commit (initial): v0.0
```

```shell
$ git reset --hard bfc113f
HEAD is now at bfc113f v0.2 version 0.2
```

```shell
$ git log
commit bfc113f6790f6e7e730a679c44912ccaaca02ffc (HEAD -> master)
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:40:08 2021 +0800

    v0.2 version 0.2

commit ecb18e4b4bb3b4108a86c52d4708e0dc083417db
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:39:00 2021 +0800

    v0.1 version0.1

commit 1d2519296736004848b728f56563b40ecd7caeea
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:33:06 2021 +0800

    v0.0rc2 git三大区域

commit 16f005fa2931f677238b909ab7b0795def404050
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 14:04:28 2021 +0800

    v0.0r1 version init and add md doc

commit e198374300602fde86ae0c218f992e4e9f79c82e
Author: ccdroid <hongchunbo@hotmail.com>
Date:   Mon Jan 11 13:49:33 2021 +0800

    v0.0
```

