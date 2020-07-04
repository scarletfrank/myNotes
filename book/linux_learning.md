# Linux Learning

> WSL: sudo su

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

## 第三部分 学习Shell与Shell scripts

### 正则化表示法与文件格式处理

#### 知识

```
vi, grep, awk, sed # RE
cp, ls # wildcard
```
BASH中的万用字元和正则表示法中的星星号不同，后者为组合形态
.*代表零个或多个任意字元

开头、结尾、取反，下面一个例子是去除空白行和注释行

```
grep -v '^$' /etc/nginx/nginx.conf | grep -v '^#'
```
#### 工具

awk, sed

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

### 例行性工作排程

> 突发性(at)和例行性(crontab)

```
# WSL
sudo service cron start
sudo /etc/init.d/cron restart
```

- batch, 考虑工作负载的工作调度
- anacron，处理非24小时一直启动的Linux系统的crontab的执行。

### 软件安装

```
file /bin/bash
```

#### Build from source

configure(建立makefile)+make

.c compile .o assemble .out

```bash
//CFLAGS
-c compile and not assemble
-Wall detailed message
-O optimization
-o output
//LIBS
-lm libm.so or libm.a
// after cd
make linux test
sudo make install
make clean
```

动态和静态函数库

```bash
ldd/ldconfig
```

#### Install from binary 

```bash
tar -C /usr/local/ -xzf xx.tar.gz
vi ~/.bashrc
export PATH=$PATH:/usr/local/xx/bin
```

#### Verify

```bash
sha1sum
md5sum
sha256sum
```

#### 软件管理器

> 用Ubuntu为主，主要用DPKG，在线升级机制APT

### 程序管理

```bash
jobs -l
fg
bg
kill
ps -l(A) #自己bash程序
ps aux #所有系统运行的程序
```

