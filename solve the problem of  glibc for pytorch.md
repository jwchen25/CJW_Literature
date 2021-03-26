# 解决pytorch (torch) glibc 2.17 依赖问题
*2021-3-26 By Junwu Chen at CAS IPE, Beijing*
  
  pytorch是常用的深度学习的python库，但在linux系统上安装时，会需要满足`glibc >= v2.17`的条件才能正常使用。这对许多linux系统版本较老且没有root权限的小伙伴们来说是一个很头疼的问题。我之前也在网上找了很多的解决方法，大部分都是通过在用户文件夹下自行编译高版本的glibc，然后通过设置环境变量或动态库路径来绕过本地的低版本的glibc。但是这些方法都比较麻烦，而且经常会遇到意想不到的错误。所以今天想给大家推荐一下自己尝试成功的conda安装pytorch的方法。  

![pytorch官网介绍](https://img-blog.csdnimg.cn/20210326095321796.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjgwNzA2NQ==,size_16,color_FFFFFF,t_70)
### 1. 创建conda虚拟环境
```
conda create -n pytorch python=3.6  # 创建名字为pytorch的虚拟环境（python版本为3.6）
conda activate pytorch  # 激活虚拟环境
```
### 2. conda安装pytorch
```
# conda安装pytorch(cpu版)
conda install pytorch torchvision torchaudio cpuonly -c pytorch
# conda安装先前版本的pytorch
conda install pytorch==1.6.0 torchvision==0.7.0 cpuonly -c pytorch
```
具体的conda安装命令请见pytorch官网：[最新版本](https://pytorch.org/get-started/locally/)；[先前版本](https://pytorch.org/get-started/previous-versions/)
### 3. 检测是否安装成功
```
python -c "import torch; print(torch.__version__)"
```
### 附1
查看当前系统glibc方法：`ldd --version`

