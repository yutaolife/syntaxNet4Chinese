# 安装Java 8
许多在linux下进行Java开发的人员，都会碰到jdk环境变量的设置，对于初学者，这篇文章很有必要．</br>
在Linux下Jdk的安装和Java环境变量的设置

## 1. 下载JDK 8
下载地址： http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
## 2. 解压并安装
## 3. 设置环境变量
使用Vi编辑器进行环境变量的编辑：</br>
在终端中输入命令</br>
```
vi /etc/profile.d/java.sh
```
这样可以在所有的用户中使用
在新的java.sh中输入以下内容：
```
#set java environment
export JAVA_HOME=/usr/java/j2sdk1.4.2_01
export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
```
保存退出
## 4. 给java.sh分配权限
输入以下命令：</br>
```
sudo chmod 755 /etc/profile.d/java.sh
```
## 5. 重启计算机
在终端中输入如下命令，测试jdk是否安装成功</br>
```
java -version
```
如果看到有JVM 的有关信息，则安装成功</br>
