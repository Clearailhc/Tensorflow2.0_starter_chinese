# tf2.0_tutorials_practice_chinese
根据仓库tensorflow2_tutorials_chinese(https://github.com/czy36mengfei/tensorflow2_tutorials_chinese
)的练习版本，增加了一些个人实现过程中的理解和爬坑，慢慢更新，欢迎讨论~

## TensorFlow 2.0 实践
### 0. TensorFlow 2.0 安装
个人推荐使用conda安装，省去了分别手动安装CUDA,CUDNN和tf、配置正确版本的繁琐过程，并且conda命令各平台通用。
#### 0.1 安装对应版本的Anaconda
可以选择官网下载或者清华开源镜像站(https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)下载，选择最新的版本下载即可（默认python3.7），下载完成后将清华镜像加入Anaconda Python 免费仓库，打开conda prompt或者terminal运行以下命令:
`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes`
####
### 1. TF中的Keras入门
#### 1.1 - Keras 快速入门