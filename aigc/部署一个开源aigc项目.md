# stable-diffusion-webui

https://github.com/AUTOMATIC1111/stable-diffusion-webui

目标: 部署起来看到图片验证效果

条件: 个人笔记本电脑(14c32g 200g-ssd 3070ti)

要求: 时间有限



# python

## 配置加速器

### linux

```
$HOME/.config/pip/pip.conf

[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple12
```



# 在本地电脑上运行项目(windows)

## 安装python

安装python 3.10.6 ( https://www.python.org/downloads/release/python-3106/ )

配置加速器(会导致部分包无法下载)

```
%APPDATA%\pip\pip.ini

[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

## 安装cuda

安装nvdia驱动 或者 cuda

### 直接安装cuda(方式一)

查看支持的cuda最高版本

```
nvidia-smi
```

安装cuda 12.1

​	https://developer.nvidia.com/cuda-toolkit-archive

​	https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=11&target_type=exe_local

### 直接安装nvdia 图形显卡驱动(方式二)



## 安装anaconda

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

如何清理

​	删除 `C:\Users\86176\anaconda3\envs\stable-diffusion-webui` 这个目录就可以了



## 运行

### 升级pip

```
D:\projects\github\AUTOMATIC1111\stable-diffusion-webui\venv\Scripts\python.exe -m pip install --upgrade pip
```

### 针对git仓库检出问题

#### 修改git代理地址

```
git config --global http.https://github.com.proxy http://127.0.0.1:53493
git config --global https.https://github.com.proxy https://127.0.0.1:53493
```

#### 修改github.com为国内地址

检出项目可能会失败

​	修改`launch.py`中的 `https://github.com` 为 `https://github.moeyy.xyz`

### 依赖包

部分包安装成功之后仍然会影响安装结果为失败时通过重启电脑解决

### 运行

```
./webui-user.bat
```



# 在服务器上运行项目

通过vagrant创建一个带gpu的debian虚拟机

配置debian国内加速源

安装gpu驱动

配置python-pip加速源

准备项目文件、下载依赖(耗时长)



# 接下来的动作

看官方文档: https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features

能够在服务器上跑起来

了解原理



研究如何产生技术价值(工具、社区)

研究如何产生商业价值(交易)









# 参考文档

https://www.tjsky.net/tutorial/457

https://zhuanlan.zhihu.com/p/591620617
