# 一.版本初始化

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

  ```
  $ git status
  On branch master
  Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
          modified:   readme.md
  no changes added to commit (use "git add" and/or "git commit -a")
  ```