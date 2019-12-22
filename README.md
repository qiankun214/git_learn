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

## Git从远程仓库拉取

```bash
git pull
```

## Git回滚

### Git查看提交记录

```bash
git log -<n>
```

查看n条提交记录，默认为查看所有

### Git回滚版本

```bash
git reset --hard <版本号>
```

版本号通过查看提交记录找到，除了写版本号外，还可以通过`HEAD`表示：

- `HEAD`表示当版本
- `^`表示上一个版本，例如`HEAD^`为当前的上一个版本，`HEAD^^`为当前的上两个版本
- `~n`表示上n个版本，例如`HEAD~10`为当前的上10个版本

## Git撤销未缓存操作（未执行git add）

### 查看工作区修改

```bash
git status
```

### 撤销操作

```

```



# Git分支操作

