# 安装Tensorflow
**请注意**，这个安装Tensorflow是指在ubuntu下面安装，我们不选择在windows下面安装，是因为版本的问题。
1. Tensorflow 在windows下面只**支持py3**</br>
2. SyntaxNet 目前只**支持py2**</br>

真的不知道Google，当初怎么想的。 不同的系统下面，有着不同的版本，还都不兼容。</br>

我们在这里介绍如何用**pip**安装**ubuntu**系统上的tensorflow，因为这是一种我们认为相对比较简单快捷的途径。如果需要了解怎样用Docker或virtualenv (virtual environment)来安装，可以参考tensorflow的官方网站 tensorflow.org 。</br>

一般可以先尝试官方安装说明的指令pip install tensorflow,
但如果报错，说明相关环境不满足条件，可以参考下面我们经过的步骤。</br>

### 安装pip和相关工具
---
首先，需要为Ubuntu安装pip，在终端里指令：
> sudo apt-get install python-pip python-dev

注意这是属于Ubuntu的command。</br>

### 升级pip
---
有了pip，需要为Ubuntu升级pip，经过我们的尝试，各种tutorials上面提及的方法并没有都成功。</br>
1. 最先用
> sudo pip install --upgrade pip

报错。</br>

2. 依照官网 tensorflow.org，

> sudo pip install -U pip

也不行。</br>


3. 于是，我们选择从pip官网下载最新可用的pip，即从 pypi.python.org/pypi/pip 下载，注意选择与电脑系统和python版本相应的pip。例如，我们选择的是python2.7可用的9.0.1版本pip。</br>


4. 下载之后，安装：
>sudo -H pip install pip-9.0.1-py2.py3-none-any.whl

之后显示usccessfully installed, 安装pip 9.0.1版本成功。</br>


### 用pip装wheel：
---
已下载的pip和最终需要安装的tensorflow都以whl形式出现。我们面对的下一个问题是whl的upgrade，只需要很简单的一步：
> pip install wheel

有了这一步的基础，我们就可以顺利install xxx.whl后缀的已下载内容了，即
> pip install xxxxx.whl

</br>

### 安装tensorflow
---
然后通过 googleapis.com 上找到与自己系统和python版本相匹配的whl形式tensorflow安装文件。</br>

例如，我们的Ubuntu系统有python2.7版本，相对应的安装指令为：
>   sudo -H pip install --upgrade \       https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.0-cp27-none-linux_x86_64.whl

然后就成功了，写成其他的cp（py3.x）版本都不行，因为电脑是python2.7，尝试了cp27-cp27m也不行，只有cp27-none可以，系统也不能写错，不然都出现“xxx is not a supported wheel on this platform.”
#### 找符合环境的安装url
根据操作系统，python版本，和cpu/gpu支持，确定您需要的URL：
例如:

python 2.7 + cpu:
https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp27-none-linux_x86_64.whl

python 2.7 + gpu
https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.2.1-cp27-none-linux_x86_64.whl

python 3.4 + cpu
https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp34-cp34m-linux_x86_64.whl

python 3.4 + gpu
https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.2.1-cp34-cp34m-linux_x86_64.whl

python 3.5 + cpu
https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp35-cp35m-linux_x86_64.whl

python 3.5 + gpu
https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.2.1-cp35-cp35m-linux_x86_64.whl

python 3.6 + cpu
https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp36-cp36m-linux_x86_64.whl

python 3.6 + gpu
https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.2.1-cp36-cp36m-linux_x86_64.whl

**如果以上列举的都不符合您的环境**，要寻找符合系统和python版本的tensorflow URL, 可以到
https://www.tensorflow.org/install/install_linux#the_url_of_the_tensorflow_python_package
直接跳到 “The URL of the TensorFlow Python package” 章节。</br>

### 初步检测tensorflow是否安装成功

参照官网 tensorflow.org 例子，在完成安装步骤之后，可以按以下步骤尝试第一个tensorflow小短程序：
1. 打开终端，输入python
>     import tensorflow as tf
>     hello = tf.constant('Hello, TensorFlow!')
>     sess = tf.Session()
>     print(sess.run(hello))

2. 如果输出
>     Hello, TensorFlow!
那么安装成功，可以开始使用tensorflow。

### 测试警报

如果在测试安装是否成功的过程当中，报如下警报，你可以选择忽略，或者修正如下错误：</br>
我的tensorflow在安装的时候采用的pip install指令，这种安装方式会存在这种问题。主要有两种解决方法，一种是修改警告信息的显示级别，使这种信息不再出现，另外一种就是自己重新编译安装ｔｅｎｓｏｒｆｌｏｗ，在编译的时候使用这些指令集。这里我尝试第二种解决方法。并且由于我的机器上没有高效的ＧＰＵ，所以我尝试安装的是CPU版本。
```
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE3 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions, but these are available on your machine and could speed up CPU computations.
W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use FMA instructions, but these are available on your machine and could speed up CPU computations.<span style="white-space:pre">
```

1. 卸载原来安装的tensorflow:
```
sudo pip uninstall tensorflow  
```
或者：
```
sudo -H pip uninstall tensorflow  
```
2. 克隆Tensorflow仓库：
```
git clone https://github.com/tensorflow/tensorflow 
```
3. 基于你的需求来添加编译参数：
```
bazel build -c opt --copt=-msse3 --copt=-msse4.1 --copt=-msse4.2 --copt=-mavx --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package
```
4. 打包：
```
bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg  
```
5. 安装：
需要说明的是，由于平台的不同，可能软件包的名字是不一样的。
```
sudo pip install /tmp/tensorflow_pkg/tensorflow-1.1.0rc1-cp27-cp27mu-linux_x86_64.whl  
```
或者：
```
sudo -H pip install /tmp/tensorflow_pkg/tensorflow-1.1.0rc1-cp27-cp27mu-linux_x86_64.whl  
```
