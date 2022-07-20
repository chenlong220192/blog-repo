- `git clean -df`只删除所有untracked的文件，如果文件已经被tracked, 修改过的文件不会被回退。
- `git reset --hard`把tracked的文件回撤到前一个版本，对于untracked的文件(比如编译的临时文件)都不会被删除。