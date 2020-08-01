# NeuralSubdivision SIGGRAPH 2020

## 1.信息
Paper: https://arxiv.org/pdf/2005.01819.pdf <br>
Github：https://github.com/HTDerekLiu/neuralSubdiv <br>

## 2.论文概述<br>
此篇文章可以将coarse triangle mesh 上采样成finer triangle mesh.

算法分为两个独立阶段：阶段一，通过fixed topological updates of Loop Subdivision生成mesh的拓扑结构，简言之就是将一个三角面片的边中点连接，把大三角分为四个小三角，所以每精细一次，面片数目扩大四倍；阶段二，通过网络预测顶点的位置。

存在问题：1）目前只适用于三角网格 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2）当三角面片的 aspect ratios 或者 area不符合训练数据时，会出现问题（如4.3）。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;因为当面片的某一条边长过小时，拓扑结构仍旧采取中点划分，此时会放大网络所预测顶点位置的误差，所以当迭代次数增加时，&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;也出现了同样的问题。

## 3.效率<br>
```
CPU:Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz
GPU:GeForce GTX 1060 6GB
System:Win10
Python:3.7.8
Pytorch:1.3.1
```
此篇文章的效率与输入顶点数目有关(阶段一采取python循环，故效率低)：
| number of vertex,  number of face | stage1 | stage2 |
| :------------------: | :------: | :------: |
| 200, 396 | 1.45s |0.36s |
| 12674, 25344 | 52.2s |0.49s |


## 4.论文效果<br>
下述所有展示图片都在result_img文件夹里，相关的obj文件在result_obj文件夹里，其中obj文件后缀_subd0意味着输入，_subdi意味着迭代i次的输出.

#### 4.1 迭代2次，从左至右，依次是输入，迭代一次，迭代二次的meshlab截图
<div  align="center"> 
    <img src=./result_img/bob.png  height = "290"/>
    <img src=./result_img/spot.png  height = "290"/>
    <img src=./result_img/rocker_arm.png  height = "290"/>
</div>

#### 4.2 迭代5次，从左至右,从上至下，依次是输入，迭代一次到迭代5次的meshlab截图
<div  align="center"> 
    <img src=./result_img/bunny.png  height = "290"/>
    <img src=./result_img/bunny_1.png  height = "290"/>
</div>

#### 4.3 当三角面片的 aspect ratios 或者 area不符合训练数据时，会出现问题
<div  align="center"> 
    <img src=./result_img/fish.png  height = "290"/>
    <img src=./result_img/horse.png  height = "290"/>
</div>
