# ssh免密账户目录设置
sshd为了安全对属主的目录和文件权限有所要求，如果权限不对，则ssh的免密码登陆不生效。

#### 目录权限
- 用户目录权限为755或者700，就是不能是77x
- .ssh目录权限一般为755或者700
- rsa_id.pub及authorized_keys权限一般为644
- rsa_id权限必须为600

#### 相关命令
```bash
mkdir .ssh
chmod 700 .ssh
# 导入authorized_keys, 可在服务器使用rz或scp

#以上三步可简化为
ssh-copy-id {$username}@{$hostname}

vim ~/.ssh/config
```

修改`~/.ssh/config`用于更新ssh服务器配置信息，示例如下：
```config
Host test
    HostName 1.2.3.4
    Port 1234
    User test
```

