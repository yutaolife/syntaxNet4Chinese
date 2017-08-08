# 安装SyntaxNet
有了tensorflow，我们可以开始安装syntaxnet. 在这个github repository的guide文件夹中，我们仅从
如何安装相关环境，安装syntaxnet, 用预先训练的官方初级模型提取英文语义，并简要介绍如何利用
官方预先初步训练的中文模型提取中文语义。目前我们已经可以用自己感兴趣的内容训练独具功能的
中文语义分析模型。但关于用特定语料库训练中文模型，我们暂不在这里讨论。
（官方介绍 https://github.com/tensorflow/models/tree/master/syntaxnet）</br>

下面我们开始。
### 为安装syntaxnet做准备：
#### 安装Bazel

在某种情况下面，Bazel无法安装上去，一直提示要安装:
```
(Reading database ... 104532 files and directories currently installed.)
Preparing to unpack bazel_0.5.3-linux-x86_64.deb ...
Unpacking bazel (0.5.3) over (0.5.3) ...
dpkg: dependency problems prevent configuration of bazel:
 bazel depends on google-jdk | java8-jdk | java8-sdk | oracle-java8-installer; h                                                                         owever:
  Package google-jdk is not installed.
  Package java8-jdk is not installed.
  Package java8-sdk is not installed.
  Package oracle-java8-installer is not installed.
 bazel depends on zlib1g-dev; however:
  Package zlib1g-dev:amd64 is not configured yet.

dpkg: error processing package bazel (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bazel
```
又或者如下错误：  

```
dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_i386.deb (--unpack):
```

可以采用以下解法：
```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install openjdk-9-jdk
```
## 一、为安装syntaxnet做准备：
1. python 安装</br>
  * python 3 在ubuntu上不支持，我们选择2.7版本</br>
2. 安装 bazel
  * 方法一：在 bazel官网 https://docs.bazel.build/versions/master/install.html ，选择和操作系统相配的安装方式。</br>
这个官网说明上关于ubuntu的安装步骤很多，尤其要先处理 jdk 8 的问题。
* 方法二：从 https://github.com/bazelbuild/bazel/releases 选择合适的 .deb 后缀文件，下载后在终端里安装：
    >sudo dpkg -i <.deb 文件名称>

  例如，我们为ubuntu linux选择了 “bazel_0.5.3-linux-x86_64.deb”。
* 安装 bazel 成功后，在终端输入 bazel version 应显示已安装的版本号。</br>
3. 安装 swig: </br>
【swig 是个帮助使用C或者C++编写的软件能与其它各种高级编程语言进行嵌入联接的开发工具。摘自swig中文网】
* 在ubuntu系统上：
    >   apt-get install swig

* 在 OSX 上：
    > brew install swig
</br>

4. 安装protocol buffer：
* 官方的 syntaxnet 并没有讲如何安装，因为默认在此之前我们已经在安装 tensorflow 时有了 protocol, 安装不难：
  * 注意，相对应 python 2.7版本
  * pip install --upgrade \
  https://storage.googleapis.com/tensorflow/linux/cpu/protobuf-3.1.0-cp27-none-linux_x86_64.whl
* 有了 protocol buffer 后，在终端使用
>pip freeze | grep protobuf

检验版本，并且用
>pip install -U protobuf==3.3.0

升级到 syntaxnet 需要的版本 3.3.0. </br>

5. 安装测试工具mock:
>pip install mock </br>

6. asciitree, 语义分析树，一种我们喜闻乐见的输出格式：
>pip install asciitree

7. numpy, 久仰大名的 python 包：
>pip install numpy

* 这里比较棘手的问题是，有时候电脑之前安装的numpy不能卸载，而更新版本就会报错。解决的方式有 </br>
  * （1）在指令后添加 --ignore-installed
  * （2）接触系统对卸载旧版本的限制，如在mac上reboot，长按command+r，终端输csrutil disable, 重启后就可以卸载了。</br>

8. 安装 pygraphviz 这样我们就能看到输出的asciitree了：
  >    apt-get install -y graphviz libgraphviz-dev </br>
  >    pip install pygraphviz --install-option="--include-path=/usr/include/graphviz" --install-option="--library-path=/usr/lib/graphviz/"

* 和上面 numpy 一样，也可能会遇到类似问题，处理方法也是一样的。
* 有些机器需要把这两个分开安装。</br>

## 二、正式建立 bazel 环境
  1. 找个有空间的位置，例如打开终端到达最上层</br>
    > git clone --recursive https://github.com/tensorflow/models.git
    > cd models/syntaxnet/tensorflow
    > ./configure
    > cd ..
    > bazel test ...

  2. 若安装成功，显示所有测试均通过
  3. 其实 syntaxnet 既可以作为一个包给 python 用，也可以用以上方法单独放在文件夹里运行。</br>
    接下来安装 SyntaxNet 和 DRAGNN Python模型：

      * 在最上层directory：
    >mkdir /tmp/syntaxnet_pkg
    >bazel-bin/dragnn/tools/build_pip_package --output-dir=/tmp/syntaxnet_pkg

    >sudo pip install /tmp/syntaxnet_pkg/syntaxnet-x.xx-none-any.whl
    >(因操作系统而异)

  * 若在 OSX 系统运行 Docker ，需要确保 Docker 虚拟机有足够内存。</br>
##三、 用官方预先不成熟的已训练模型分析英文语义
官方其实有预先训练的小模型，既能分析中文又能分析英文，只不过中文是繁体的哦。我们在这里介绍如何用 demo.sh 分析英文语义，即 syntaxnet 最可爱的小礼物。**么么哒！干巴滴擦浪嘿，酷路萌卡酷路萌c！**

* 打开 syntaxnet 所在文件夹，以下称 models/
* 首先，确定所在路径 models/syntaxnet/syntaxnet/demo.sh
* 选择两种输出形式：
  * ascii树：默认英文分析模式，按树的格式从输入文本的根开始，逐层由上到下将组成句子的词语展现。即靠上方为主干词语，靠下方为修饰词语。
  * conll-u表格形式：简要介绍见本github指南上层文件夹conll2017介绍。
* 运行：
  在 models/syntaxnet/syntaxnet 这一层，

  * 上面介绍的输出形式一：

  >echo "要分析的英文文本" | demo.sh

  * 输出形式二：
  > echo "要分析的英文文本" | demo.sh --conll
