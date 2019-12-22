[TOC]

# Git仓库基本操作

## Git仓库建立

### 本地仓库建立

```bash
git init
```

### 远程仓库建立（空仓库）

```bash
git init --bare <name>.git
```

## 链接远程仓库

```bash
git remote add origin <远程仓库路径>/<远程仓库名称>.git
```

其中`origin`为远程仓库的“别名”，可以修改，若要修改则将后续所有`origin`都进行修改

## Git提交

### 本地提交

```bash
git add <提交的文件>
git commit -m "<提交说明>"
```

`<提交的文件>`可以使用`*`表示该文件夹下所有，还可以使用`.gitignore`文件指示忽略那些文件

### 推到远程仓库

```bash
git push origin <分支名称>
```

