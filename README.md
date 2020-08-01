# NeuralSubdivision SIGGRAPH 2020
## 1.信息
Paper: https://arxiv.org/pdf/2005.01819.pdf <br>
Github：https://github.com/HTDerekLiu/neuralSubdiv <br>

## 2.效率<br>
```
CPU:Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz
GPU:GeForce GTX 1060 6GB
system:win10
Python:3.7.8
Pytorch:1.3.1
```

## 3.论文总结<br>
Paper: https://arxiv.org/pdf/2005.01819.pdf <br>
Github：https://github.com/HTDerekLiu/neuralSubdiv <br>

## 4.论文效果<br>
下述所有展示图片都在result_img文件夹里，相关的obj文件在result_obj文件夹里，其中obj文件后缀_sub0意味着输入，_subi意味着迭代i次.

### 4.1 迭代2次，从左至右，依次是输入，迭代一次，迭代二次的meshlab截图
<center class="half">
    <img src=./result_img/bob.png  height = "290"/>
    <img src=./result_img/spot.png  height = "290"/>
    <img src=./result_img/rocker_arm.png  height = "290"/>
</center>
### 4.2 迭代5次，从左至右,从上至下，依次是输入，迭代一次到迭代5次的meshlab截图
<center class="half">
    <img src=./result_img/bunny.png  height = "290"/>
    <img src=./result_img/bunny_1.png  height = "290"/>
</center>

### 4.3 当三角面片的 aspect ratios 或者 area不符合训练数据时，会出现问题
<center class="half">
    <img src=./result_img/fish.png  height = "290"/>
    <img src=./result_img/horse.png  height = "290"/>
</center>
