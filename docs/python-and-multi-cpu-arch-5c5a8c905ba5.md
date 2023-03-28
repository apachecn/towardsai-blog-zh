# Python 和多 CPU 架构

> 原文：<https://pub.towardsai.net/python-and-multi-cpu-arch-5c5a8c905ba5?source=collection_archive---------1----------------------->

## 可靠地修复 mac M1/M2 上的 python 工具链损坏

![](img/8f6d876b78f25c602cfb2851a2d4871c.png)

克里斯托夫·高尔在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 介绍

python 的设计目标之一是与平台无关，并且无需修改即可跨环境运行脚本。只要应用程序和库是使用 Python 脚本编写的，python 就能很好地确保这种兼容性。随着 python 的流行和适应性的增加，越来越多的库开始使用 python 扩展来包含本机编译的代码，以提高性能和效率。像 pandas 和 NumPy 这样的流行 python 库可以高效地处理大量数据，这要归功于它们的本地扩展。随着越来越多的 python 库开始使用本机编译的代码，平台兼容性问题开始在 python 环境中出现。如果你使用的是基于 Mx(M1/M2)的 MacBooks，你很可能会在 python 环境中发现平台兼容性问题。本文讨论 python 库管理器(如 pip 和 conda)如何管理平台相关的二进制文件，它们为什么会崩溃，以及如何在 Mac M1/M2 系统上以更简单、更可靠和可复制的方式克服它们。

Python 二进制文件和任何其他二进制文件一样，是针对不同的 CPU 架构和平台(Windows/Mac/Linux)单独编译的。当 python 在系统中安装 Python 库时，它会收集和处理特定于本地 CPU 和平台的元数据。如果 python 库包含任何本机扩展，则需要将其编译成 CPU 和特定于平台的二进制文件，以便在本地运行。简要了解 python 包管理器如‘PIP’和‘conda’如何管理 CPU 和平台依赖性，将有助于理解它的缺点以及如何克服它们。

# PIP 多拱支架

