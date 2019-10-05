## 第二部分 Linux档案、目录与磁碟格式
### Linux档案权限与目录配置
|1|2|3|
|---|---|---|
|档案拥有者|群组|其他人|
> 档案属性

|10位|inode|用户|群组|容量bytes|建档日期|档名|
|----|---|----|---|---|-----|---|
|档案类型权限|连接数|拥有者|所属群组|档案容量|修改日期|档名|
用途：
- 系统保护
- 团队开发软件或资料共用
- 设定恰当的权限
>change group/owner/modify?
chgrp/chown/chmod

rwx对于文件和目录
- read/write/execute
- read contents/modify contents/access directory
档案种类：
- regular file
- directory
- link
- device
- sockets
- pipe,FIFO
#### Linux目录配置
**FHS**
- /(root)
- /usr(unix software resource)
- /var(variable)
absolute/relative path
### Linux档案与目录管理

## 第四部分 Linux使用者管理
### Linux账号管理与ACL权限控制
#### UID与GID
- /etc/passwd
- /etc/shadow 
- /etc/group
#### 有效群组(effective group)与初始群组(initial group)
1. groups 有效与支援群组的观察
2. newgrp 有效群组的更换
3. 
