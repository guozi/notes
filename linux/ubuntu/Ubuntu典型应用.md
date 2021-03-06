# 常用方式

[TOC]

## 1. 常见安装

### 1.1. 添加root

```sh
sudo passwd root
```

### 1.2. 开启ssh

```sh
sudo apt-get install openssh-server
```

```sh
sudo vi /etc/ssh/sshd_config
```

```text
PermitRootLogin yes
```

### 1.3. 支持exfat

```sh
sudo apt-get install exfat-fuse
```

### 1.4. 安装五笔输入法

桌面右上角下拉箭头 -> Settings -> Region & Language

### 1.5. 字体

```sh
sudo apt-get install ttf-mscorefonts-installer
# 更新字体缓存
sudo fc-cache -f -v
```

### 1.6. 笔记本模式工具

如果不安装，部分环境关机的时候会变成重启

```sh
sudo apt install laptop-mode-tools
```

### 1.7. 系统配置

安装 ```Unity Tweak Tool```

### 1.8. Chrome

ppa如果已经安装，可不用再次安装

```sh
sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt-get install chromium-browser
```

### 1.9. wps

#### 1.9.1. 安装缺失字体

- 下载缺失的字体文件

国外下载地址：https://www.dropbox.com/s/lfy4hvq95ilwyw5/wps_symbol_fonts.zip

国内下载地址：https://pan.baidu.com/s/1eS6xIzo

- 解压并复制到Linux系统中的/usr/share/fonts文件夹中。

- 执行以下命令

```sh
# 生成字体的索引信息
sudo mkfontscale
sudo mkfontdir
# 运行fc-cache命令更新字体缓存。
sudo fc-cache
```

#### 1.9.2. libpng12-0

进入https://packages.ubuntu.com搜索

或
https://packages.debian.org/zh-cn/wheezy/amd64/libpng12-0/download

选择ftp.cn.debian.org/debian进行下载

下载完后安装

#### 1.9.3. wps

http://community.wps.cn/download/
http://kdl1.cache.wps.com/ksodl/download/linux/a21//wps-office_10.1.0.5707~a21_amd64.deb

下载完后安装


### 1.10. eclipse

配置图标在启动栏

```sh
sudo vi /usr/share/applications/eclipse.desktop
```

```ini
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse
Exec=/usr/local/eclipse/eclipse-jee-oxygen-2/eclipse
Icon=/usr/local/eclipse/eclipse-jee-oxygen-2/icon.xpm
Terminal=false
StartupNotify=true
Type=Application
Categories=Application;Development;
```

```sh
sudo chmod u+x /usr/share/applications/eclipse.desktop
```

### 1.11. meld

```sh
sudo apt-get install meld
```

### 1.12. wireshark

ppa如果已经安装，可不用再次安装

```sh
sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt install wireshark
```

## 2. 常见配置

### 2.1. apt国内镜像

- 查看当前系统的Codename

```sh
lsb_release -a
```

- 搜索相应Codename的国内镜像

- 修改镜像文件

```sh
vi /etc/apt/sources.list
```

### 2.2. 配置文件的默认打开方式

 ```鼠标右击文件``` > ```Properpies``` > ```Open with```

## 3. 常见卸载

### 3.1. 卸载多余内核

- 查看当前核心

```sh
uname -a
```

- 查询系统中装了多少内核

```sh
dpkg --get-selections|grep linux
```

- 删除内核

```sh
sudo apt-get remove linux-image-*.*.*-**（*号用你想删除的实际情况改写）
sudo apt-get remove linux-headers-*.*.*-**（*号用你想删除的实际情况改写）
```

- 再次查看

```sh
dpkg --get-selections|grep linux
```

查看内核是否都删除干净了。没干净继续删除。有的内核后面会显示是deinstall 那需要通过

```sh
dpkg --get-selections | grep deinstall | sed 's/deinstall/\lpurge/' | sudo dpkg --set-selections; sudo dpkg -Pa
```

## 4. 常见快捷键

### 4.1. 资源管理器

Ctrl + H 显示/隐藏<隐藏文件>
Ctrl + L 调出地址栏
