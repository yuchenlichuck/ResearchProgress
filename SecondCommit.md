# 1.23

*glob文件路径查找*

​	查找符合特定规则的文件路径名。跟使用windows下的文件搜索差不多

"*"匹配0个或多个字符；"?"匹配单个字符；"[]"匹配指定范围内的字符，如：[0-9]匹配数字。

ob.glob（pathname), 返回所有匹配的文件路径列表。它只有一个参数pathname，定义了文件路径匹配规则，这里可以是绝对路径，也可以是相对路径。



*训练模型* 

得到数据集中指定图片经过预训练模型Inception-v3前向计算后得到的特征向量文件路径，其中函数输入参数bottleneck_dir为Inception-v3模型瓶颈层结果保存目录，其余输入参数同get_image_path函数。

### The difference bewteen tf.placeholder and tf.Variable

tf.Variable: major for the trainable variables and models' weight(W)or bias(b)

- **声明时，必须提供初始值；**
- 名称的真实含义，在于变量，也即在真实训练时，其值是会改变的，自然事先需要指定初始值； 

tf.placeholder :for trainning sample

- **不必指定初始值，可在运行时，通过 Session.run 的函数的 feed_dict 参数指定；**
- **这也是其命名的原因所在，仅仅作为一种占位符；**

# inceptionv3

**get_model_config**:

width=299 height=299 depth=3

- bottleneck_tensor_name代表瓶颈层结果的tensor名称

bottleneck_tensor_size为Inception-v3模型瓶颈层的节点个数（Inception-v3模型瓶颈层输出为2048维向量），input_width、 input_height和 input_depth分别为模型输入图像的宽、高和位深度（模型输入图像的大小为299×299×3）



- train final layer

定义新的全链接层和softmax层来训练模型以解决新的图片分类问题

1.类别数目，即分类层的输出向量维数

2.分类层输出的tensor名称

3.Inception-v3模型瓶颈层结果所对应的tensor

4.Inception-v3模型瓶颈层的节点个数

5.学习率

*batch——size*

## Cross Validation



Trainning set: 用于训练模型的子集

Test set：用于测试训练后模型的子集

 交叉验证法（Cross Validation） 

  ”交叉验证法”先将数据集D划分为k个大小相似的互斥子集，即D=D1∪D2∪...∪Dk,Di∩Dj=∅(i≠j)D=D1∪D2∪...∪Dk,Di∩Dj=∅(i≠j)。每个子集都尽可能保持数据分布的一致性，即从D中通过分层采样得到。然后，每次用k-1个子集的并集作为训练集，余下的子集作为测试集；这样就可以获得k组训练/测试集，从而可以进行k次训练和测试，最终返回的是k个测试结果的均值。 

显然，交叉验证法评估结果的稳定性和保真性在很大程度上取决于k的取值，为了强调这一点，通常把交叉验证法称为”k折交叉验证”（k-fold cross validation），k通常取10—10折交叉
--------------------- 


当评价估计器的不同设置（”hyperparameters(超参数)”）时，例如手动为 SVM 设置的 `C` 参数， 由于在训练集上，通过调整参数设置使估计器的性能达到了最佳状态；但 *在测试集上* 可能会出现过拟合的情况。 此时，测试集上的信息反馈足以颠覆训练好的模型，评估的指标不再有效反映出模型的泛化性能。 为了解决此类问题，还应该准备另一部分被称为 “validation set(验证集)” 的数据集，模型训练完成以后在验证集上对模型进行评估。 当验证集上的评估实验比较成功时，在测试集上进行最后的评估。

然而，通过将原始数据分为3个数据集合，我们就大大减少了可用于模型学习的样本数量， 并且得到的结果依赖于集合对（训练，验证）的随机选择。

这个问题可以通过 [交叉验证（CV 缩写）](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) 来解决。 交叉验证仍需要测试集做最后的模型评估，但不再需要验证集。

最基本的方法被称之为，*k-折交叉验证* 。 k-折交叉验证将训练集划分为 k 个较小的集合（其他方法会在下面描述，主要原则基本相同）。 每一个 *k* 折都会遵循下面的过程：

> - 将 ![k-1](http://sklearn.apachecn.org/docs/img/51d052e3e4c7f694f3c05eb4159ba243.jpg) 份训练集子集作为 training data （训练集）训练模型，
> - 将剩余的 1 份训练集子集作为验证集用于模型验证（也就是利用该数据集计算模型的性能指标，例如准确率）。

*k*-折交叉验证得出的性能指标是循环计算中每个值的平均值。 该方法虽然计算代价很高，但是它不会浪费太多的数据（如固定任意测试集的情况一样）， 在处理样本数据集较少的问题（例如，逆向推理）时比较有优势。



**synthesize.py**





# left

INFO:tensorflow:Best validation accuracy = 85.78431606292725
INFO:tensorflow:Final test accuracy =  80.52372932434082

