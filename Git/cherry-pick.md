将指定的提交（commit）应用于其他分支。

```bash
git cherry-pick <commitHash>
```
将指定的提交commitHash，应用于当前分支。这会在当前分支产生一个新的提交，当然它们的哈希值会不一样。

举例来说，代码仓库有master和feature两个分支。

```
a - b - c - d   Master
     \
       e - f - g Feature
```
现在将提交f应用到master分支。

```bash
# 切换到 master 分支
git checkout master

# Cherry pick 操作
git cherry-pick f
```

上面的操作完成以后，代码库就变成了下面的样子。

```
a - b - c - d - f   Master
     \
       e - f - g Feature
```
从上面可以看到，master分支的末尾增加了一个提交f。

git cherry-pick命令的参数，分支名也是可以的，表示转移该分支的最新提交。

```bash
git cherry-pick feature
```
上面代码表示将feature分支的最近一次提交，转移到当前分支。

## 多个提交

将 A 和 B 两个提交应用到当前分支。这会在当前分支生成两个对应的新提交。

```bash
git cherry-pick <HashA> <HashB>
```

转移一系列的连续提交。转移从 A 到 B 的所有提交。它们必须按照正确的顺序放置：提交 A 必须早于提交 B，否则命令将失败，但不会报错。

```bash
git cherry-pick A..B 
```

注意：提交 A 将不会包含在 cherry pick 中。

如果要包含提交 A，使用以下命令：

```bash
git cherry-pick A^..B 
```

