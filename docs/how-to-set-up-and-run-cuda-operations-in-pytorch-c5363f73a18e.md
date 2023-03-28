# 如何在 PyTorch 中设置和运行 Cuda 操作

> 原文：<https://pub.towardsai.net/how-to-set-up-and-run-cuda-operations-in-pytorch-c5363f73a18e?source=collection_archive---------4----------------------->

# 介绍

近年来深度学习的出现创造了对计算资源和加速工作负载的需求。深度学习中涉及的各种操作，如矩阵乘法、图像平铺和处理语音样本块，可以并行化，以获得更好的性能，并加速机器学习模型的开发。因此，许多深度学习库，如 TensorFlow 和 Pytorch，为用户提供了一组函数或 API 来利用他们的 GPU。CUDA 就是这样一种编程模型和计算平台，它使我们能够通过在 GPU 之间并行化任务来更快地执行复杂的操作。

本文将讨论什么是 CUDA，以及如何设置 CUDA 环境并运行 Pytorch 中可用的各种 CUDA 操作。

![](img/91119a303d52d14180df601536033db6.png)

卢卡斯·凯普纳在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

# 什么是 CUDA

**CUDA**(**C**computer**U**ni fied**D**evice**A**architecture)是 Nvidia 开发的编程模型和并行计算平台。使用 CUDA，可以最大限度地利用 Nvidia 提供的 GPU，从而提高计算能力，并通过并行化任务更快地执行操作。PyTorch 提供了一个 torch.cuda 库来设置和运行 cuda 操作。

使用 Pytorch CUDA，我们可以创建张量并将它们分配给设备。一旦分配，我们就可以对其执行操作，并且结果也被分配给设备。

# 装置

Pytorch 在其官方网站上提供了一个用户友好的界面，我们可以在那里选择我们的操作系统、期望的编程语言和其他要求，如下图所示。

参考 Pytorch 官方链接— [本地启动| PyTorch](https://pytorch.org/get-started/locally/) 并根据我们的系统规格选择要求。Pytorch 为 Windows 和 Linux 操作系统提供了 CUDA 库。对于 windows，请确保使用 CUDA 11.6，因为 windows 不再支持 CUDA 10.2 和 ROCm。对于 Python 编程语言，我们可以在 conda、pip、源码包中选择一个，而 LibTorch 用于 C++和 Java 语言。

# 在 PyTorch 中运行 CUDA 操作

一旦安装成功，我们可以使用 **torch.cuda** 接口在 Pytorch 中运行 cuda 操作。

要确保安装是否成功，请使用 torch.version.cuda 命令，如下所示:

```
# Importing Pytorchimport torch# To print Cuda versionprint(“Pytorch CUDA Version is “, torch.version.cuda)
```

如果安装成功，上述代码将显示以下输出

```
# OutputPytorch CUDA Version is 11.6
```

在使用 CUDA 之前，我们必须确定我们的系统是否支持 CUDA。

使用 torch.cuda.is_available()命令，如下所示

```
# Importing Pytorchimport torch# To check whether CUDA is supportedprint(“Whether CUDA is supported by our system:”, torch.cuda.is_available())
```

上述命令将返回一个布尔值，如下所示

```
# OutputWhether CUDA is supported by our system: True
```

Pytorch CUDA 还提供了以下函数，用于在给定设备 id 时了解设备 ID 和设备名称，如下所示

```
# Importing Pytorchimport torch# To know the CUDA device ID and name of the deviceCuda_id = torch.cuda.current_device()print(“CUDA Device ID: ”, torch.cuda.current_device())print(“Name of the current CUDA Device: ”, torch.cuda.get_device_name(cuda_id))
```

上述代码将显示以下输出–

```
# OutputCUDA Device ID: 0Name of the current CUDA Device: NVIDIA GeForce FTX 1650
```

我们还可以通过指定 ID 来更改默认的 CUDA 设备，如下所示

```
# Importing Pytorchimport torch# To change the Default CUDA devicetorch.cuda.set_device(1)
```

注意:使用 CUDA 时，一定要开发与设备无关的代码，因为有些系统可能没有 GPU，必须在 CPU 上运行，反之亦然。这可以通过在我们的代码中添加下面一行来实现-

```
device = ‘cuda’ if torch.cuda.is_available() else ‘cpu’
```

# 使用 CUDA 操作张量

通常，Pytorch 张量与 NumPy 数组相同。它是一个用于数值计算的 n 维数组。张量和 NumPy 数组的唯一区别是张量可以在 CPU 和 GPU 上运行。

Pytorch CUDA 提供了以下函数来处理张量——

tensor.device 返回张量的设备名称。默认是“CPU”。

tensor.to(设备名称)—返回所述设备上张量的新实例。“CPU”表示 CPU，而“cuda”表示支持 CUDA 的 GPU。

tensor.cpu() —将张量从当前设备传输到 cpu。

让我们通过创建一个张量并执行一些基本操作来理解上述函数的用法。

我们将创建一个样本张量并在 CPU 上执行张量操作(平方)，然后我们将张量传输到 GPU 并再次执行相同的操作并了解性能。

进口火炬

```
# Creating a sample tensorx = torch.randint(1, 1000, (100, 100))# Checking the device name: will return ‘CPU’ by defaultprint(“Device Name: ” , x.device)# Applying tensor operationres_cpu = x ** 2# Transferring tensor to GPUx = x.to(torch.device(‘cuda’))# Checking the device name: will return ‘cuda:0’print(“Device Name after transferring: ”, x.device)# Applying same tensor operationres_gpu = x ** 2# Transferring tensor from GPU to CPUx.cpu()
```

# 使用 CUDA 运行机器学习模型

CUDA 提供以下功能将机器学习模型转移到以下设备

model.to(设备名称)—返回指定设备名称上的机器学习模型的新实例。“CPU”表示 CPU，而“cuda”表示支持 CUDA 的 GPU。

为了演示上述功能，我们将从 torchvision.models 导入预训练的“Resnet-18”模型

```
# Importing PytorchImport torchimport torchvision.models as models# Making the code device-agnosticdevice = ‘cuda’ if torch.cuda.is_available() else ‘cpu’# Instantiating a pre-trained modelmodel = models.resnet18(pretrained=True)# Transferring the model to a CUDA-enabled GPUmodel = model.to(device)
```

一旦模型被转移，我们可以在支持 CUDA 的 GPU 上继续机器学习工作流的剩余部分。

# 结论

读完这篇文章，你可以理解如何在我们的系统中安装 PyTorch CUDA 库，实现 PyTorch CUDA 的基本命令，用 CUDA 处理张量和机器学习模型。