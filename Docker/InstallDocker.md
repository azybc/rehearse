# 在 Ubuntu 中安装 Docker

## 检查 Docker 旧版本

```shell
$ sudo apt remover docker docker-engine docker.io containerd runc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package docker-engin
```

## 使用资源库 (repository) 安装 Docker

### 1\. 预先安装必要的软件

```shell
$ sudo apt update

$ sudo apt install \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common
```

### 2\. 加入 Docker 官方 GPG 密钥

```shell
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
 # 验证 Docker 的 GPG 密钥，看其后8位
$ sudo apt-key fingerprint 0ebfcd88
 # 或使用如下命令，列表中找 docker 的邮件地址
$ sudo apt-key list
```

### 3\. 将 Docker 稳定版 (stable) 添加到本机 apt 库

```shell
$ sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

### 4\. 安装 Doker 稳定版

```shell
$ sudo apt update
$ sudo apt install docker-ce docker-ce-cli containerd.io
```

### 5\. 附加： 查看可装 Docker 的版本

```
$ sudo apt-cache madison docker-ce
```

## 测试 Docker 是否安装成功

先别着急用网上所说的命令 `$ sudo docker run hello-world` 命令测试， 一般 Ubuntu 安装后都会关闭 root 账户， 但打开了安装用户的 sudo 权限。 若现在使用 sudo 权限运行测试， 之后就只能用 sudo 权限运行 Docker 命令。 若参考不使用 sudo 权限的设置， 加入 docker 组的方法， 由于这里运行过测试， 可能会遇到问题。

故先将当前用户加入到 docker 组用户里。

```shell
$ cat /etc/group | grep 'docker'            #查看是否已存在 docker 组
$ sudo usermod -aG docker $USER             #将当前用户加入到 docker 组中
$ id -a                                     #查看自己是否在 docker 组中
```

一般上步最后的命令，你会发现你没在 docker 组中， 这是你没登录出再登入的缘故， 若是桌面版， 你需要重启动登录进来。 可用上面第一个命令， 会看到你的用户名在 docker 组里。 这里有个暂不重启动的方法， 只满足测试， 最终仍需要重启。

```shell
$ newgrp docker             # 注意， 这里你进入了一个新的 shell 里
$ docker run hello-world    # 测试是否 docker 被正确安装
```

