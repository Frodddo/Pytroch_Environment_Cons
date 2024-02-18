# Pytorch环境搭建指南

## Pycharm：python 3.9＋CUDA 11.8 + cuDNN 8.9.7 + pytorch 2.2.0

1.安装Anaconda3 

网址：[Index of /anaconda/archive/ | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)

我下载的版本：[Anaconda3-2022.10-Windows-x86_64]

2.安装Anaconda3

![image-20240218132930915](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218132930915.png)

Just Me和All Users两个都可以

![image-20240218133019248](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218133019248.png)

**要勾选上面的！！！**

验证是否安装成功：打开电脑cmd，输入“conda -V”,如果跳出conda版本号，那么说明安装成功

![image-20240218133245329](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218133245329.png)

3.安装Python的IDE：Pycharm

下载网址：[Download PyCharm: Python IDE for Professional Developers by JetBrains](https://www.jetbrains.com/pycharm/download/?section=windows)

4.创建虚拟环境

我创建的配置为 python 3.9＋CUDA 11.8 + cuDNN 8.9.7 + pytorch 2.2.0

打开anaconda prompt，输入“conda create -n py39 python=3.9”

py39为虚拟环境的名字 python=3.9为虚拟环境中python编译器版本为3.9 

有y/N 输入y

安装成功后 应该默认回到base环境

![image-20240218133729533](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218133729533.png)

现在最基础的虚拟环境py39就创建好了 我们要激活并添加pytorch了

5.安装CUDA与cuDNN

在cmd中输入指令“nvidia-smi”

![image-20240218134634925](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218134634925.png)

CUDA-version即为你的电脑能安装的最高的版本，**最高不是只能安装**！

CUDA下载（记得开魔法）：[CUDA Toolkit Archive | NVIDIA Developer](https://developer.nvidia.com/cuda-toolkit-archive)

cuDNN下载（应该要注册登陆下nvidia账号）：[developer.nvidia.com/rdp/cudnn-archive](https://developer.nvidia.com/rdp/cudnn-archive)

注意CUDA与cuDNN版本是一一对应的！

我下载的是 CUDA 11.8 + cuDNN 8.9.7

下载完CUDA 11.8后安装 选择自定义安装 修改下安装路径 自己新建一个安装下

勾选：

![image-20240218140158418](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218140158418.png)

下载位置修改：

![image-20240218140123929](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218140123929.png)

cuDNN应该是一个压缩包 解压后有bin include lib三个文件夹 刚刚CUDA安装后的位置也会有这三个文件夹，直接把cuDNN的三个拖到CUDA的三个文件夹里

验证：

打开anaconda prompt，输入指令“nvcc -V”，显示出类似以下信息那么就成功了

![image-20240218140402043](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218140402043.png)

6.下载Pytorch

下载网址：[PyTorch](https://pytorch.org/)

![image-20240218135329396](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218135329396.png)

这个版本与CUDA11.8对应，注意Package选Conda

在anaconda prompt中激活py39环境“conda activate py39”

输入图片中“conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia”

这样就在py39中安装好了pytorch

接下来验证pytorch是否可用（我之前在环境中配置了Python3.7 由于2.2.0的Pytorch不支持3.8以下的Python版本 我这里报错了 所以验证是否可用是很重要的）

打开anaconda prompt，激活环境后，输入指令"python","import torch","torch.cuda,is_available()"如果是True那么就成功了

![image-20240218135801634](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218135801634.png)

7.Pycharm添加环境

我的方法：

![image-20240218140525168](C:\Users\董晓鸥\AppData\Roaming\Typora\typora-user-images\image-20240218140525168.png)

pycharm左上角settings里选择Project里的Python Interpreter，conda environment里首先添加你的anaconda3的本地文件夹里的Scripts文件夹里的conda.exe 然后下面“Using existing Environment”里就会跳出创建的虚拟环境，我创建了两个py37和py39，所以就有两个，点击Apply