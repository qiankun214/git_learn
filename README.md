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

## Git撤销操作

### 查看修改

```bash
git status
```

### 撤销操作（未执行git add）

```bash
git checkout -- <文件名>
```

该操作将指定文件恢复到上一次`git add`或`git commit`时的状态

### 撤销操作（已执行git add）

```bash
git reset HEAD <文件名>   	//将操作放回工作区
git checkout -- <文件名>   //撤销操作
```

这两条操作将指定文件恢复到上一次`git commit`时的状态

# Git分支操作

## 创建分支

```bash
git checkout -b <分支名称>	//旧版本，仍可使用
git switch -c   <分支名称>	//新版本
```

该命令表示创建指定名称的分支并转向该分支，相当于以下两条指令

```bash
git branch dev		//创建分支
git checkout dev	//转向分支
```

## 转向分支

### 查看分支状态

```bash
git branch
```

列出所有分支名称，在当前分之前有`*`

### 转向分支

```bash
git checkout <分支名称>   //旧版本，仍可使用
git switch <分支名称>	  //新版本
```

转向分支后会将仓库修改为对应分支的情况，例如在修改一个分支提交后转向另一个分支，修改消失

## 合并分支

### 快速合并模式（无合并记录）

```bash
git merge <分支名称>
```

合并指定分支到当前分支，对于`master`-`dev`分支对，需要首先回到`master`分支才能操作

### 非快速合并模式（有合并记录）

```bash
git merge --no-ff -m "<提交记录>" <分支名称>
```

此种方式合并分支到一个新提交中，有提交记录

## 远程仓库

### 推送分支到远程仓库

```bash
git push origin <分支名称>
```

### 拉取远程分支

```bash
git checkout -b dev origin/<分支名称>
```

该方式为从远程仓库中创建分支，已有分支后，直接在该分支下执行`git pull`即可

### 链接远程分支

```bash
git branch --set-upstream-to=origin/<远程分支名称> <本地分支名称>
```

当进行`git pull`拉取分支失败提示需要链接时使用

## 复制提交

```bash
git cherry-pick <commit id>
```

将指定id的提交复制到当前分支

## 删除分支

```bash
git branch -d <branch名称> 	//删除分支
git branch -D <branch名称> 	//强行删除分支
```

