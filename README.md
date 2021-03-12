# 准备工作

Linux Ubuntu

Anaconda 3

Python 3.8

Cuda 10.1

Pytorch 1.4 https://pypi.tuna.tsinghua.edu.cn/simple/torch/

Pytorch3D 0.2.0 https://conda.anaconda.org/pytorch3d/linux-64

TorchVision 0.5.0 https://pypi.tuna.tsinghua.edu.cn/simple/torchvision/

其中后三者需要手动在网站上下载与python版本和cuda版本相对应的安装包，否则使用anaconda安装容易混淆版本。若是满足上诉版本配置可以直接从下面的链接下载。

[pytorch 1.4](https://pypi.tuna.tsinghua.edu.cn/packages/bc/47/5b7c4f832b600779eed76cac86efbd5054f124bc919930aced51de2ccbb1/torch-1.4.0-cp38-cp38-manylinux1_x86_64.whl#sha256=504915c6bc6051ba6a4c2a43c446463dff04411e352f1e26fe13debeae431778)	  	[pytorch3d 0.2.0](https://conda.anaconda.org/pytorch3d/linux-64/pytorch3d-0.2.0-py38_cu101_pyt14.tar.bz2) 		[torchvision 0.5.0](https://pypi.tuna.tsinghua.edu.cn/packages/30/6b/dc28e1714340d40e9422c4e94179fde72bf52f06f3e0a640beed408f527c/torchvision-0.5.0-cp38-cp38-manylinux1_x86_64.whl#sha256=aa4354d339de2c5ea2633a6c94294c68bae3e42a4b099624299e2a50c9e97a85) 



# 环境配置

`conda create -n p2m python=3.8`
`conda activate p2m`
`pip install torch-1.4.0-cp38-cp38-manylinux1_x86_64.whl torchvision-0.5.0-cp38-cp38-manylinux1_x86_64.whl`
`conda install pytorch3d-0.2.0-py38_cu101_pyt14.tar.bz2`



# 编译ManiFold

接下来的操作默认MeshReconstruction安装在/home/ubuntu/MeshReconstruction路径下

`cd /home/ubuntu/MeshReconstruction/Manifold/build`
`cmake .. -DCMAKE_BUILD_TYPE=Release`
`make`

修改/home/ubuntu/MeshReconstruction目录下的options.py文件的第6行为绝对路径



# 运行

运行脚本在/MeshReconstruction/scripts路径下，1-D1977.sh是有瑕疵的头模点云重建，1-D1977-1.sh是无瑕疵的头模点云重建。

1-D1977点云的迭代重建，第一张图片是目标点云，从第二张图片的初始网格不断形变获得最终结果，可以很好解决鼻子裂缝问题，面部轮廓可以正确重建。

![-1](D:\1-D1977-13000\-1.png)

![0](D:\1-D1977-13000\0.png)

![1](D:\1-D1977-13000\1.png)

![2](D:\1-D1977-13000\2.png)

![3](D:\1-D1977-13000\3.png)

![4](D:\1-D1977-13000\4.png)

![5](D:\1-D1977-13000\5.png)

![6](D:\1-D1977-13000\6.png)

# 目前存在的问题

1.缺失/稀少的点云有一定概率无法重建，如耳朵；

2.含有深腔的部位，如眼睛和嘴巴，重建的特征还不够明显

