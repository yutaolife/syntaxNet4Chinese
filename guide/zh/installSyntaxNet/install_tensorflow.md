# 安装Tensorflow
**请注意**，这个安装Tensorflow是指在ubuntu下面安装，我们不选择在windows下面安装，是因为版本的问题。
1. Tensorflow 在windows下面只**支持py3**</br>
2. SyntaxNet 目前只**支持py2**</br>

真的不知道Google，当初怎么想的。 不同的系统下面，有着不同的版本，还都不兼容。</br>

我们在这里介绍如何用**pip**安装ubuntu系统上的tensorflow，因为这是一种我们认为相对比较简单快捷的途径。如果需要了解怎样用Docker或virtualenv (virtual environment)来安装，可以参考tensorflow的官方网站。</br>

首先，需要为ubuntu升级pip，经过我们的尝试，各种tutorials上面提及的方法并没有都成功。</br>
1. 最先用sudo pip install --upgrade pip报错
2. 依照官网tensorflow.org，用sudo pip install -U pip也不行
3. 于是，我们选择从pip官网下载最新可用的pip，即从 pypi.python.org/pypi/pip 下载，注意选择与电脑系统和python版本相应的pip。例如，我们选择的是python2.7可用的9.0.1版本pip。
4. 下载之后，用sudo -H pip install pip-9.0.1-py2.py3-none-any.whl后显示usccessfully installed, 安装pip 9.0.1版本成功。
