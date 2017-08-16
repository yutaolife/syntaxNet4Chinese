# 声明
此代码借鉴了 [dsindex](https://github.com/dsindex/syntaxnet) 项目中很多的思路。 我们非常的感谢

# 如何使用（未完成）
1， git</br>
2,  配置</br>

配置是一个简单的过程，Google已经把配置文件做的非常的简单。</br>
首先，我们需要去准备我们的三个文件。 train.conll, dev.conll 和 test.conll.这些文件的生成，请参考[准备conllu文件](https://github.com/yutaolife/syntaxNet4Chinese/blob/master/guide/zh/conllu/conllu.md)</br>
其次，按照Google官方的定义，在训练一个新的模型之间，请先编辑修改context.pbtxt的文件。在我的项目当中，这个文件的路径，我放在了UD_Chinese下面。</br>

3， 训练</br>
当上述步骤与过程，全部都配置好以后，就可以开始正式训练了
```
./train.sh -v -v
```
结果如下：


4， 测试</br>
训练完成以后，程序会自动退出。执行以下代码，可以看到输入的语义树：</br>
**请注意**，你的路径应该是 work的目录下
```
echo '猴子 喜欢 吃 香蕉 。' | ./test.sh
```
输出：
```
INFO:tensorflow:Seconds elapsed in evaluation: 0.15, eval metric: 25.00% //这行我把它叫做命中率
INFO:tensorflow:Read 1 documents
Input: 猴子 喜欢 吃 香蕉 .
Parse:
喜欢 VV ROOT
 +-- 猴子 NNP nsubj
 +-- 吃 VV xcomp
 |   +-- 香蕉 NN obj
 +-- . . punct

```

**备注**：</br>
因为我不用syntaxNet做分词，所以我传入之前会把分主词以后的结果交给syntaxNet。所以大家会看到echo后面全部都是分词后的句子。
