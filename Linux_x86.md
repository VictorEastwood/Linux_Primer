# Linux 初步设置（x86）
---
## 1.安装系统：

## 2.安装必要软件：

::: warning
注意请选择自己电脑架构对应的软件。本篇文档对应的是x86架构。千万不要下载错误的架构软件。一定要下载扩展名为.deb文件。
:::

### 2.1 软件包安装
类似于安卓系统的apk安装方式，Linux系统也有自己的安装方式，那就是.deb文件安装方式。下面是一些常用软件的.deb文件下载地址和安装方式：
| 软件 | 下载地址 |
| --- | --- |
| Chrome | https://www.google.cn/chrome/ |
| VSCode | https://code.visualstudio.com/ |
| QQ | https://im.qq.com/linuxqq/index.shtml |
| 飞书 | https://www.feishu.cn/download |
| 腾讯文档 | https://docs.qq.com/home/download |
| ToDesk | https://www.todesk.com/ |
| 百度网盘 | https://pan.baidu.com/download |

进入上面的链接，下载对应的.deb文件，在.deb文件所在的文件夹下打开终端，输入：
```shell
sudo dpkg -i 文件名.deb
```
即可安装软件。

### 2.2 手动安装
#### 2.2.1 微信Linux原生版本
复制以下命令到终端运行：
```shell
# 下载铜豌豆软件源
sudo wget -c -O atzlinux-v11-archive-keyring_lastest_all.deb https://www.atzlinux.com/atzlinux/pool/main/a/atzlinux-archive-keyring/atzlinux-v12-archive-keyring_lastest_all.deb

# 安装铜豌豆软件源
sudo apt -y install ./atzlinux-v11-archive-keyring_lastest_all.deb

# 使用终端命令行安装微信原生版本
sudo apt update
sudo cp /etc/lsb-release /etc/lsb-release.Ubuntu
sudo apt -y install electronic-wechat-icons-atzlinux
sudo apt -y install com.tencent.wechat
sudo cp /etc/lsb-release /etc/lsb-release.wechat
```
#### 2.2.2 Clash for Windows Linux版
- 确定你的电脑架构是x86_64，然后运行以下命令下载软件包：
```shell
wget https://github.com/clashdownload/Clash_for_Windows/releases/download/0.20.39/Clash.for.Windows-0.20.39-x64-linux.tar.gz
```
如果 wget 下载不了，就把下载链接复制到浏览器下载。
然后找到你下载的安装包，解压提取，打开文件夹，里面有一个 cfw 文件，双击就是 Clash 了。如果不行，请在该文件夹内打开终端，使用./cfw命令执行它。
打开软件到 Profiles 里粘贴你的订阅地址，下载。
把网络代理改成手动，按照如下设置：
- HTTP代理 `127.0.0.1` `7890`
- HTTPS代理 `127.0.0.1` `7890`
- FTP代理 `      ` `0`
- Socks主机(s)`127.0.0.1` `7890`
到浏览器测试YouTube，看看是否可以打开: https://www.youtube.com/

#### 2.2.3 搜狗输入法
1. 更新源
   在终端执行 `sudo apt update`
2. 安装fcitx输入法框架
   在终端输入 `sudo apt install fcitx`
3. 设置fcitx为系统输入法
   点击左下角菜单选择语言支持，将语言选择为fcitx
4. 设置fcitx开机自启动
   在终端执行 `sudo cp /usr/share/applications/fcitx.desktop /etc/xdg/autostart/`
5. 卸载系统ibus输入法框架
   在终端执行 `sudo apt purge ibus`
6. 安装搜狗输入法
   1. 在官网https://shurufa.sogou.com/linux 下载搜狗输入法安装包，并安装，安装命令 `sudo dpkg -i 安装包名`
   2. 安装输入法依赖
      在终端执行：
      ```bash
      sudo apt install libqt5qml5 libqt5quick5 libqt5quickwidgets5 qml-module-qtquick2
      sudo apt install libgsettings-qt1
      ```
7. 重启电脑、调出输入法
   1. 重启电脑
   2. 查看右上角，可以看到“搜狗”字样，在输入窗口即可调出搜狗输入法。
   3. 如果没有“搜狗”字样，选择配置，将搜狗加入输入法列表即可。
---
# 3.安装驱动
## 3.1 NVIDIA显卡驱动
输入以下命令查看驱动支持的最大CUDA版本。
```shell
nvidia-smi
```
这里是12.4(CUDA Version)
```shell
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.120                Driver Version: 550.120        CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3060 ...    Off |   00000000:01:00.0  On |                  N/A |
| N/A   47C    P8             12W /  115W |      58MiB /   6144MiB |     39%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      1753      G   /usr/lib/xorg/Xorg                             53MiB |
+-----------------------------------------------------------------------------------------+
```


