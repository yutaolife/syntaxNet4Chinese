# 声明
我们不是科学家，我们在这里讨论的快速理解SyntaxNet，不具备任何一种学术上面的认知。从实用出发，慢慢去理解过程这个系统的工作方式。我们同时很希望有专业人员，可以帮助我们完善如何从学术的角度理解SyntaxNet的工作方式。

# 什么是SyntaxNet
很多人在问，以至于很多人都想知道SyntaxNet到底是什么。 网易上面有一篇文章《[深度解读谷歌SyntaxNet：全新TensorFlow自然语言处理模型](http://digi.163.com/16/0517/19/BN9S2KU100162OUT.html)》介绍的非常的详细。</br>
总而言之，言而总之，SyntaxNet是语义分析模型，它现在支持[40种语言](https://github.com/tensorflow/models/blob/master/syntaxnet/g3doc/universal.md)。</br>

Language | No. tokens | POS | fPOS | Morph | UAS | LAS
--------  | :--: | :--: | :--: | :--: | :--: | :--:
Ancient_Greek-PROIEL | 18502 | 97.14% | 96.97% | 89.77% | 78.74% | 73.15%
Ancient_Greek | 25251 | 93.22% | 84.22% | 90.01% | 68.98% | 62.07%
Arabic | 28268 | 95.65% | 91.03% | 91.23% | 81.49% | 75.82%
Basque | 24374 | 94.88% | - | 87.82% | 78.00% | 73.36%
Bulgarian | 15734 | 97.71% | 95.14% | 94.61% | 89.35% | 85.01%
Catalan | 59503 | 98.06% | 98.06% | 97.56% | 90.47% | 87.64%
Chinese | 12012 | 91.32% | 90.89% | 98.76% | 76.71% | 71.24%
Croatian | 4125 | 94.67% | - | 86.69% | 80.65% | 74.06%
Czech-CAC | 10862 | 98.11% | 92.43% | 91.43% | 87.28% | 83.44%
Czech-CLTT | 4105 | 95.79% | 87.36% | 86.33% | 77.34% | 73.40%
Czech | 173920 | 98.12% | 93.76% | 93.13% | 89.47% | 85.93%
Danish | 5884 | 95.28% | - | 95.24% | 79.84% | 76.34%
Dutch-LassySmall | 4562 | 95.62% | - | 95.44% | 81.63% | 78.08%
Dutch | 5843 | 89.89% | 86.03% | 89.12% | 77.70% | 71.21%
English-LinES | 8481 | 95.34% | 93.11% | - | 81.50% | 77.37%
English | 25096 | 90.48% | 89.71% | 91.30% | 84.79% | 80.38%
Estonian | 23670 | 95.92% | 96.76% | 92.73% | 83.10% | 78.83%
Finnish-FTB | 16286 | 93.50% | 91.15% | 92.44% | 84.97% | 80.48%
Finnish | 9140 | 94.78% | 95.84% | 92.42% | 83.65% | 79.60%
French | 7018 | 96.27% | - | 96.05% | 84.68% | 81.05%
Galician | 29746 | 96.81% | 96.14% | - | 84.48% | 81.35%
German | 16268 | 91.79% | - | - | 79.73% | 74.07%
Gothic | 5158 | 95.58% | 96.03% | 87.32% | 79.33% | 71.69%
Greek | 5668 | 97.48% | 97.48% | 92.70% | 83.68% | 79.99%
Hebrew | 12125 | 95.04% | 95.04% | 92.05% | 84.61% | 78.71%
Hindi | 35430 | 96.45% | 95.77% | 90.98% | 93.04% | 89.32%
Hungarian | 4235 | 94.00% | - | 75.68% | 78.75% | 71.83%
Indonesian | 11780 | 92.62% | - | - | 80.03% | 72.99%
Irish | 3821 | 91.34% | 89.95% | 77.07% | 74.51% | 66.29%
Italian | 10952 | 97.31% | 97.18% | 97.27% | 89.81% | 87.13%
Kazakh | 587 | 75.47% | 75.13% | - | 58.09% | 43.95%
Latin-ITTB | 6548 | 97.98% | 92.68% | 93.52% | 84.22% | 81.17%
Latin-PROIEL | 14906 | 96.50% | 96.08% | 88.39% | 77.60% | 70.98%
Latin | 4832 | 88.04% | 74.07% | 76.03% | 56.00% | 45.80%
Latvian | 3985 | 80.95% | 66.60% | 73.60% | 58.92% | 51.47%
Norwegian | 30034 | 97.44% | - | 95.58% | 88.61% | 86.22%
Old_Church_Slavonic | 5079 | 96.50% | 96.28% | 89.43% | 84.86% | 78.85%
Persian | 16022 | 96.20% | 95.72% | 95.90% | 84.42% | 80.28%
Polish | 7185 | 95.05% | 85.83% | 86.12% | 88.30% | 82.71%
Portuguese-BR | 29438 | 97.07% | 97.07% | 99.91% | 87.91% | 85.44%
Portuguese | 6262 | 96.81% | 90.67% | 94.22% | 85.12% | 81.28%
Romanian | 18375 | 95.26% | 91.66% | 91.98% | 83.64% | 75.36%
Russian-SynTagRus | 107737 | 98.27% | - | 94.91% | 91.68% | 87.44%
Russian | 9573 | 95.27% | 95.02% | 87.75% | 81.75% | 77.71%
Slovenian-SST | 2951 | 90.00% | 84.48% | 84.38% | 65.06% | 56.96%
Slovenian | 14063 | 96.22% | 90.46% | 90.35% | 87.71% | 84.60%
Spanish-AnCora | 53594 | 98.28% | 98.28% | 97.82% | 89.26% | 86.50%
Spanish | 7953 | 95.27% | - | 95.74% | 85.06% | 81.53%
Swedish-LinES | 8228 | 96.00% | 93.77% | - | 81.38% | 77.21%
Swedish | 20377 | 96.27% | 94.13% | 94.14% | 83.84% | 80.28%
Tamil | 1989 | 79.29% | 71.79% | 75.97% | 64.45% | 55.35%
Turkish | 8616 | 93.63% | 92.62% | 86.79% | 82.00% | 71.37%
**Average** | - | 94.27% | 92.93% | 90.38% | 81.12% | 75.85%


**请注意**：</br>
表格是SyntaxNet里面所提到的已经支持的语义模型，我们会看到里面提到了**Chinese**，可是在这里，我需要解释一下，这个Chinese是繁体中文（Traditional Chinese）,并不是我们所熟知的简体中文（Simplified Chinese）。所以目前的语义分析模型，我们不能直接拿过来使用。

**POS**：part-of-speech</br>
**fPOS**:</br>
**Morph**: A morph is the phonetic realization of a morpheme.</br>
**UAS**: Unlabeled Attachment/Accuracy Score</br>
**LAS**：labeled Attachment/Accuracy Score</br>

# 为什么我们会关注SyntaxNet
国内关注语义分析大多数都是机器翻译这个领域，但是我们想做到通知Google SyntaxNet来完成对于说这些话的人的肖像描述。当然，可能会有很多种方法，很多种的数据可以做人物画像。可是我们的研究，或者我们所想像到的，最直接的肖像建立，无非是从表达的方式，对某一件事情的表达，最能够刻画出来人物的肖像。</br>

另外，一套成熟的语义模型，需要大量的人力，物力来完成。而在此时，Google SyntaxNet恰恰开源了这个项目，我们想从这个项目当中，理解或者研究出来一套理论。</br>

# 快速理解SyntaxNet的工作方式
## 现有模型的使用
如果你认为现有的Google SyntaxNet分布的语义模型，可以达到你的使用的话，完全可以用现有的模型去使用。</br>
Many of these models also support text segmentation, with:</br>
Text segmentation is currently available for: Bulgarian, Czech, German, Greek, English, Spanish, Estonian, Basque, Persian, Finnish, Finnish-FTB, French, Galician, Ancient_Greek, Ancient_Greek-PROIEL, Hebrew, Hindi, Croatian, Hungarian, Indonesian, Italian, Latin, Latin-PROIEL, Dutch, Norwegian, Polish, Portuguese, Slovenian, Swedish, Tamil.</br>
```
MODEL_DIRECTORY=/where/you/unzipped/the/model/files
 cat sentences.txt | syntaxnet/models/parsey_universal/tokenize.sh \
   $MODEL_DIRECTORY > output.conll
```

对于繁体中文的语言：</br>
For Chinese (traditional) we use a larger text segmentation model, which can be run with:</br>
```
MODEL_DIRECTORY=/where/you/unzipped/the/model/files
 cat sentences.txt | syntaxnet/models/parsey_universal/tokenize_zh.sh \
   $MODEL_DIRECTORY > output.conll
```

## 训练新的模型
