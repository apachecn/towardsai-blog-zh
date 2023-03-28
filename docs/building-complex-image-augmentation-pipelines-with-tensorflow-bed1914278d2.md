# 用 Tensorflow 构建复杂的图像增强管道

> 原文：<https://pub.towardsai.net/building-complex-image-augmentation-pipelines-with-tensorflow-bed1914278d2?source=collection_archive---------2----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)，[编程](https://towardsai.net/p/category/programming)

## 使用张量流数据模块构建复杂的图像增强管道。

![](img/53108c1f8325e29ee8c633b9c806ac18.png)

来源:https://www.kaggle.com/docs/tpu

如果您想用 Tensorflow 以最有效的方式训练您的模型，您可能应该使用 [TFRecords](https://www.tensorflow.org/tutorials/load_data/tfrecord) 和 [Tensorflow 数据模块](https://www.tensorflow.org/guide/data)来构建您的管道，但是根据您的应用程序的要求和约束，使用它们可能是必要的而不是可选的，好消息是 Tensorflow 已经使它们变得非常干净和易于使用。

> 在本文中，我们将使用 Tensorflow 数据模块，通过复杂的数据增强组合，以简单而高效的方式构建管道。

我提到的可以改善模型训练的一个选项是使用 TFRecords，TFRecord 是 Tensorflow 提供的一种简单的数据存储格式，我不打算详细介绍 TFRecords，因为这不是本文的重点，但如果您想了解更多信息，请查看 Tensorflow 的教程。

此处提供的信息可应用于在任何硬件中使用 Tensorflow 训练模型，我将使用 TPU 作为目标硬件，因为如果您使用 TPU，可能您已经在尝试充分利用您的资源，无论如何您都需要使用 Tensorflow 数据模块。

# Tensorflow 数据增强

首先，我们将从 Tensorflow 的[官方数据扩充教程中了解数据扩充是如何完成的开始。](https://www.tensorflow.org/tutorials/images/data_augmentation)

```
# Data augmentation function
def augment(image, label):
  image = tf.image.random_crop(image, size=[IMG_SIZE, IMG_SIZE, 3])
  image = tf.image.random_brightness(image, max_delta=0.5)
  image = tf.clip_by_value(image, 0, 1)
  return image, label # Tensorflow data pipeline
train_ds = (
    train_ds
    .shuffle(1000)
    .map(augment, num_parallel_calls=AUTOTUNE)
    .batch(batch_size)
    .prefetch(AUTOTUNE)
)
```

正如我们在**增强**功能中看到的，它将对图像应用一系列变换，首先，它将进行随机裁剪，然后应用随机亮度，最后裁剪值以保持它们在 0 和 1 之间。

根据 Tensorflow 最佳实践，数据扩充功能通常通过**映射**操作应用于数据管道。

上述方法的问题是如何将变换应用于图像，你基本上只是按顺序堆叠它们，一般来说，你需要对应用什么和如何应用有一些控制，让我描述几个场景来说明我的观点。

## 场景 1:

您的数据可能会受益于先进的数据增强技术，如[剪切](https://arxiv.org/pdf/1708.04552.pdf)、[混合](https://arxiv.org/pdf/1710.09412.pdf)或[剪切混合](https://arxiv.org/pdf/1905.04899.pdf)，如果您熟悉它们的工作方式，您会知道对于每个样本，您可能只会应用其中一种。

## 场景 2:

您可能希望使用许多“像素级”增强，像素级我指的是像亮度、伽玛调整、对比度或饱和度这样的变换，通常这些变换的较轻变化可以安全地用于许多不同的数据集，但一次使用所有这些可能会改变太多图像，并最终干扰模型训练。

# 那么，我们能做些什么呢？

如果你熟悉计算机视觉任务的数据增强，你可能听说过像 [Imgaug](https://imgaug.readthedocs.io/) 或[albuminations](https://albumentations.readthedocs.io/en/latest/)这样的库，如果没有，这里是来自 albuminations 库的[两个例子](https://github.com/albumentations-team/albumentations_examples/blob/master/notebooks/example.ipynb)和[关于它如何进行数据增强:](https://albumentations.readthedocs.io/en/latest/examples.html)

```
**def** augment(p=0.5):
    **return** Compose([
        RandomRotate90(),
        Flip(),
        Transpose(),
        OneOf([
            IAAAdditiveGaussianNoise(),
            GaussNoise(),
        ], p=0.2),
        OneOf([
            MotionBlur(p=0.2),
            MedianBlur(blur_limit=3, p=0.1),
            Blur(blur_limit=3, p=0.1),
        ], p=0.2),
        OneOf([
            OpticalDistortion(p=0.3),
            GridDistortion(p=0.1),
            IAAPiecewiseAffine(p=0.3),
        ], p=0.2),
        OneOf([
            CLAHE(clip_limit=2),
            IAASharpen(),
            IAAEmboss(),
            RandomBrightnessContrast(),
        ], p=0.3),
        HueSaturationValue(p=0.3),
    ], p=p)

augmented_image = augment(image=image)['image']
```

我们可以清楚地看到，Albumentations 提供了一种更有效的方式来对图像应用不同的变换。您可以按顺序应用它们，就像 Tensorflow 教程一样，但是您也可以使用像" **OneOf"** 这样的操作，并在一组要应用的变换中只选择一个，最重要的细节是，在这里您可以控制每个变换被应用的概率。
值得注意的是，这些库使用的转换都经过了大量优化，以尽可能快地运行，Albumentations 甚至有一个[基准](https://github.com/albumentations-team/albumentations#benchmarking-results)。

如果我们能够使用像 Albumentations 这样非常高效的库，并且已经通过我们的 Tensorflow 数据管道实现了许多不同的[转换](https://github.com/albumentations-team/albumentations#spatial-level-transforms)，那么这将是两全其美的，但不幸的是，这是不可能的，所以我们能做什么呢？

# 使用 Tensorflow 进行复杂数据扩充

实际上，如果我们发挥一些创造力，我们可以构建与 Albumentation 提供的功能非常接近的数据增强功能，并且只使用 Tensorflow 代码，因此它可以在与 Tensorflow 管道集成的 TPU 上运行，下面是一个简单的示例:

```
def augment(image):
    p_spatial = tf.random.uniform([], 0, 1.0, dtype=tf.float32)
    p_rotate = tf.random.uniform([], 0, 1.0, dtype=tf.float32)

    *# Flips*
    if p_spatial >= .2:
        image = tf.image.random_flip_left_right(image)
        image = tf.image.random_flip_up_down(image)

    *# Rotates*
    if p_rotate > .75:
        image = tf.image.rot90(image, k=3) *# rotate 270º*
    elif p_rotate > .5:
        image = tf.image.rot90(image, k=2) *# rotate 180º*
    elif p_rotate > .25:
        image = tf.image.rot90(image, k=1) *# rotate 90º*

    return image
```

太好了！这个函数有我们喜欢的关于白蛋白的所有东西，并且是纯张量流，让我们检查:
—【x】依次应用变换。
—【x】**变换类型之一(分组)。
—【x】控制应用变换的概率。**

## **让我们来分析一下这个函数是怎么回事。**

**首先，我们定义两个变量 **p_spatial** 和 **p_rotate** ，然后给它们分配概率，这些概率是从随机的[均匀分布](https://en.wikipedia.org/wiki/Continuous_uniform_distribution)中抽样的，这意味着区间[0，1]中的所有数字都有相同的机会被抽样。
然后我们要应用两种不同类型的转换，**翻转**和**旋转**，它们具有不同的语义，因此它们属于不同的组。
对于**翻转**变换，如果 **p_spatial** 大于 **.2** 我们将应用两个随机翻转变换，换句话说，有 **80%的机会**应用这两个随机翻转。
在**旋转**变换时，我们使用了更多的控制，这将类似于相册中的" **OneOf"** "，因为我们只应用了其中一个变换，每个变换都有 **25%的机会**被应用，并且还有 **25%的机会**不应用任何东西，我们需要这种控制，因为没有必要将图像旋转 90 三次，然后**

**利用这个想法，你可以构建比这个复杂得多的数据增强函数，这里有一个我在 [SIIM-ISIC 黑素瘤分类](https://www.kaggle.com/c/siim-isic-melanoma-classification) Kaggle 竞赛中使用的例子:**

```
**def** data_augment(image):
    p_rotation = tf.random.uniform([], 0, 1.0, dtype=tf.float32)
    p_rotate = tf.random.uniform([], 0, 1.0, dtype=tf.float32)
    p_cutout = tf.random.uniform([], 0, 1.0, dtype=tf.float32)
    p_shear = tf.random.uniform([], 0, 1.0, dtype=tf.float32)
    p_crop = tf.random.uniform([], 0, 1.0, dtype=tf.float32)

    **if** p_shear > .2:
        **if** p_shear > .6:
            image = transform_shear(image, config['HEIGHT'], shear=20.)
        **else**:
            image = transform_shear(image, config['HEIGHT'], shear=-20.)

    **if** p_rotation > .2:
        **if** p_rotation > .6:
            image = transform_rotation(image, config['HEIGHT'], rotation=45.)
        **else**:
            image = transform_rotation(image, config['HEIGHT'], rotation=-45.)

    **if** p_crop > .2:
        image = data_augment_crop(image)

    **if** p_rotate > .2:
        image = data_augment_rotate(image)

    image = data_augment_spatial(image)

    image = tf.image.random_saturation(image, 0.7, 1.3)
    image = tf.image.random_contrast(image, 0.8, 1.2)
    image = tf.image.random_brightness(image, 0.1)

 *if p_cutout > .5:*
 *image = data_augment_cutout(image)*

    **return** image

**def** data_augment_spatial(image):
    p_spatial = tf.random.uniform([], 0, 1.0, dtype=tf.float32)

    image = tf.image.random_flip_left_right(image)
    image = tf.image.random_flip_up_down(image)
    **if** p_spatial > .75:
        image = tf.image.transpose(image)

    **return** image

**def** data_augment_rotate(image):
    p_rotate = tf.random.uniform([], 0, 1.0, dtype=tf.float32)

    **if** p_rotate > .66:
        image = tf.image.rot90(image, k=3) *# rotate 270º*
    **elif** p_rotate > .33:
        image = tf.image.rot90(image, k=2) *# rotate 180º*
    **else**:
        image = tf.image.rot90(image, k=1) *# rotate 90º*

    **return** image

**def** data_augment_crop(image):
    p_crop = tf.random.uniform([], 0, 1.0, dtype=tf.float32)
    crop_size = tf.random.uniform([], int(config['HEIGHT']*.7), config['HEIGHT'], dtype=tf.int32)

    **if** p_crop > .5:
        image = tf.image.random_crop(image, size=[crop_size, crop_size, config['CHANNELS']])
    **else**:
        **if** p_crop > .4:
            image = tf.image.central_crop(image, central_fraction=.7)
        **elif** p_crop > .2:
            image = tf.image.central_crop(image, central_fraction=.8)
        **else**:
            image = tf.image.central_crop(image, central_fraction=.9)

    image = tf.image.resize(image, size=[config['HEIGHT'], config['WIDTH']])

    **return** image
```

**我还将留下两个链接来完成使用类似方法的代码示例。
— [上例的完整代码](https://github.com/dimitreOliveira/melanoma-classification/blob/master/Model%20backlog/Train/136_melanoma_5fold_EfficientNetB5_512.ipynb)T5—[tensor flow 高级增强入门笔记本](https://www.kaggle.com/dimitreoliveira/flower-with-tpus-advanced-augmentations)**

**如果你想了解如何在 TPUs 上建立一个完整的 Tensorflow 管道来训练模型，这里有一篇我写的很酷的文章“[有效地使用 TPU 进行图像分类](https://medium.com/swlh/efficiently-using-tpu-for-image-classification-ed20d2970893)”。**

**要了解更多信息，请查看参考资料:
— [Tensorflow TFRecords 教程](https://www.tensorflow.org/tutorials/load_data/tfrecord)
— [Tensorflow 数据模块文档](https://www.tensorflow.org/api_docs/python/tf/data)
— [Tensorflow 数据模块教程](https://www.tensorflow.org/guide/data)
— [使用 tf.data API 提高性能](https://www.tensorflow.org/guide/data_performance)
— [Tensorflow 数据增强教程](https://www.tensorflow.org/tutorials/images/data_augmentation)
— [高效使用 TPU 进行图像分类](https://medium.com/swlh/efficiently-using-tpu-for-image-classification-ed20d2970893)
—**