### git add

```
// 监控工作区的状态树，将工作时的所有变化提交到暂存区，包括文件内容修改(modify)和新文件(new)，但不包括被删除的文件。
git add .	
// 仅仅监控已经被add的文件（即tracked file），会将被修改的文件再次提交到暂存区。
git add -u
// 上面两个功能的合集。
git add -A 
```

### git branch

```
// 查看所有分支
git branch 
//  创建新分支
git branch <name>
// 切换分支
git switch <branch name> || git cheackout <branch name>
```

#### git remote

```
// 将本地库链接到远程仓库
git remote add <address of origin>
// 查看本地仓库链接的远程仓库
git remote
```

#### git push

```
// 初次推送
git push -u origin < master >
// 再次推送
git push origin < master >
```





