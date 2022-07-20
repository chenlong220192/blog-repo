## 撤销commit
在使用git时，偶尔会发现提交的代码有问题，需要回退到上一个版本。  
这里记录以下两种方法，可以实现撤销相关commit的功能。

### reset  
`git reset` 方式不会留下`commit`记录。不加上`--force`会提示版本落后于远程仓库。
```
git reset --hard <commit_ID>
git push origin <branch_name> --force
```

### revert
`git revert` 方式会留下一个新的`commit`记录，用以记录撤销了什么内容。相当于直接在代码上做修改并重新`commit`。
```
git revert -n <commit_ID>
git commit -m "revert xxx"
```

***
⚠️注意可以通过HEAD来指定回退几个commit
```
# 回退到上一个提交
git reset HEAD^

# 回退最后三次commit
git reset HEAD~3

# 回退到指定的commit
git reset <commit_ID>
```

***

⚠️注意`git reset`三种模式介绍：

根据`–-soft``–-mixed``–-hard`会对working tree和index和HEAD进行重置。

`git reset –-mixed` 此为默认方式，不带任何参数的git reset，即时这种方式，它回退到某个版本，只保留源码，回退commit和index信息。  
`git reset -–soft` 回退到某个版本，只回退了commit的信息，不会恢复到index file一级。如果还要提交，直接commit即可。  
`git reset –-hard` 彻底回退到某个版本，本地的源码也会变为上一个版本的内容。  
