# 1. 分布式计算框架MapReduce
## 1.1. MapReduce概述
MapReduce是`Google`提出的一个软件架构，用于大规模数据集的并行运算。`Map(映射)`和`Reduce(规约)`,及他们的主要思想，是从函数式编程语言借鉴的（可参考java8中Stream API 中类似的map和reduce函数,但java函数式编程发布的时间较晚）。一个MapReduce过程可简单理解为把一堆杂乱无章的数据按照某种特征归纳起来(Map)，然后处理并得到结果(Reduce)。
        
Hadoop MapReduce 是一个分布式计算框架，用于编写批处理应用程序。编写好的程序可以提交到 Hadoop 集群上用于并行处理大规模的数据集。

MapReduce 作业通过将输入的数据集拆分为独立的块，这些块由 map 以并行的方式处理，框架对 map 的输出进行排序，然后输入到 reduce 中。MapReduce 框架专门用于 <key，value> 键值对处理，它将作业的输入视为一组 <key，value> 对，并生成一组 <key，value> 对作为输出。输出和输出的 key 和 value 都必须实现Writable 接口
     
```html
(input) <k1, v1> -> map -> <k2, v2> -> combine -> <k2, v2> -> reduce -> <k3, v3> (output)
```
     
MapReduce的应用场景往往都具有一个共同的特点：任务可被分解成相互独立的子问题，MapReduce编程模型可分为5个步骤：     
(1)迭代。遍历输入数据,将之解析为key/value对。      
(2)将输入key/value对映射成另外一些key/value对(map)。        
(3)依据key对中间数据进行分组(grouping)。      
(4)以组为单位对数据进行规约(reduce)。      
(5)迭代。将最终产生的key/value对保存到输出文件中。      
      
## 1.2. MapReduce编程模型简述
这里以词频统计为例进行说明，MapReduce 处理的流程如下：
      
![MapReduce处理的流程](https://camo.githubusercontent.com/3b204efc2326763ffe927a99a9e9714d86f9e96e/68747470733a2f2f67697465652e636f6d2f68656962616979696e672f426967446174612d4e6f7465732f7261772f6d61737465722f70696374757265732f6d617072656475636550726f636573732e706e67)
       
1. input：读取文本文件。
2. splitting：将文本按照行进行拆分，此时得到的`K1`行数，`V1`表示对应行的文本内容。
3. mapping：并行将每一行按照空格进行拆分，拆分得到的`List(K2,V2)`，其中`K2`代表每一个单词，由于是做词频统计，所以`V2`的值为1，代表出现1次。
4. shuffling：由于`Mapping`操作可能是在不同的机器上并行处理的，所以需要通过`shuffling`将相同`key`值的数据分发到同一个节点上去合并，这样才能统计出最终的结果，此时得到`K2`为每一个单词，`List(V2)`为可迭代集合，`V2`就是`Mapping`中的`V2`。
5. Reducing：这里的案例是统计单词出现的总次数，所以`Reducing`对`List(V2)`进行归纳求和操作，最终输出。
       
MapReduce 编程模型中`splitting`和`shuffing`操作都是由框架实现的，需要我们自己编程实现的只有`mapping`和`reducing`，这也就是`MapReduce`这个称呼的来源。