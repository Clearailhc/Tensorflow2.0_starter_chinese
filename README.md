# tf2.0_tutorials_practice_chinese
根据仓库tensorflow2_tutorials_chinese(https://github.com/czy36mengfei/tensorflow2_tutorials_chinese
)的练习版本，增加了一些个人实现过程中的理解和爬坑，慢慢更新，欢迎讨论~

## TensorFlow 2.0 实践
### 0. TensorFlow 2.0-gpu 安装
个人推荐使用conda安装，省去了分别手动安装CUDA,CUDNN和tf、配置正确版本的繁琐过程，并且conda命令各平台通用。
#### 0.1. 安装对应版本的Anaconda
可以选择官网下载或者清华开源镜像站 (https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/) 下载，选择最新的版本下载即可（默认python3.7），下载完成后将清华镜像加入Anaconda Python 免费仓库，打开conda prompt或者terminal运行以下命令:

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

#### 0.2. 新建环境并安装Tensorflow 2.0

使用conda最大的好处是可以创建相对独立的环境，哪怕某个环境崩了也不会影响其它，同样在conda prompt或者terminal运行以下命令：

```
conda create -n your_env_name python=3.7
```

将your_env_name替换为您想要的环境名（如tf2），后面的python版本可选，若省略则默认和你的anaconda基础python同一版本。

创建完成后运行：

```
conda activate your_env_name
```

激活该独立环境，此时命令行前会显示当前环境名，之后的操作默认都在新的环境中进行。

下面将使用conda安装Tensorflow 2.0，因为此时conda库中并无tf 2.0的包(仅可以通过pip安装)，可以采用曲线救国策略先安装`Tensorflow 1.13.1`（cuda和cudnn版本与tf 2.0相同），运行如下命令：

```
conda install tensorflow-gpu==1.13.1
```

之后会提示安装相关的包，按 `y` 继续，等待安装完成。

然后偷梁换柱卸载掉tf 1.13，使用pip安装tf 2.0：

```
pip uninstall tensorflow-gpu
pip install tensorflow-gpu==2.0.0b1 -i https://pypi.tuna.tsinghua.edu.cn/simple
```

至此就在该环境中安装完了Tensorflow 2.0-gpu。

#### 0.3. Jupyter lab多kernel配置

此时可以通过三种方式使用该环境：

1. 在conda prompt或者terminal中激活该环境后，直接输入*python*进入python。
2. 使用pycharm、spyder等IDE，手动切换环境路径为“%Anaconda安装目录/envs/your_env_name”
3. 使用Jupyter Lab（notebook升级版）配置多多环境kernel

因为本项目为基于Jupyter的项目，着重讲一下第三种方式：

- 先激活tf2.0所在的环境，使用`conda install ipykernel`安装*ipykernel*.
- 使用`conda deactivate`回到base环境，使用`conda install nb_conda` 安装*nb_conda*.
- 新建一个conda prompt或者terminal，输入`jupyter lab`运行juyter lab，此时可以看到多个环境的kernel。

jupyter lab的其它用法可以通过别的学习资料了解，至此已经完成了Tensorflow 2.0的安装和运行环境配置，如有问题欢迎提问~

### 1. TF中的Keras入门
#### 1.1 - Keras 快速入门