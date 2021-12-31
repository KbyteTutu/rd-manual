常用命令
======

##### 新建tag
`git tag <tag_name>`

##### 删除tag
`git tag -d <tag_name>`

##### 推送tag
`git push --tags`

##### 控制台命令行设置为彩色输出
`git config color.ui true`

不常用命令
======

##### 回滚到指定版本
```bash
git reset --hard {commit_id}
git push --force    # 慎重使用
```

##### 修改提交记录:
```bash
git rebase -i HEAD~3        # 3此处为可变，数值表示需要修改的最近几条提交的数量
git commit --amend 
git rebase --continue
三条语句组合使用
例如修改最后一条提交记录的时间
1.git rebase -i HEAD~1, 输入完命令后在弹出框内选择commit, 修改commit前的标识为edit
2.git commit --amend
3.GIT_COMMITTER_DATE="2021-12-26T23:01:07" git commit --amend --date="2021-12-26T23:01:07"
4.git rebase --continue
5.git push  --force        # 不推荐使用的命令
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

尽量不要使用的命令
======
##### 强行推送tag到远端
`git push --force`