PIP 使用“轮子”打包标准来分发 python 包。“Wheel”是一个打包系统，用于以源代码和编译的二进制格式打包纯 python 脚本和本机扩展。要更好地了解 pip 如何维护不同的分发格式，请访问您选择的图书馆的“PIP”网页，然后单击“下载文件”。在这个页面上,“源代码发行版”部分列出了源代码格式的可用包,“构建的发行版”部分列出了所有预构建的二进制格式的可用包。例如，这个页面[链接](https://pypi.org/project/pandas/#files)显示了“熊猫”库的源代码和预构建的发行版。这些分发包遵循下面指定的命名约定。

```
{dist}-{version}(-{build})?-{python}-{abi}-{platform}.whl
```

{括号}中的每一部分都是一个标签或轮子名称的一个组成部分，其中包含一些关于轮子包含的内容以及轮子在哪里可以工作或不可以工作的含义。示例:

```
pandas-1.5.0-cp311-cp311-macosx_11_0_arm64.whl
```

> pandas —是库名
> 1.5.0 —是库版本
> cp11 —最低要求 python 版本
> cp11 —最低要求应用二进制接口(ABI)
> ma cosx _ 11 _ 0 _ arm 64—平台标签再细分如下:
> —ma cosx—操作系统
> —11 _ 0—最低要求 MacOS SDK 版本
> —arm 64—Cpu 架构

PIP 命名约定还支持“通配符”来优化软件包。比如‘chardet-3 . 0 . 4-py2 . py3-none-any . whl’既支持 python2 又支持 python3，对 ABI 没有依赖性，可以安装在任何平台和 CPU 架构上。许多 python 库使用这些通配符选项来优化包包的数量。有关 Python“轮子”和 PIP 的更多信息，请参考[什么是 Python 轮子，为什么要关注？](https://realpython.com/python-wheels/)

为什么 PIP 安装失败？

大多数情况下，PIP 安装失败有两个主要原因。首先，如果存储库中没有预构建的库，PIP 将在主机系统上编译本机扩展源代码。为此，它希望构建工具和其他依赖库在主机上可用。有时候，这对于本地安装构建依赖项来说是一个挑战，尤其是当依赖树变得很深的时候。

第二，由于轮包名称中的“通配符”。MacBook 最近推出了基于 arm 的“M1/M2”CPU 架构。一些用于 macOS 的较旧的 wheel 包被列为 CPU 架构的“any ”,因为 x86 是当时唯一支持的架构。如果 PIP 将软件包依赖关系解析为这些旧版本中的一个，PIP 将在新的 CPU 架构上安装这个软件包，假设它可以运行。这个问题的一个例子是包“azure-eventhub”。此库依赖于另一个名为“uamqp”的库。本库列出了与 M1/M2 arm64 处理器不兼容的 macOS 通用/通配符包。如果你在 M1/M2 安装“azure-eventhub ”,你会看到这个包会成功安装，但在导入这个包时会抛出一个运行时异常。

# 康达多拱支架

Conda 在确保平台可移植性方面更进了一步。Conda 不仅打包了 python 库，还打包了针对不同操作系统和 CPU 架构的相关库、二进制文件、编译器和 python 解释器本身。这样可以确保整个工具链可以跨环境移植。因为所有依赖的二进制文件都打包了 python 库，所以除了标准的 C 库之外，它不期望对本地系统有任何依赖。那么，如果 conda 提供了更好的可移植性，并修复了 PIP 的缺点，会出什么问题呢？问题是在 Conda 中并不是所有的 python 包都可用。在 conda 环境中使用 pip 来安装在 conda 中不可用的 python 包是很常见的；因此，人们暴露了 PIP 的缺点。再次(不是吹毛求疵)“azure-eventhub”包就是一个相同的例子。

如果有人遇到这样的平台兼容性问题，并且在论坛中搜索解决方案时，他会遇到不同的选项，如安装特定版本的 python 或库，通过其他打包系统(如“brew ”)安装库或安装替代包等。许多这样的修复对于生产来说是不可靠的，并且可能无法跨其他系统复制。下面精选了三个选项，它们是克服 python 平台兼容性问题的更简单、可靠且可复制的方法。它们是:

*   Pip 从源安装
*   康达&罗塞塔
*   多克多拱建筑

# Pip 从源安装

如果一个包的本地代码的编译依赖是最小的，那么可以在主机系统上重新编译它。当 python 工具链(库)安装失败时，最有可能的是，破坏的不是顶层包，而是嵌套在依赖关系树中的依赖包。可以使用下面的命令来指示 pip 不要安装软件包的二进制版本。例如，下面的命令将跳过“uamqp”的二进制 pip 版本，并从源代码编译它。

```
pip install --no-binary uamqp azure-eventhub
```

# 康达&罗塞塔

解决这个问题的另一种方法是利用“Rosetta”。在 Rosetta 上运行 x86 版本的 python 的最简单的选择是使用 conda 平台覆盖选项。例子

```
CONDA_SUBDIR=osx-64 conda create -n myenv_x86 python=3.10
conda activate myenv_x86
conda config --env --set subdir osx-64#Config its using x86_64 platform version of python
python -c "import platform;print(platform.machine())"
```

在执行 conda 环境创建命令时,“CONDA_SUBDIR”环境变量会覆盖 CONDA 的 CPU 架构。conda config 命令始终覆盖新环境中的 CPU 架构，因此无需为该环境中的所有其他命令设置“CONDA_SUBDIR”。在创建一个新的环境并将 conda 平台覆盖到 x86 之后，它的行为就像任何其他 conda 环境一样。人们可以在这个环境中进行 PIP 安装，它将安装 x86 版本的 python 库。在同一个终端中，多个 conda 环境之间的切换是无缝的，甚至像 VS Code 这样的其他工具也可以无缝地工作，没有任何问题。

# 多拱码头

第三种选择是再次利用罗塞塔，但通过“码头工人”。这是可跨多个环境和用户工作的最可移植和最无缝的选项。Docker 的 Multi-Platform 功能可用于强制在 M1/M2 MacBooks 上构建 x86 docker 映像。当向码头工人运行呈现 x86 码头工人映像时，其在内部使用 Rosetta 来运行该映像。以下是构建 x86 跨平台 docker 映像的步骤。

*样本备审文件:*

```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y python3
CMD ["/usr/bin/python3", "-c", "import platform; print(\"Platform:\", platform.machine())"]
```

*打造 x86 码头工人形象:*

```
$ docker build **--platform linux/amd64** . -t img_x86
```

*运行 x86 码头工人形象:*

```
$ docker run **--platform linux/amd64** -it img_x86
Platform: x86_64
```

为了更好地跨多个用户和环境进行移植，可以使用 Dockerfile 的 FROM 命令中的“平台”选项。这确保即使用户未指定 build 命令的“platform”选项，也可以使用 x86 映像。

*样本备审文件:*

```
FROM **--platform=linux/amd64** ubuntuRUN apt-get update
RUN apt-get install -y python3
CMD ["/usr/bin/python3", "-c", "import platform; print(\"Platform:\", platform.machine())"]
```

此码头工人文件将构建 x86 码头工人映像，而不使用“platform”码头工人构建选项。

```
$ docker build . -t img_x86
$ docker run -it img_x86
Platform: x86_64
```

# 结论

上述选项可能不是可靠地修复 python 平台兼容性问题的唯一方法，但我相信，对于我们中的许多人来说，它们将成为一种通用的无需思考的方法，可以快速克服此类问题，避免沮丧，并节省寻找自定义解决方案的时间。希望在不久的将来，Python 生态系统将进一步发展和成熟，以便无缝地处理多个 CPU 和平台，而无需用户的任何额外参与。