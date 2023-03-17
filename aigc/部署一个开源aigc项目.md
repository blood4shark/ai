# stable-diffusion-webui

目标: 部署起来看到图片验证效果

条件: 个人笔记本电脑(14c32g 200g-ssd 3070ti)

要求: 时间有限





策略:

​	与官方文档的操作指南、环境保持一致

问题:

​	无法通过官方文档复现部署

​		官方文档只是提供了核心的部署操作指令







购买 香港、gpu、按量付费、带公网 的服务器、选择debian 10系统



不一样的地方, 作者环境是个人电脑, 所以用户为非root, 这里希望能改成root

​	使用root之后, 安装包可以不用输入密码



操作指令

```
sudo apt update -y
sudo apt install -y wget git python3 python3-venv
bash <(wget -qO- https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh)


wget https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh

bash /root/webui.sh

mkdir -p /home/root && chmod 777 /home/root
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd /home/root/stable-diffusion-webui
pip install -r requirements.txt
pip install -r requirements_versions.txt
vi webui.sh
	can_run_as_root=0  -> can_run_as_root=1

```



是否需要安装nvidia驱动?

安装nvdia gpu驱动

```
sudo vim /etc/apt/sources.list
deb http://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free

deb http://security.debian.org/debian-security bullseye-security main contrib non-free
deb-src http://security.debian.org/debian-security bullseye-security main contrib non-free

deb http://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free

sudo apt update -y && sudo apt install -y nvidia-detect
nvidia-detect
sudo apt install -y nvidia-driver
```



# python项目

## 配置加速器

### linux

```
$HOME/.config/pip/pip.conf

[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple12
```

### windows

```
%APPDATA%\pip\pip.ini

[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```



# 在本地电脑上运行项目

安装python 3.10.6 ( https://www.python.org/downloads/release/python-3106/ )

​	





安装Anaconda

​	下载安装 https://www.anaconda.com/products/distribution/start-coding-immediately

配置加速器

```
conda config --set show_channel_urls yes

# 修改文件
%APPDATA%/.condarc


channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud

conda clean -i
```



# 在服务器上运行项目

通过vagrant创建一个带gpu的debian虚拟机

配置debian国内加速源

安装gpu驱动

配置python-pip加速源

准备项目文件、下载依赖(耗时长)





# 参考文档

https://www.tjsky.net/tutorial/457

https://zhuanlan.zhihu.com/p/591620617
