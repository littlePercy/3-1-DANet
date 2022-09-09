# DANet
DAnet：Dual Attention Network for Scene Segmentation  
发布于CVPR2019，本文将进行DAnet的论文讲解和复现工作。
![DANet_cvpr2019](https://user-images.githubusercontent.com/52816016/189250053-b5b4ca6e-18e2-4b88-9879-57d182098b70.png)
主要思想:

DAnet的思想并没有之前提到的DFAnet那么花里胡哨，需要各种多层次的连接，DAnet的主要思想就是——同时引入了空间注意力和通道注意力，也就是Dual Attention = Channel Attention + Position Attention。

其中，Position Attention可以在位置上，捕捉任意两个位置之间的上下文信息，而Channel Attention可以捕捉通道维度上的上下文信息

关于Position Attention：较为通俗的解释是，所有的位置，两两之间都有一个权重γ，这个γ的值由两个位置之间的相似性来决定，而不是由两个位置的距离来决定，这就提供了一个好处，也就是——无论两个位置距离多远，只要他们相似度高，空间注意力机制就可以锁定这两个位置。

关于Channel Attention：在高级语义特征中，每一个通道都可以被认为是对于某一个类的特殊响应，增强拥有这种响应的特征通道可以有效的提高分割效果。而通道注意力在EncNet和DFAnet中都有应用，通过计算一个权重因子，对每个通道进行加权，突出重要的通道，增强特征表示。

作者的一些观点:

1. 关于为什么需要Attention机制，作者认为，在卷积的过程中，导致感受野局限在某一范围，而这种操作导致相同类别的像素之间产生一定的差异，这会导致识别上准确率降低的问题。

2. 与大部分作者相同，在文中作者也对ResNet的最后几层做了一些改动，加入空洞卷积，将原先ResNet下采样速率从32倍降低到8倍，也就是ResNet最后一层输出的特征图大小为原始输入的1/8。这样子做的好处就是保留了更多的细节信息，毕竟下采样过多倍速以后细节容易丢失。

版权声明：本文为CSDN博主「yumaomi」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/yumaomi/article/details/124909672
![DANet_P](https://user-images.githubusercontent.com/52816016/189251196-7b74bbeb-bc6a-42f7-a185-bc6ad933d5bb.png)
![DANet_1](https://user-images.githubusercontent.com/52816016/189251204-577ce96c-5e56-4ff3-8f7c-6650a7e22b28.png)
![DANet_C](https://user-images.githubusercontent.com/52816016/189251383-ffe7f373-6c7f-4656-a03e-07a8e9e10d31.png)
![DANet_2](https://user-images.githubusercontent.com/52816016/189251390-30e16380-361a-4250-a38f-baa0b5e4ee86.png)

