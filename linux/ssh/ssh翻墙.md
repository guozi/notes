# ssh翻墙

## 1. 配置浏览器代理

略

## 2. ssh命令

```sh
ssh -fNTD 12345 root@<翻墙服务器的IP>
```

SSH会建立一个socket，去监听本地的12345端口。一旦有数据传向那个端口，就自动把它转移到SSH连接上面，发往远程主机。

**参数解释**

- D 转发socket请求
- N 表示只连接远程主机，不打开远程shell
- T 表示不为这个连接分配TTY。T和N这个两个参数可以放在一起用，代表这个SSH连接只用来传数据，不执行远程操作。
- f 表示SSH连接成功后，转入后台运行。这样一来，你就可以在不中断SSH连接的情况下，在本地shell中执行其他操作。

## 3. 附杀掉进程的方法

```sh
netstat -Plant | grep <remote port>
```