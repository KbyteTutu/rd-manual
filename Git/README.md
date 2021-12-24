<font face="黑体" color=green size=5>常用命令</font>

##### 新建tag
`git tag <tag_name>`

##### 删除tag
`git tag -d <tag_name>`

##### 推送tag
`git push --tags`

##### 控制台命令行设置为彩色输出
`git config color.ui true`

<font face="黑体" color=yellow size=5>不常用命令</font>
##### 修改提交记录:
```bash
git rebase -i HEAD~1
git commit --amend
git rebase --continue
三条命令组合使用
```

##### 修改提交用户名和邮箱
```bash
git filter-branch --env-filter '
OLD_EMAIL="miaoyongchao@xx.com" 
CORRECT_NAME="miaoyc"
CORRECT_EMAIL="miaoyongchao@xx.com"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
export GIT_COMMITTER_NAME="$CORRECT_NAME"
export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
export GIT_AUTHOR_NAME="$CORRECT_NAME"
export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' -f --tag-name-filter cat -- --branches --tags
```

##### 拷贝git项目到新库步骤
1. git clone --bare git@github.com:miaoyc666/rd-manual.git
2. 新建新的git库，空白库：git@github.com:miaoyc666/rd-manual_new.git
3. cd rd-manual.git
4. git push --mirror git@github.com:miaoyc666/rd-manual_new.git

##### 切换git库的两个方法
1. 重新git clone项目；
2. 修改.git/config文件，将git@github.com:miaoyc666/rd-manual.git替换为git@github.com:miaoyc666/rd-manual_new.git


<font face="黑体" color=red size=5>尽量不要使用的命令</font>
##### 强行推送tag到远端
`git push --force`
