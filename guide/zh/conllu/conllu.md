# 什么是 Conll 文件
简单的说明和介绍一下，由于CoNLL是每年不同的共享任务，所以有很多不同的CoNLL格式。Conll 2009的格式介绍在[这里](http://ufal.mff.cuni.cz/conll2009-st/task-description.html)。每一行代表着一个单词，由制表符分隔，并对于这个单词的词性简单分析。</br>

本次，我们所使用的是Conll-U格式的文件。可以在[这里](http://universaldependencies.github.io/docs/format.html)找到更多的说明。</br>

通俗的总结来说，要做语义分析来讲，要么得到语义树，要么就得到Conll的文件。拿到这些才可以去分析，语义的表达。</br>

stackoverflow.com有[What is CoNLL data format?](https://stackoverflow.com/questions/27416164/what-is-conll-data-format)也有简单的问答</br>

Conll 2017 share task:http://www.conll.org/

# 如何生成Conllu文件
## 第一种方式 手工生成
not ready

## 第二种方式 机器生成
采用机器生成Conllu,本文采用Stanford NLP的工具包来生成Conllu的文件。</br>
工具包使用说明：https://stanfordnlp.github.io/CoreNLP/cmdline.html#input

```
java -mx1g -cp "*" edu.stanford.nlp.pipeline.StanfordCoreNLP -props StanfordCoreNLP-chinese.properties -annotators tokenize,ssplit,pos,depparse -file chinese.txt -outputFormat conllu
```
请注意：</br>
chinese.txt的文件是你的语料库，以每一句话做为一行，但是请把**分完词后**的结果写入这个文件，然后传给standford NLP，然后它可以自动产生Conllu方件。</br>

比如：chinese.txt文件是：</br>
原句为： 核心主题就是绝不能以牺牲生态环境为代价换取经济的一时发展。</br>
分词后的句子为：</br>
```
核心 主题 就是 绝不能 以 牺牲 生态 环境 为 代价 换取 经济 的 一时 发展。
```
生成的结果如下所示：</br>
```
1	﻿	        _	_	  NR	 _	  3	  nmod:assmod	  _	_
2	核心	   _	_	 NN	  _	   3	 compound:nn	  _	_
3	主题	   _	_	 NN	  _	   11	 nsubj	_	_
4	就是	   _	_	 AD	  _	   11	 advmod	_	_
5	绝不	   _	_	 AD	  _	   11	 advmod	_	_
6	能	      _	_	  VV	 _	  11	aux:modal	_	_
7	以	      _	_	  P	   _	  10	case	_	_
8	牺牲	   _	_	 NN	  _	   10	 compound:nn	_	_
9	生态	   _	_	 NN	  _	   10	 compound:nn	_	_
10	环境	 _	_	 NN	  _	   11	 nmod:prep	_	_
11	为	   _	_	  VC	 _	  0	  root	_	_
12	代价	_	_	   NN	  _	   11	 dobj	_	_
13	换取	_	_	   VV	  _	   17	 acl	_	_
14	经济	_	_	   NN	  _	   13	 dobj	_	_
15	的	   _	_	  DEG	 _	  13	mark	_	_
16	一时	_	_	   JJ	  _	   17	 amod	_	_
17	发展	_	_	   NN	  _	   11	 dobj	_	_
18	。	   _	_	  PU	 _	  11	punct	_	_

```

# 总结
不管采用哪一种生成的方式，Conllu文件在分析语义的过程当中，都是非常的关键的。</br>
如果你有大量的人工可以做这件事情，你就采用第一种方式。</br>
如果你信任某一机构所产生的，或者说他们公布的，你就用机器来生成。</br>

通往结果的路有很多种，没有必要只走一条路。
