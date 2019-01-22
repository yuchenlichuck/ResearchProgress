

Vocabulary：

Diabetic retinopathy 糖尿病性视网膜病变

choroidal neovascularization 脉络膜新生血管 CNV with neovascular membrane (white arrowheads) and associated subretinal ﬂuid (arrows). 

 Diabetic macular edema (DME) with retinal-thickening-associated intraretinal ﬂuid (arrows). 糖尿病性黄斑水肿

Multiple drusen (arrowheads) present in early AMD（age-related macular degeneration

fluid 流体

Normal retina with preserved foveal contour and absence of any retinal ﬂuid/edema



DR!  left: 1259	right：1348	all: 2607

DMnotDR	left:2950 right:3107 all:6057



rate: train: test: val == 6: 2: 2 

755 808 | 252 270|

1770 1864 | 590 621





XRray 

training：Normal：1349

PNEUMONIA：3884

test：Normal：234

PNEUMONIA：390



CUDA_VISIBLE_DEVICES=0 

![1547448002473](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547448002473.png)



![1547448924605](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547448924605.png)

x-Ray数据



![1547455174775](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547455174775.png)

x-Ray again

![1547458279921](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547458279921.png)



run 10000 times







![1547461806601](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547461806601.png)

Run DR and DMnotDR





![1547464514654](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547464514654.png)

![1547465920689](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547465920689.png)

![1547474861432](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547474861432.png)

散瞳切过黑边的



![1547516804273](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547516804273.png)

运行过50000次效果并没有提升

![20090624000936-1748614830](C:\Users\PC\Desktop\DR\20090624000936-1748614830.jpg)\









![timg](C:\Users\PC\Desktop\DR\timg.jpg)





![u=203080269,3007400771&fm=214&gp=0](C:\Users\PC\Desktop\DR\u=203080269,3007400771&fm=214&gp=0.jpg)







# Day 2  Some image processing of the picture

DR

![do histeq function](C:\Users\PC\Desktop\DR\下载 (1).png)





### do histeq function





![1547537160598](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547537160598.png)

直方图



![下载](C:\Users\PC\Desktop\DR\下载.png)



original picture

![1547537208287](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\1547537208287.png)



直方图



## DMNOTDR





![下载 (2)](C:\Users\PC\Desktop\DR\下载 (2).png)

original image

![下载 (3)](C:\Users\PC\Desktop\DR\下载 (3).png)

histeq









## 图像平均





2019.1.22

# Cross Validation

　	    　第一种是**简单交叉验证**，所谓的简单，是和其他交叉验证方法相对而言的。首先，我们随机的将样本数据分为两部分（比如： 70%的训练集，30%的测试集），然后用训练集来训练模型，在测试集上验证模型及参数。接着，我们再把样本打乱，重新选择训练集和测试集，继续训练数据和检验模型。最后我们选择损失函数评估最优的模型和参数。　

 　　　　第二种是**S折交叉验证**（S-Folder Cross Validation）。和第一种方法不同，S折交叉验证会把样本数据随机的分成S份，每次随机的选择S-1份作为训练集，剩下的1份做测试集。当这一轮完成后，重新随机选择S-1份来训练数据。若干轮（小于S）之后，选择损失函数评估最优的模型和参数。

　　　　第三种是**留一交叉验证**（Leave-one-out Cross Validation），它是第二种情况的特例，此时S等于样本数N，这样对于N个样本，每次选择N-1个样本来训练数据，留一个样本来验证模型预测的好坏。此方法主要用于样本量非常少的情况，比如对于普通适中问题，N小于50时，我一般采用留一交叉验证。