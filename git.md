***

***把文件添加到暂存区***

`git add filename `

`git checkout //撤销对工作区的修改 用版本库里最新的替换工作区文件`



***把文件提交到当前分支***

`git commit  -m ""`

`git reset HEAD /撤销`

***查看工作区和暂存区区别***

`git diff`

`git diff --cached //查看暂存区和版本库的区别`



查看工作区状态

`git status`

***查看日志***

`git log`

---

HEAD表示当前的版本

HEAD^上个版本

***回退版本***

`git reset  --hard HEAD^`

`git checkout //在工作区回退 都是撤回到和版本库最新的版本`

`git reset HEAD <filename> //在暂存区回退都是撤回到和版本库最新的版本`

***删除文件***‘

`git rm filename`

`git commit -m ""`

***推送到远程仓库***

`git push oringin master`

***pull到本地***

`git pull origin master`









***记录命令&&回退版本***

`git reflog`

***

.git:git的版本库

