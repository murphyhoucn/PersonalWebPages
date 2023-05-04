<font face="黑体" size=10 color=MediumPurple>深度学习开发环境搭建及实验记录</font>

***非教程，仅作为记录，复现不能保证成功***





# 起因

信息论小组作业，老师给了一篇论文，用论文中的方法实现一定的功能。

我首先读了论文，再根据改论文的标题找到了论文的源地址[LSPR2106.10683](https://arxiv.org/abs/2106.10683)，然后找到了论文中用到的源代码[LSPR](https://github.com/JiaxinZhuang/Large-scale-Product-Recognition.Pytorch)


![根据标题找到论文收录地址-康奈尔大学arvix](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E6%A0%B9%E6%8D%AE%E6%A0%87%E9%A2%98%E6%89%BE%E5%88%B0%E8%AE%BA%E6%96%87%E6%94%B6%E5%BD%95%E5%9C%B0%E5%9D%80-%E5%BA%B7%E5%A5%88%E5%B0%94%E5%A4%A7%E5%AD%A6arvix.png)

![下载源代码](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E4%B8%8B%E8%BD%BD%E6%BA%90%E4%BB%A3%E7%A0%81.png)

将源代码clone到本地***（这里有个问题，我挂了VPN，仍然不能git clone，只有下载zip能下载到本地）***。根据作者的说明文档，我对这个程序做了基本的判断：需要深度学习开发环境，用的Python，好像是在Linux系统下跑的程序！

Linux操作系统对我来说确实有点困难，我觉得先试试在Windows下能不能运行吧，于是就开始折腾之路！



# 在Windows下安装深度学习开发环境

因为论文作者只提供了CUDA和PyTorch的版本，我查看了电脑支持的最大CUDA版本是11.6，但是根据作者提供的，我最终选择了安装了CUDA10.2。

![image-20211121112547170](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121112547170.png)

## PyTorch 1.10

直接找了官网，找了相关的配置，直接pip下载了

![pytorch的安装](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/pytorch%E7%9A%84%E5%AE%89%E8%A3%85.png)

![image-20211121113302674](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121113302674.png)

进入python，检查一下pytorch是不是成功安装了

``` python
import torch

x = totch.rand(5,3)

print(x)
```

![image-20211120234607835](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211120234607835.png)

## CUDA 10.2

参考资源:

[如何在Win10下轻松安装CUDA和Cudnn](https://www.bilibili.com/video/BV1q54y1y7Mf)

[CUDA 安装 （windows版）](https://blog.csdn.net/weixin_43848614/article/details/117221384)

按照网上的教学步骤安装即可

![安装CUDA](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E5%AE%89%E8%A3%85CUDA.png)

``` bash
nvcc -V
```

![image-20211120235638749](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211120235638749.png)

跑几个测试看一下

![image-20211120235749266](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211120235749266.png)

![image-20211120235843604](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211120235843604.png)

## cuDNN 7.6.5

参考资料：与CUDA的安装相同相同

[如何在Win10下轻松安装CUDA和Cudnn](https://www.bilibili.com/video/BV1q54y1y7Mf)

[CUDA 安装 （windows版）](https://blog.csdn.net/weixin_43848614/article/details/117221384)

需要注册nVidia开发者账号才能下载cuDNN

![CUDnn的安装需要NVIDIA账户](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/CUDnn%E7%9A%84%E5%AE%89%E8%A3%85%E9%9C%80%E8%A6%81NVIDIA%E8%B4%A6%E6%88%B7.png)

![下载CUDNN](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E4%B8%8B%E8%BD%BDCUDNN.png)

下载之后解压，按照视频中的步骤，直接复制到CUDA的安装路径即可

![image-20211121113659274](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121113659274.png)

![检查CUDA环境变量](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E6%A3%80%E6%9F%A5CUDA%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F.png)



最后再检查一下环境变量是不是已经弄好了！

![检查CUDA环境变量2](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E6%A3%80%E6%9F%A5CUDA%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F2.png)



## TensorFlow2.3.0

Python&CUDA&cuDNN&TensorFlow版本对应关系

[fo40225/tensorflow-windows-wheel: Tensorflow prebuilt binary for Windows (github.com)](https://github.com/fo40225/tensorflow-windows-wheel)

Windows-CPU

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/20210131153046629.png" alt="CPU" style="zoom:150%;" />

Windows-GPU

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/20210131153313535.png" alt="GPU" style="zoom:150%;" />

```bash
pip install tensorflow==2.3.0

pip install tensorflow-gpu==2.3.0
```

注意所有的版本对应，否则会出现各种各样的问题

## 结果

```bash
Windows PowerShell
版权所有 (C) Microsoft Corporation。保留所有权利。

尝试新的跨平台 PowerShell https://aka.ms/pscore6

PS C:\Users\DELL> python --version
Python 3.8.6
PS C:\Users\DELL> nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2019 NVIDIA Corporation
Built on Wed_Oct_23_19:32:27_Pacific_Daylight_Time_2019
Cuda compilation tools, release 10.2, V10.2.89
PS C:\Users\DELL> python
Python 3.8.6 (tags/v3.8.6:db45529, Sep 23 2020, 15:52:53) [MSC v.1927 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> print(torch.__version__)
1.10.0+cu102
>>> import tensorflow as tf
2021-11-21 12:17:03.769777: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cudart64_101.dll
>>> print(tf.__version__)
2.3.0
>>> print(torch.cuda.is_available())
True
>>> tf.test.is_gpu_available()
WARNING:tensorflow:From <stdin>:1: is_gpu_available (from tensorflow.python.framework.test_util) is deprecated and will be removed in a future version.
Instructions for updating:
Use `tf.config.list_physical_devices('GPU')` instead.
2021-11-21 12:19:43.396815: I tensorflow/core/platform/cpu_feature_guard.cc:142] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN)to use the following CPU instructions in performance-critical operations:  AVX2
To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.
2021-11-21 12:19:43.406420: I tensorflow/compiler/xla/service/service.cc:168] XLA service 0x1da756cae50 initialized for platform Host (this does not guarantee that XLA will be used). Devices:
2021-11-21 12:19:43.406558: I tensorflow/compiler/xla/service/service.cc:176]   StreamExecutor device (0): Host, Default Version
2021-11-21 12:19:43.406737: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library nvcuda.dll
2021-11-21 12:19:43.406971: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1716] Found device 0 with properties:
pciBusID: 0000:01:00.0 name: NVIDIA GeForce GTX 1650 computeCapability: 7.5
coreClock: 1.56GHz coreCount: 16 deviceMemorySize: 4.00GiB deviceMemoryBandwidth: 119.24GiB/s
2021-11-21 12:19:43.407083: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cudart64_101.dll
2021-11-21 12:19:43.407208: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cublas64_10.dll
2021-11-21 12:19:43.407387: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cufft64_10.dll
2021-11-21 12:19:43.407520: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library curand64_10.dll
2021-11-21 12:19:43.407593: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cusolver64_10.dll
2021-11-21 12:19:43.407740: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cusparse64_10.dll
2021-11-21 12:19:43.407894: I tensorflow/stream_executor/platform/default/dso_loader.cc:48] Successfully opened dynamic library cudnn64_7.dll
2021-11-21 12:19:43.408023: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1858] Adding visible gpu devices: 0
2021-11-21 12:19:45.176360: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1257] Device interconnect StreamExecutor with strength 1 edge matrix:
2021-11-21 12:19:45.176465: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1263]      0
2021-11-21 12:19:45.176528: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1276] 0:   N
2021-11-21 12:19:45.176750: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1402] Created TensorFlow device (/device:GPU:0 with 2905 MB memory) -> physical GPU (device: 0, name: NVIDIA GeForce GTX 1650, pci bus id: 0000:01:00.0, compute capability: 7.5)
2021-11-21 12:19:45.179856: I tensorflow/compiler/xla/service/service.cc:168] XLA service 0x1da3ed8bce0 initialized for platform CUDA (this does not guarantee that XLA will be used). Devices:
2021-11-21 12:19:45.179952: I tensorflow/compiler/xla/service/service.cc:176]   StreamExecutor device (0): NVIDIA GeForce GTX 1650, Compute Capability 7.5
True
>>>
```



![ceshi](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/ceshi.jpg)

![ceshi222](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/ceshi222.jpg)





# 在WSL-Ubuntu 20.04 安装深度学习开发环境（失败了）

## CUDA 安装失败

参考资料：

[nVidia官方说明文档](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)

[Cuda On WSL 2](https://www.bilibili.com/video/BV1FZ4y1p7Qp)

![dawafg](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/dawafg.jpg)

![fafwrh9haiu](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/fafwrh9haiu.jpg)

原因：可能是CUDA还未适配到WSL的Ubuntu 20.04



# 在WSL-Ubuntu 18.04 安装深度学习开发环境

参考资料：

[GPU in Windows Subsystem for Linux (WSL) | NVIDIA Developer](https://developer.nvidia.com/cuda/wsl)

[CUDA on WSL :: CUDA Toolkit Documentation (nvidia.com)](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)

[nVidia官方说明文档](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)

[Cuda On WSL 2](https://www.bilibili.com/video/BV1FZ4y1p7Qp)

[win10的wsl2安装cuda并配置pytorch](https://zhuanlan.zhihu.com/p/350399229)

[WSL Ubuntu修改软件源](https://www.bilibili.com/video/BV1RJ411X7Uz)

重装了Ubuntu 18.04

切换为WSL2

``` bash
wsl --set-version Ubuntu-18.04 2
```

## CUDA 11.0

下载

``` bash
sudo apt-key adv --fetch-keys http://mirrors.aliyun.com/nvidia-cuda/ubuntu1804/x86_64/7fa2af80.pub

sudo sh -c 'echo "deb http://mirrors.aliyun.com/nvidia-cuda/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda.list'

sudo apt-get update

sudo apt-get install -y cuda-toolkit-11-0
```

配置环境变量

```bash
sudo su -
vim ~/.bashrc
```

用vim打开的文档，在最后面添加如下内容

``` bash
export PATH=/usr/local/cuda-11.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64:$LD_LIBRARY_PATH

# cuda-11.0 自己安装版本的名称
```

安装docker

``` bash
curl https://get.docker.com | sh
```

测试CUDA根据视频[Cuda On WSL 2](https://www.bilibili.com/video/BV1FZ4y1p7Qp)



## cuDNN 8.0.5

在Windows系统下下载cuDNN的压缩包，在Ubuntu下用cp命令从Windows移动到Ubuntu

![tYLIHUWND](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/tYLIHUWND.png)

``` bash
tar -zxvf cudnn-11.0-linux-x64-v8.0.5.39.tgz

# cudnn-11.0-linux-x64-v8.0.5.39.tgz cuDNN压缩包的名称

# 复制
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-11.0/lib64/
sudo cp  cuda/include/cudnn.h /usr/local/cuda-11.0/include/

# 更改权限
sudo chmod a+r /usr/local/cuda-11.0/include/cudnn.h 
sudo chmod a+r /usr/local/cuda-11.0/lib64/libcudnn*
```

![image-20211121140908702](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121140908702.png)



## PyTorch 1.7.1+cu110

安装了3遍才成功了

![gawdagwafw](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/gawdagwafw.jpg)

![hrgegwe](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/hrgegwe.jpg)

```bash
murphy-ubuntu@Murphy-DELL:/mnt/c/Users/DELL$ python
Python 3.6.9 (default, Jan 26 2021, 15:33:00)
[GCC 8.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow
2021-11-21 14:34:29.474127: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudart.so.11.0
>>> import torch
>>> print(torch.cuda.is_available())
True
>>>
```

 

##  TensorFlow 2.4.0

直接用pip install tensorflow安装的版本是最新的版本，不能与CUDA和cnDNN匹配，运行的时候不能调用GPU，因此需要根据文档找到合适的版本

Windows-CPU

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/20210131153046629.png" alt="CPU" style="zoom:150%;" />

Windows-GPU

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/20210131153313535.png" alt="GPU" style="zoom:150%;" />

``` bash
murphy-ubuntu@Murphy-DELL:/mnt/c/Users/DELL$ python
Python 3.6.9 (default, Jan 26 2021, 15:33:00)
[GCC 8.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
WARNING:tensorflow:From <stdin>:1: is_gpu_available (from tensorflow.python.framework.test_util) is deprecated and will be removed in a future version.
Instructions for updating:
Use `tf.config.list_physical_devices('GPU')` instead.
2021-11-21 14:36:24.495813: I tensorflow/compiler/jit/xla_gpu_device.cc:99] Not creating XLA devices, tf_xla_enable_xla_devices not set
2021-11-21 14:36:24.496873: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcuda.so.1
2021-11-21 14:36:24.498697: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:36:24.498759: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1720] Found device 0 with properties:
pciBusID: 0000:01:00.0 name: NVIDIA GeForce GTX 1650 computeCapability: 7.5
coreClock: 1.56GHz coreCount: 16 deviceMemorySize: 4.00GiB deviceMemoryBandwidth: 119.24GiB/s
2021-11-21 14:36:24.498799: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudart.so.11.0
2021-11-21 14:36:24.516945: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcublas.so.11
2021-11-21 14:36:24.517034: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcublasLt.so.11
2021-11-21 14:36:24.532660: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcufft.so.10
2021-11-21 14:36:24.538639: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcurand.so.10
2021-11-21 14:36:24.557670: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcusolver.so.10
2021-11-21 14:36:24.562764: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcusparse.so.11
2021-11-21 14:36:24.564244: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudnn.so.8
2021-11-21 14:36:24.564836: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:36:24.565348: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:36:24.566200: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1862] Adding visible gpu devices: 0
2021-11-21 14:36:24.566892: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudart.so.11.0
2021-11-21 14:36:26.926735: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1261] Device interconnect StreamExecutor with strength 1 edge matrix:
2021-11-21 14:36:26.926810: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1267]      0
2021-11-21 14:36:26.926840: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1280] 0:   N
2021-11-21 14:36:26.928867: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:36:26.928923: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1489] Could not identify NUMA node of platform GPU id 0, defaulting to 0.  Your kernel may not have been built with NUMA support.
2021-11-21 14:36:26.929470: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:36:26.929971: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:36:26.930033: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1406] Created TensorFlow device (/device:GPU:0 with 2875 MB memory) -> physical GPU (device: 0, name: NVIDIA GeForce GTX 1650, pci bus id: 0000:01:00.0, compute capability: 7.5)
True
```





## 结果

``` bash
murphy-ubuntu@Murphy-DELL:/mnt/c/Users/DELL$ neofetch
            .-/+oossssoo+/-.               murphy-ubuntu@Murphy-DELL
        `:+ssssssssssssssssss+:`           -------------------------
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 18.04.2 LTS on Windows 10 x86_64
    .ossssssssssssssssssdMMMNysssso.       Kernel: 5.10.60.1-microsoft-standard-WSL2
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Uptime: 18 mins
  +ssssssssshmydMMMMMMMNddddyssssssss+     Packages: 895
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Shell: bash 4.4.19
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Terminal: /dev/pts/0
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   CPU: Intel i5-9300H (8) @ 2.400GHz
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   GPU: Microsoft Corporation Device 008e
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   Memory: 94MiB / 12654MiB
+sssshhhyNMMNyssssssssssssyNMMMysssssss+
.ssssssssdMMMNhsssssssssshNMMMdssssssss.
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/
  +sssssssssdmydMMMMMMMMddddyssssssss+
   /ssssssssssshdmNNNNmyNMMMMhssssss/
    .ossssssssssssssssssdMMMNysssso.
      -+sssssssssssssssssyyyssss+-
        `:+ssssssssssssssssss+:`
            .-/+oossssoo+/-.

murphy-ubuntu@Murphy-DELL:/mnt/c/Users/DELL$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2020 NVIDIA Corporation
Built on Wed_Jul_22_19:09:09_PDT_2020
Cuda compilation tools, release 11.0, V11.0.221
Build cuda_11.0_bu.TC445_37.28845127_0
murphy-ubuntu@Murphy-DELL:/mnt/c/Users/DELL$ python
Python 3.6.9 (default, Jan 26 2021, 15:33:00)
[GCC 8.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> import tensorflow as tf
2021-11-21 14:38:07.986815: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudart.so.11.0
>>> print(torch.__version__)
1.7.1+cu110
>>> print(tf.__version__)
2.4.0
>>> print(torch.cuda.test_gpu_abailable())
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: module 'torch.cuda' has no attribute 'test_gpu_abailable'
>>> print(torch.cuda.is_available())
True
>>> tf.test.is_gpu_available()
WARNING:tensorflow:From <stdin>:1: is_gpu_available (from tensorflow.python.framework.test_util) is deprecated and will be removed in a future version.
Instructions for updating:
Use `tf.config.list_physical_devices('GPU')` instead.
2021-11-21 14:39:05.764557: I tensorflow/compiler/jit/xla_gpu_device.cc:99] Not creating XLA devices, tf_xla_enable_xla_devices not set
2021-11-21 14:39:05.764673: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcuda.so.1
2021-11-21 14:39:05.765235: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:39:05.765340: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1720] Found device 0 with properties:
pciBusID: 0000:01:00.0 name: NVIDIA GeForce GTX 1650 computeCapability: 7.5
coreClock: 1.56GHz coreCount: 16 deviceMemorySize: 4.00GiB deviceMemoryBandwidth: 119.24GiB/s
2021-11-21 14:39:05.765400: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudart.so.11.0
2021-11-21 14:39:05.767384: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcublas.so.11
2021-11-21 14:39:05.767443: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcublasLt.so.11
2021-11-21 14:39:05.768263: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcufft.so.10
2021-11-21 14:39:05.768539: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcurand.so.10
2021-11-21 14:39:05.771097: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcusolver.so.10
2021-11-21 14:39:05.771751: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcusparse.so.11
2021-11-21 14:39:05.771888: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudnn.so.8
2021-11-21 14:39:05.772427: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:39:05.772838: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:39:05.772878: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1862] Adding visible gpu devices: 0
2021-11-21 14:39:05.772930: I tensorflow/stream_executor/platform/default/dso_loader.cc:49] Successfully opened dynamic library libcudart.so.11.0
2021-11-21 14:39:11.938306: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1261] Device interconnect StreamExecutor with strength 1 edge matrix:
2021-11-21 14:39:11.938386: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1267]      0
2021-11-21 14:39:11.938421: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1280] 0:   N
2021-11-21 14:39:11.939059: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:39:11.939098: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1489] Could not identify NUMA node of platform GPU id 0, defaulting to 0.  Your kernel may not have been built with NUMA support.
2021-11-21 14:39:11.939505: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:39:11.939939: E tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:927] could not open file to read NUMA node: /sys/bus/pci/devices/0000:01:00.0/numa_node
Your kernel may have been built without NUMA support.
2021-11-21 14:39:11.940011: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1406] Created TensorFlow device (/device:GPU:0 with 1951 MB memory) -> physical GPU (device: 0, name: NVIDIA GeForce GTX 1650, pci bus id: 0000:01:00.0, compute capability: 7.5)
True
>>>
```

![gaoylkjgybw](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/gaoylkjgybw.jpg)





# 后续

``` markdown
  - 因为WSL占据的系统存储太大了，且在系统盘，有点担心，就去卸载一些没用的东西；
  - 因为前几天也弄过把Ubuntu从C盘移动到D盘，当时是不允许我移动，我就随便点了一下，然后我看到了系统的硬盘资源在疯狂占用，我想，居然真的搬移了，我还担心搬过去之后配置好的环境是不是就没了。结果我担心的事情发生了，WSL-Ubuntu直接打不开了，直接完蛋，两天时间白费；
  - 在向旺哥和学长诉苦的时候，我以为我真的搞完蛋了，我就在看之前目录的时候，发现了之前的文件夹还在，打不开，我一看文件大小，20多个GB，但是系统上显示的的确是没有了这部分，我就很纳闷，死马当做活马医，就把D盘的Ubuntu搬到了C盘，心里很忐忑，等到搬过去之后，我测试了一下，救过来了，感谢老天，实在是太险了，两天的时间差点就全白费了。唉！
  - 以后真的不敢这么折腾了，太可怕了！
```

从C盘移动到D盘时

![image-20211121144321555](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121144321555.png)

![image-20211121144358342](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121144358342.png)

移动到D盘时，所占存储大小

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121144423968.png" alt="image-20211121144423968" style="zoom:150%;" />

 移动到D盘后Ubuntu打不开了，且KALI也受到影响也打不开了，过了一段时间之后KALI能打开了

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121144528795.png" alt="image-20211121144528795" style="zoom:150%;" />

移动到D盘之后C盘的容量扩大了20多GB，但是我看后台的C盘利用率并没有很大，我猜原来的内容没有删掉，我找了找果然这个20多GB还在这里，我就死马当做活马医，把Ubuntu从D盘又搬回了C盘

![image-20211121144603971](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121144603971.png)

<img src="https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121144835332.png" alt="image-20211121144835332" style="zoom:150%;" />

最后救活了，不敢手贱了

![gaergfEFGUNJ.R](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/gaergfEFGUNJ.R.jpg)



目前C盘仅有了40多GB，等完成了这个作业在再折腾一下这个WSL搬到非系统盘的方法

![image-20211121145134059](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211121145134059.png)



# 语义分割Semantic Segmentation

[[2003.13328\] Strip Pooling: Rethinking Spatial Pooling for Scene Parsing (arxiv.org)](https://arxiv.org/abs/2003.13328)

https://github.com/Andrew-Qibin/SPNet

[[论文笔记\] Strip Pooling（SPNet） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/132532190)

[比较语义分割的几种结构：FCN，UNET，SegNet，PSPNet和Deeplab - yunfeng_net - 博客园 (cnblogs.com)](https://www.cnblogs.com/liuyunfeng/p/10505991.html)

## 简介

语义分割：给图像的每个像素点标注类别。通常认为这个类别与邻近像素类别有关，同时也和这个像素点归属的整体类别有关。利用图像分类的网络结构,可以利用不同层次的特征向量来满足判定需求。现有算法的主要区别是如何提高这些向量的分辨率，以及如何组合这些向量。

## 几种结构

- 全卷积网络FCN：上采样提高分割精度，不同特征向量相加。[3]
- UNET：拼接特征向量；编码-解码结构；采用弹性形变的方式，进行数据增广；用边界加权的损失函数分离接触的细胞。[4]
- SegNet：记录池化的位置，反池化时恢复。[3]
- PSPNet：多尺度池化特征向量，上采样后拼接[3]
- Deeplab：池化跨度为1，然后接带孔卷积。
- ICNet：多分辨图像输入，综合不同网络生成结果。



## semseg（Semantic Segmentation）

作者：香港中文大学的博士生Hengshuang Zhao。https://hszhao.github.io/

基于PyTorch的语义分割开源库semseg：https://github.com/hszhao/semseg

semseg用PyTorch实现的语义分割/场景解析开源库。 它可以方便帮助开发者用于各种语义分割数据集的训练和测试。

该库主要使用ResNet50 / 101/152作为主干网，也可以很容易地改成其他分类网络结构。

>ResNet又名残差神经网络，指的是在传统卷积神经网络中加入残差学习（residual learning）的思想，解决了深层网络中梯度弥散和精度下降（训练集）的问题，使网络能够越来越深，既保证了精度，又控制了速度。

目前已经实现了包括**PSPNet和PSANet**在内的网络，其在2016年ImageNet场景解析挑战赛@ ECCV16，LSUN语义分割挑战赛2017 @ CVPR17和WAD可驾驶区域分割挑战赛2018 @ CVPR18中排名第一。 示例实验数据集包括主流的ADE20K，PASCAL VOC 2012和Cityscapes。

ps. 该库开发者即PSPNet和PSANet算法的一作。

**核心组件Pyramid Pooling Module**

金字塔池化模块Pyramid Pooling Module由一组不同尺度的池化块组成

![img](https://github.com/hszhao/semseg/raw/master/figure/pspnet.png)

![pspnet](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/pspnet.jpg)



- （a）Input Image：即自然场景下拍摄的包含不同目标的原始图；
- （b）Feature Map：即通过前面CNN获得的特征图，**这个CNN是预训练的ResNet**；
- （c）Pyramid Pooling Module：上图中方框POOL表示采用**1x1、2x2、3x3和6x6四种不同尺寸的pooling操作**得到多个尺寸的特征图，并对这些尺寸的特征图再次进行“**1x1的Conv”来减少通道数**。然后采用**双线性插值进行UPSAMPLE**（上采样），即通过上采样来获得金字塔模块前相同尺寸的特征图，并在**通道上进行拼接**；
- （d）Final Prediction：即最终预测结果。

1. 同时支持多线程训练与多进程训练，并且后者非常快（该库比较重视训练）。

2. 重新实现的算法取得更好的结果，而且代码结构清晰（说明代码质量高）。
3. 所有初始化模型、训练得到的模型和预测的结果都能够下载[google drive](https://drive.google.com/open?id=15wx9vOM0euyizq-M1uINgN0_wjVRf9J3)，方便开发者直接使用或者研究比较。

作者推荐的软硬件环境：

![hseta35g](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/hseta35g.png)

[【资源】常用的语义分割架构结构综述以及代码复现 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/77418807)

[场景解析网络PSPNet——金字塔池化模型 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/97706803)

[CNN基础知识——池化（pooling） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/78760534)

[你必须要知道CNN模型：ResNet - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/31852747)



## PSPNet

[Pyramid Scene Parsing Network (hszhao.github.io)](https://hszhao.github.io/projects/pspnet/index.html)

作者：香港中文大学的博士生Hengshuang Zhao。https://hszhao.github.io/

Pyramid Scene Parsing Network：

[[1612.01105\] Pyramid Scene Parsing Network (arxiv.org)](https://arxiv.org/abs/1612.01105)

[GitHub - hszhao/PSPNet: Pyramid Scene Parsing Network, CVPR2017.](https://github.com/hszhao/PSPNet)

[【实验记录】PSPNet（PyTorch）_yaoyz105-CSDN博客_pspnet pytorch](https://blog.csdn.net/qq_31347869/article/details/102476128)

[[论文笔记\] PSPNet：Pyramid Scene Parsing Network - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/115004020)

摘要：

本文提出了基于整合全局上下文信息的金字塔池化模块的PSPNet，这种全局的先验信息能够有效地在场景语义分析中获得高质量的结果。

为了实现准确地场景感知，这需要场景上下文的先验信息。文章发现基于FCN的模型的主要问题是，缺乏合适的策略来利用全局场景的类别信息。 对于典型的复杂场景理解，以前要获得全局图像级别的功能，spatial pyramid pooling被广泛采用，其中空间统计为整体场景解释提供了良好的描述符，SPPNet进一步增强了这个能力。

为了实现准确地场景感知，这需要场景上下文的先验信息。文章发现基于FCN的模型的主要问题是，缺乏合适的策略来利用全局场景的类别信息。 对于典型的复杂场景理解，以前要获得全局图像级别的功能，spatial pyramid pooling被广泛采用，其中空间统计为整体场景解释提供了良好的描述符，SPPNet进一步增强了这个能力。

本文主要有3个贡献：1、提出了PSPNet，在FCN中嵌入了不同场景的上下文特征；2、我们基于深度监督的损失为deep ResNet开发了有效的优化策略；3、我们构建了一个用于最新场景解析和语义分割的实用系统，其中包括了所有关键的实现细节。





## SPNet

作者：[Andrew-Qibin](https://github.com/Andrew-Qibin)

Strip Pooling: Rethinking Spatial Pooling for Scene Parsing：

[[2003.13328\] Strip Pooling: Rethinking Spatial Pooling for Scene Parsing (arxiv.org)](https://arxiv.org/abs/2003.13328)

[GitHub - Andrew-Qibin/SPNet: Code for our CVPR2020 paper "Strip Pooling: Rethinking Spatial Pooling for Scene Parsing"](https://github.com/Andrew-Qibin/SPNet)

SPM

![spnet](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/spnet.png)

MPM

![image-20211225140915981](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211225140915981.png)

The results reported in our paper are originally based on [PyTorch-Encoding](https://github.com/zhanghang1989/PyTorch-Encoding) but the environment settings are a little bit complicated. To ease use, we reimplement our work based on [semseg](https://github.com/hszhao/semseg).

[[论文笔记\] Strip Pooling（SPNet） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/132532190)

[CVPR2020-语义分割：Strip Pooling（条纹池化） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/122571198)



摘要：

事实证明，空间池化在捕获用于场景分析等像素级预测任务的远程上下文信息方面非常有效。

基于条带池化，我们深入了解了空间池化的架构设计：（1）引入了新的条带池化模型，可以使主干网络可以有效地捕捉长距离的依赖关系；（2）提出了一个新颖的、可以将不同的空间池化作为核心的构件块；（3）有组织地在性能上比较了所提出的条带池化和传统的空间池化技术的差别。



![image-20211225112618480](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211225112618480.png)

因为SPNet是基于semseg的环境，因此我们不仅做了SPNet的实验，而且还做了semseg的作者基于semseg做的一个非常著名的PSPNet的实验。

由于SPNet与PSPNet的实验过程类似，下面仅记录PSPNet 。

# PSPNet on WSL-Ubuntu 18.04

**在已经完成"在WSL-Ubuntu 18.04 安装深度学习开发环境"的前提下进行下一步**



## 卸载 CUDA11.0

[卸载cuda11.0并安装cuda11.1和cudnn_u012372401的博客-CSDN博客_卸载cuda11.1](https://blog.csdn.net/u012372401/article/details/117251997?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~default-1.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~default-1.no_search_link)

由于考虑到与pytorch版本的匹配问题，还是决定重装成CUDA10.1

根据网上的教程是用这一行就可以完成卸载，但是在文件目录下并没有找到这个文件

```bash
sudo /usr/local/cuda-11.0/bin/cuda-uninstaller
```

遂采用如下命令，直接选择删除该文件夹

``` bash
sudo rm -rf /usr/local/cuda-11.0
```

## 重装CUDA10.1

```bash
# 下载
wget https://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.243_418.87.00_linux.run
# 安装
sudo sh cuda_10.1.243_418.87.00_linux.run
# 配置环境变量
vim ~/.bashrc

# 使用vim把cuda的路径放到环境变量中
export PATH=/usr/local/cuda-10.1/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-10.1/lib64:$LD_LIBRARY_PATH


# 运行该命令，保存环境变量的配置
source ~/.bashrc
```

![image-20211219142750500](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219142750500.png)

![image-20211219144421658](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219144421658.png)

![image-20211219141854640](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219141854640.png)

![image-20211219142146181](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219142146181.png)

## cuDNN 8.0.5

在nVidia的官网下载cuDNN，到Windows目录下；

用cp命令移动到wsl /home/目录下；

运行如下命令

```bash
# 解压
tar -xzvf cudnn-11.0-linux-x64-v8.0.5.39.tgz
#移动
sudo cp cuda/include/cudnn*.h /usr/local/cuda/include 
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
#修改权限
sudo chmod a+r /usr/local/cuda/include/cudnn*.h /usr/local/cuda/lib64/libcudnn*

```



## 检查 CUDA和cuDNN

[查看cuda和cudnn版本win&linux_天真不无邪，hello和world-CSDN博客_查看cudnn和cuda版本](https://blog.csdn.net/m511655654/article/details/88419965?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2.not_use_machine_learn_pai&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2.not_use_machine_learn_pai)

运行如下命令，检查

``` bash
# cuDNN
cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
# CUDA
cat /usr/local/cuda/version.txt
```

![image-20211219143502295](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219143502295.png)

## 安装Anaconda

在读代码的时候发现，程序的运行需要anaconda环境，于是下载anaconda；

[Index of /anaconda/archive/ | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)

![Murphy_2021-12-08_22-02-57](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/Murphy_2021-12-08_22-02-57.png)

## 使用conda创建虚拟环境

``` bash
# 创建虚拟环境
conda create -n pt140 python==3.7

# pt140是虚拟环境的名称，读代码的时候发现，虚拟环境的名字就叫做pt140，于是直接就叫做这个名字，免得再改代码了
```

![Murphy_2021-12-08_23-02-46](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/Murphy_2021-12-08_23-02-46.png)

激活虚拟环境，可以看到，激活后，在终端出现（pt140）的字样

![image-20211219144221905](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219144221905.png)

## 在虚拟环境pt140下安装PyTroch

这一步很可能安装的是CPU版本的pytorch

在官网直接用命令行下载（这一步是错误的，不要做这一步）

![image-20211219144716255](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219144716255.png)

## 配置pt140

``` bash
# 创建虚拟环境
conda create -n pt140 python==3.7
pip install torch==1.4.0+cu90 torchvision==0.5.0+cu92 -f https://download.pytorch.org/whl/torch_stable.html
pip install tensorboardX
conda install opencv
conda install pillow
conda install pyaml

# clone源文件
git clone https://github.com/hszhao/semseg.git
```



## 运行程序&修改代码

### 不知道什么错误

![5dtygR](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/5dtygR.jpg)

### 无法调用GPU，重装了pytorch

![cjkgrsdh](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/cjkgrsdh.jpg)

在[pytorch的这个网站](https://download.pytorch.org/whl/torch_stable.html)下载whl文件，离线安装

![image-20211219162510029](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219162510029.png)

![gear](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/gear.jpg)

``` python
# testgpu.py

import torch
import torchvision
print(torch.__version__)
print(torch.cuda.is_available())
print(torch.cuda.device_count())
print(torch.cuda.get_device_name())
print(torch.cuda.current_device())
```



![image-20211219145145564](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219145145564.png)

### 代码中用了八个GPU，但是电脑上面只有一个GPU，因此需要将显卡序列改掉

![shrthhj](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/shrthhj.jpg)

注意，在修改代码的时候，我加了一个注释，这个注释不能是中文的，因为编码问题，程序报错

``` bash
# 需要英文注释

# modify GPU
```



![image-20211219150250773](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219150250773.png)

![image-20211219150414672](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219150414672.png)



### 读取数据量序列错误

需要对数据集的list文件进行修改

![image-20211219150449817](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219150449817.png)

![image-20211219150545807](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219150545807.png)



### 成功了，但没完全成功

程序能跑了，但由于显存资源不够，不能完全跑起来

![image-20211219150614087](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219150614087.png)

![saraf](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/saraf.jpg)

![ntsrt](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/ntsrt.jpg)







# PSPNet on Server Ubuntu 16.04

自己电脑上面跑不起代码来，于是用实验室服务器重新环境配置，以运行该项目

## 数据扩增

通过程序，对图像加入高斯噪声，变换亮度等操作，将数据集扩增14倍

![hrfwrg](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/hrfwrg.jpg)

![ategr](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/ategr.jpg)

``` python
# -*- coding: utf-8 -*-

import cv2
import numpy as np
import os.path
import copy

# 椒盐噪声
def SaltAndPepper(src,percetage):
    SP_NoiseImg=src.copy()
    SP_NoiseNum=int(percetage*src.shape[0]*src.shape[1])
    for i in range(SP_NoiseNum):
        randR=np.random.randint(0,src.shape[0]-1)
        randG=np.random.randint(0,src.shape[1]-1)
        randB=np.random.randint(0,3)
        if np.random.randint(0,1)==0:
            SP_NoiseImg[randR,randG,randB]=0
        else:
            SP_NoiseImg[randR,randG,randB]=255
    return SP_NoiseImg

# 高斯噪声
def addGaussianNoise(image,percetage):
    G_Noiseimg = image.copy()
    w = image.shape[1]
    h = image.shape[0]
    G_NoiseNum=int(percetage*image.shape[0]*image.shape[1])
    for i in range(G_NoiseNum):
        temp_x = np.random.randint(0,h)
        temp_y = np.random.randint(0,w)
        G_Noiseimg[temp_x][temp_y][np.random.randint(3)] = np.random.randn(1)[0]
    return G_Noiseimg

# 昏暗
def darker(image,percetage=0.9):
    image_copy = image.copy()
    w = image.shape[1]
    h = image.shape[0]
    #get darker
    for xi in range(0,w):
        for xj in range(0,h):
            image_copy[xj,xi,0] = int(image[xj,xi,0]*percetage)
            image_copy[xj,xi,1] = int(image[xj,xi,1]*percetage)
            image_copy[xj,xi,2] = int(image[xj,xi,2]*percetage)
    return image_copy

# 亮度
def brighter(image, percetage=1.5):
    image_copy = image.copy()
    w = image.shape[1]
    h = image.shape[0]
    #get brighter
    for xi in range(0,w):
        for xj in range(0,h):
            image_copy[xj,xi,0] = np.clip(int(image[xj,xi,0]*percetage),a_max=255,a_min=0)
            image_copy[xj,xi,1] = np.clip(int(image[xj,xi,1]*percetage),a_max=255,a_min=0)
            image_copy[xj,xi,2] = np.clip(int(image[xj,xi,2]*percetage),a_max=255,a_min=0)
    return image_copy

# 旋转
def rotate(image, angle, center=None, scale=1.0):
    (h, w) = image.shape[:2]
    # If no rotation center is specified, the center of the image is set as the rotation center
    if center is None:
        center = (w / 2, h / 2)
    m = cv2.getRotationMatrix2D(center, angle, scale)
    rotated = cv2.warpAffine(image, m, (w, h))
    return rotated

# 翻转
def flip(image):
    flipped_image = np.fliplr(image)
    return flipped_image
    
# 图片文件夹路径
file_dir = r'D:/Python_Develop/datasets/IT/Demo/output/' 
for img_name in os.listdir(file_dir):
    img_path = file_dir + img_name
    img = cv2.imread(img_path)
    # cv2.imshow("1",img)
    # cv2.waitKey(5000)
    # 旋转
    rotated_90 = rotate(img, 90)
    cv2.imwrite(file_dir + img_name[0:-4] + '_r90.jpg', rotated_90)
    rotated_180 = rotate(img, 180)
    cv2.imwrite(file_dir + img_name[0:-4] + '_r180.jpg', rotated_180)

for img_name in os.listdir(file_dir):
    img_path = file_dir + img_name
    img = cv2.imread(img_path)
    # 镜像
    flipped_img = flip(img)
    cv2.imwrite(file_dir +img_name[0:-4] + '_fli.jpg', flipped_img)

    # 增加噪声
    # img_salt = SaltAndPepper(img, 0.3)
    # cv2.imwrite(file_dir + img_name[0:7] + '_salt.jpg', img_salt)
    img_gauss = addGaussianNoise(img, 0.3)
    cv2.imwrite(file_dir + img_name[0:-4] + '_noise.jpg',img_gauss)

    #变亮、变暗
    img_darker = darker(img)
    cv2.imwrite(file_dir + img_name[0:-4] + '_darker.jpg', img_darker)
    img_brighter = brighter(img)
    cv2.imwrite(file_dir + img_name[0:-4] + '_brighter.jpg', img_brighter)

    blur = cv2.GaussianBlur(img, (7, 7), 1.5)
    #      cv2.GaussianBlur(图像，卷积核，标准差）
    cv2.imwrite(file_dir + img_name[0:-4] + '_blur.jpg',blur)

```



## Xftp 代码和数据上传到服务器

![image-20211219151339713](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219151339713.png)

## 创建集群Platform for AI 平台账户

代码将从该平台提交到服务器中

![image-20211219151707948](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219151707948.png)

## 使用集群上预置的系统环境，提交代码

程序不能正常运行，需要重新配置一个符合要求的环境

## 使用Xshell登陆服务器修改一个符合要求的环境

```bash
# 1. 使用 ssh 登陆服务器

# 2. 使用 ssh 登陆一台节点服务器

# 3. sudo docker images 列出服务器上的 dockers 镜像，找到提交任务时使用的镜像

# 4. sudo docker run -it ufoym/deepo:pytorch-py36-cu90 /bin/bash 使用该命令运行该镜像

# 5. 然后我们可以在这里继续安装软件，安装方法和正常 ubuntu 系统一样。安装完成后我们需要将镜像重新保存。

# 6.exit 首先退出容器

# 7. sudo docker ps -a 找到我们刚刚运行的容器

# 8. sudo docker commit 3cac363bc174 ufoym/pytorch-py36-cu90:v1.0 将容器重新保存为镜像，命令中 3cac363bc174 为容器的 id，见上图第一列 CONTAINER ID。ufoym/pytorch-py36-cu90:v1.0 是为镜像修改的名字，:v1.0 是镜像版本，可根据需求修改。

# 9. 保存完之后我们再次查看镜像列表 sudo docker images，此时镜像已经显示了。

```

![image-20211219153819090](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219153819090.png)


### Xshell上对深度学习镜像环境进行配置

``` bash
# 进入我的镜像环境
sudo docker run -it ufoym/pytorch15-py37-cuda101:v1.0 /bin/bash
```

### anaconda3 下载

![image-20211219163336368](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219163336368.png)

![image-20211219163412966](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219163412966.png)

创建conda 虚拟环境 pt140

``` bash 
# 创建虚拟环境
conda create -n pt140 python==3.7
```

conda设置清华源

![image-20211219163516431](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219163516431.png)

``` bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --set show_channel_urls yes

作者：Ginkgo
链接：https://www.jianshu.com/p/7e663bb0d904
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

其他环境的配置

```bash 
pip install torch==1.4.0+cu90 torchvision==0.5.0+cu92 -f https://download.pytorch.org/whl/torch_stable.html
pip install tensorboardX
conda install opencv
conda install pillow
conda install pyaml
```

### CUDA 10.1

![sjlrioegbauo](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/sjlrioegbauo.jpg)

![image-20211219211952632](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219211952632.png)

### cuDNN 8.0.5

在Windows上下载,然后用Xftp传到服务器

**docker cp 命令，将服务器上的文件传到镜像环境下(这一步我不会,找学长帮忙给搞得,操作太快了,没看懂)**

[传输文件到docker容器 - wakasann - 博客园 (cnblogs.com)](https://www.cnblogs.com/fsong/p/11335251.html)

![image-20211219212238816](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219212238816.png)

### pytorch 1.5.0+cu101

![image-20211219212417973](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219212417973.png)

## 验证

``` bash
ssh登陆服务器

ssh登陆节点服务器

# 查看镜像
sudo docker images

# 进入镜像
sudo docker run -it pt140:2.0

# 查看cuda版本
nvcc -V
cat /usr/local/cuda/version.txt
cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
```

![image-20211219213303346](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219213303346.png)

``` bash
# 激活pt140虚拟环境
conda activate pt140

# 进入python
python
import torch

# 查看torch版本和GPU调用情况
print(torch.__version__)
torch.cuda.is_available()

# 问题!!!
# torch不能调用GPU,找不到解决的方向了
```

![image-20211219213503637](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219213503637.png)

# 将docker 镜像推送到阿里云

## 阿里云账户

注册阿里账户

[阿里云](https://cr.console.aliyun.com/cn-shanghai/instances/repositorie)

## 命名空间

![image-20211219224624886](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211219224624886.png)

## 在服务器登陆阿里云

``` bash
sudo docker login --username=murphyhou0928 registry.cn-qingdao.a liyuncs.com
```

![docker 登录阿里云](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/docker%20%E7%99%BB%E5%BD%95%E9%98%BF%E9%87%8C%E4%BA%91.png)

## 把镜像修改为阿里云的 docker 仓库路径

``` bash
sudo docker tag aa553d773527 registry.cn-qingdao.aliyuncs.com/murphyhou/pt140:v1.0
```

![tag docker 镜像到阿里云](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/tag%20docker%20%E9%95%9C%E5%83%8F%E5%88%B0%E9%98%BF%E9%87%8C%E4%BA%91.png)

## 把镜像推送到阿里云

``` bash
sudo docker push registry.cn-qingdao.aliyuncs.com/murphyhou/pt140:v1.0
```

![推送到阿里云仓库](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/%E6%8E%A8%E9%80%81%E5%88%B0%E9%98%BF%E9%87%8C%E4%BA%91%E4%BB%93%E5%BA%93.png)

![image-20211225103355594](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211225103355594.png)



# 在Platform for AI 平台提交代码

![image-20211225103720403](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211225103720403.png)

![jhsdagrghq53](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/jhsdagrghq53.png)

![image-20211225103830678](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/image-20211225103830678.png)

# 结果分析工具程序

## 图像相似度

``` python
from PIL import Image
 
# 将图片转化为RGB
def make_regalur_image(img, size=(64, 64)):
    gray_image = img.resize(size).convert('RGB')
    return gray_image
 
# 计算直方图
def hist_similar(lh, rh):
    assert len(lh) == len(rh)
    hist = sum(1 - (0 if l == r else float(abs(l-r))/max(l,r))for l, r in zip(lh, rh))/len(lh)
    return hist
 
# 计算相似度
def calc_similar(li, ri):
    calc_sim = hist_similar(li.histogram(), ri.histogram())
    return calc_sim
 
if __name__ == '__main__':

    for num in range(151,209):
        patha="./validation/"+str(num)+".png"
        pathb="./color/"+str(num)+".png"
        image1 = Image.open(patha)
        image1 = make_regalur_image(image1)
        image2 = Image.open(pathb)
        image2 = make_regalur_image(image2)
        print("图片"+str(num)+"的相似度为",calc_similar(image1, image2))
 
 
```



## 统计

``` python
import pandas
import numpy
results = [0.5357053546104784,0.5507430161474265,0.5285612742106119,0.603323384344262,0.6080867770442063,0.6575597122000112,0.6114677464392965,0.8446443289317913,0.9043420339718073,0.9041090450680298,0.9943628311157227,0.9301581073676269,0.6554113765607682,0.4948109783779284,0.4464763005574544,0.537724494934082,0.5748386242222617,0.6774920940940619,0.5907715624134954,0.5808468070438285,0.5194940567016602,0.5553396342901941,0.4472212463045831,0.5701756034156457,0.749638084820338,0.7998814375835139,0.7819517675158355,0.7034507667709003,0.8941413242592676,0.9030247433871216,0.9960931142171224,0.9021762212117513,0.6966854060271549,0.5482711791992188,0.5566729593095879,0.6602304149091052,0.6497804211327798,0.5605064664271656,0.5285503069638954,0.7237626953522035,0.6645485884810058,0.6430581410725912,0.6576677958170573,0.6513833999633789,0.5016614719713388,0.6468158204973189,0.7732410430908203,1.0,0.8808919355405141,0.7832873451527739,0.6083869868941091,0.9531558296113718,0.8561667485859004,0.8622514783048857,0.9823717198087157,0.9268625386919616,0.801384002484161,0.768682721808406 ]
sections = [0, 0.1, 0.2, 0.3, 0.4, 0.5,0.6,0.7,0.8,0.9,1.0]
group_names = ['0-0.1', '0.1-0.2', '0.2-0.3', '0.3-0.4', '0.4-0.5','0.5-0.6','0.6-0.7','0.7-0.8','0.8-0.9','0.9-1.0']
x=[]
cuts = pandas.cut(numpy.array(results), sections, labels=group_names)
counts = pandas.value_counts(cuts)
for key, value in dict(counts).items():
    print(key, value)
    x.append(str(value))
```

![rgwFWHEAJRLKNE](https://gitee.com/murphyhou/picgo/raw/master/WSLDLE/rgwFWHEAJRLKNE.jpg)

