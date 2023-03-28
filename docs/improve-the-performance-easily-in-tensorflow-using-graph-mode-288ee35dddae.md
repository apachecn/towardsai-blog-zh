# 使用图形模式轻松提高 TensorFlow 的性能

> 原文：<https://pub.towardsai.net/improve-the-performance-easily-in-tensorflow-using-graph-mode-288ee35dddae?source=collection_archive---------2----------------------->

## 我们将看到使用自动图形模式代码修饰来获得显著的性能提升是多么容易。

![](img/d3377f31843420db99d49978db4140ec.png)

马修·施瓦茨在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

本来 TensorFlow 只允许你在图形模式下编码，但是自从引入了在渴望模式下编码的能力后，大部分生产的笔记本都是渴望模式。

以至于很难找到用图模式编写的代码，大多数刚开始或者已经创建模型一段时间的 TensorFlow 程序员都没有用图模式编程过。

事实是，图形模式下的代码阅读和维护起来要复杂得多，尽管它的效率也高得多。幸运的是，TensorFlow 为我们提供了一种从渴望模式到图形模式的简单方法:签名！

获得一个想法的最好方法是在 Eager 和 Graph 模式下查看一个基本函数的代码。

```
#Eager mode. 
def func_eager(x):
    if (x >0):
        x = x + 1
    return x     

#Same function in graph mode. 
def func_graph(x):
    def if_true():
        return x + 1
    def if_false():
        return x
    x=tf.cond(tf.greater(x, 0), if_true, if_false)
```

这个函数真的很简单:如果 ***x*** 大于 0，它就给**x**加 1。

急切功能毋庸置疑。对于懂一点编程的人来说，阅读起来很简单。但是图形函数中的代码变得非常复杂，很难阅读和理解，更不用说写了。尽管如此，它对机器来说是更好的代码，并且更容易并行执行，这将导致更好的性能。

图形模式代码获得的这些性能改进使它成为许多笔记本电脑非常感兴趣的技术。我们必须利用这一点。

在下一节中，我们将研究一些如何使用亲笔签名的例子。基于一个笔记本，可以在 Kaggle 上找到。在其中，您可以找到 Graph 和 Eager 模式下的函数，从而可以比较这两种方法的性能。

[](https://www.kaggle.com/code/peremartramanonellas/improve-tensorflow-performance-with-graph-mode) [## 使用图形模式提高张量流性能。

### 使用 Kaggle 笔记本探索和运行机器学习代码|使用来自无附加数据源的数据

www.kaggle.com](https://www.kaggle.com/code/peremartramanonellas/improve-tensorflow-performance-with-graph-mode) 

# 测试签名。

我们将使用与上面相同的函数。

```
@tf.function
def func(x):
    if x > 0:
        x = x + 1
    return x
```

唯一的修改是用 ***@tf.function*** 来修饰函数。我们不需要其他任何东西，但是我们很快就会明白为什么不总是这样，为什么不是所有的代码都可以 100%移植到图形模式。

除了知道如何转换代码，查看生成的代码也很有趣。我们只用一行代码就可以做到。

```
print (tf.autograph.to_code(func.python_function))
```

显示的代码是:

```
def tf__func(X):
    with ag__.FunctionScope('func', 'fscope', ag__.ConversionOptions(recursive=True, user_requested=True, optional_features=(), internal_convert_user_code=True)) as fscope:
        do_return = False
        retval_ = ag__.UndefinedReturnValue()

        def get_state():
            return (x,)

        def set_state(vars_):
            nonlocal x
            (x,) = vars_

        def if_body():
            nonlocal x
            x = (ag__.ld(x) + 1)

        def else_body():
            nonlocal x
            pass
        x = ag__.Undefined('x')
        ag__.if_stmt((ag__.ld(x) &gt; 0), if_body, else_body, get_state, set_state, ('x',), 1)
        try:
            do_return = True
            retval_ = ag__.ld(x)
        except:
            do_return = False
            raise
        return fscope.ret(retval_, do_return)
```

它比我写的具有相同功能的要复杂得多，尽管如果我们仔细观察，它具有相同的结构。

所有要执行的代码都包含在包含智能的行之前定义的函数中。流程由 ***if_stmt*** 函数控制，该函数接收一个条件，并具有在函数为真或假时执行的函数。在我们的例子中，条件是 ***x*** 大于 0。满足条件就调用 ***if_body*** ，不满足条件就调用 ***else_body*** 。

让我们来看一些情况，如果我们想在图形模式下使用代码，我们必须修改代码。

例如，**我们不能在函数中声明张量变量，如果我们需要它们的话**。

```
#This function will fail as it does not support declaring tf variables in the body. 
#if you want to execute and test it, remove the comments. </em>
#@tf.function
#def f(x):
#    v = tf.Variable(1.0)
#    return v.assign_add(x)

#For it to work, we just have to remove the variable and declare it outside the function
v = tf.Variable(1.0)
@tf.function
def f(x):
    return v.assign_add(x)
```

解决方法很简单，就是在函数体外部声明变量。

另一个要考虑的例子是 ***print()*** 函数是如何工作的。在图形模式下，这个函数将只执行一次，不管它是否在应该执行多次的循环中。解决方法很简单，用 ***tf.print()*** 函数替换即可。

```
@tf.function
def print_test(): 
    tf.print("with tf.print")
    print("with print")

for i <strong>in</strong> range(5):
    print_test()
```

该函数的结果将是:

```
with print
with tf.print
with tf.print
with tf.print
with tf.print
with tf.print
```

也就是说，该块将被执行五次，但只对 ***print()*** 进行一次调用。 ***断言*** 也会发生类似的情况，必须用相应的***TF . debugging . ASSERT***替换。

这三种情况只是一个示例，尽管它们是我们在试图将代码从 Eager 模式传递到 Graph 模式时最先遇到的。

# 使用几个数据集比较 Eager 和 Graph 模式。

在 Kaggle 上可以找到[的笔记本里，你会找到所有的代码。在本文中，我将只展示与图形模式中的测试和代码直接相关的部分。](https://www.kaggle.com/code/peremartramanonellas/improve-tensorflow-performance-with-graph-mode)

该笔记本已经准备好处理几个非常流行的数据集: ***猫 vs 狗*** 和 ***人 vs 马*** 。在 Kaggle 中，由于平台的内存限制，我使用了人与马的数据集。你可以试试 ***猫 vs 狗*** 数据集，如果你下载了你的笔记本并在内存更大的机器上运行的话。

这两个数据集是 TensorFlow 数据集数据库的一部分。因此，在任何环境中使用笔记本都更加容易，而不必担心从数据集中获取数据。

因为更容易看到所获得的改进，所以我使用了一个定制模型。

可以加速的一个领域是数据处理。在这种情况下，它们是简单的图像，几乎没有处理，但即使如此，也可以看到显著的百分比改善。在像自然语言处理这样的数据处理非常繁重的领域，改进将更加显著。这取决于数据集的大小和您想要执行的处理。

```
#Treat the image in eager mode. 
def map_fn_eager(img, label):
    # resize the image
    img = tf.image.resize(img, size=[IMAGE_SIZE, IMAGE_SIZE])
    # normalize the image
    img /= 255.0
    return img, label

#Treat the image in graph mode. 
@tf.function
def map_fn_graph(img, label):
    # resize the image
    img = tf.image.resize(img, size=[IMAGE_SIZE, IMAGE_SIZE])
    # normalize the image
    img /= 255.0
    return img, label

# Prepare train dataset by using preprocessing with map_fn_eager or graph, shuffling and batching
def prepare_dataset(train_examples, validation_examples, test_examples, num_examples, map_fn, batch_size):
    train_ds = train_examples.map(map_fn).shuffle(buffer_size = num_examples).batch(batch_size)
    valid_ds = validation_examples.map(map_fn).batch(batch_size)
    test_ds = test_examples.map(map_fn).batch(batch_size)

    return train_ds, valid_ds, test_ds
```

可以看到， ***map_fn_eager*** 和 ***map_fn_graph*** 这两个函数的代码是一样的，只是用@tf.function 的修饰有所不同。

还有第三个函数***prepare _ dataset***，这个函数将被调用来准备数据集。它将接收要执行的函数作为参数。当我们调用这个函数时，我们将指出我们是否想要执行准备在图形模式或渴望模式下工作的函数。

```
start_time = time.time()
train_ds_eager, valid_ds_eager, test_ds_eager = prepare_dataset(train_examples, 
                                                                validation_examples, 
                                                                test_examples, 
                                                                num_examples, 
                                                                map_fn_eager, BATCH_SIZE)
end_time = time.time()
print ("Eager Time spend:",  end_time - start_time)

start_time = time.time()
train_ds_graph, valid_ds_graph, test_ds_graph = prepare_dataset(train_examples, 
                                                                validation_examples, 
                                                                test_examples, 
                                                                num_examples, 
                                                                map_fn_graph, BATCH_SIZE)
end_time = time.time()
print ("GraphTime spend:",  end_time - start_time)
```

```
Eager Time sped: 0.061063528060913086
Graph Time spend: 0.0561823844909668
```

如您所见，这是一个非常快速的过程，这很正常，因为数据集很小而且很简单。即便如此，我们只需要一行代码就可以获得 15%的性能提升。一点也不差。**最重要的改进将出现在模式** l 的执行中。

Kaggle 中使用的笔记本可以与三种型号配合使用。其中两个是从 TensorFlow 的 HUB 获得的:A resnet_50 和 resnet_v2_152。但我们将看到第三个模型的结果，这个模型简单得多，是用 TensorFlow 的顺序 API 构建的。如果您可以在更强大的机器上运行它，请不要犹豫尝试其他两个模型。

```
#MODULE_HANDLE = 'https://tfhub.dev/tensorflow/resnet_50/feature_vector/1'
#MODULE_HANDLE = 'https://tfhub.dev/google/imagenet/resnet_v2_152/classification/5'
#model = tf.keras.Sequential([
#    hub.KerasLayer(MODULE_HANDLE, input_shape=(IMAGE_SIZE, IMAGE_SIZE, 3)),
#    tf.keras.layers.Dense(num_classes, activation='softmax')
#])

model = tf.keras.models.Sequential([
            tf.keras.layers.Conv2D(16, (4,4), activation="relu", input_shape=(IMAGE_SIZE, IMAGE_SIZE, 3)),
            tf.keras.layers.MaxPooling2D(2,2),
            tf.keras.layers.Dropout(0.2),   
            tf.keras.layers.Conv2D(32, (4,4), activation="relu"),
            tf.keras.layers.MaxPooling2D(2,2),  
            tf.keras.layers.Dropout(0.2),  
            tf.keras.layers.Conv2D(64, (4,4), activation="relu"),
            tf.keras.layers.MaxPooling2D(2,2),  
            tf.keras.layers.Dropout(0.5), 
            tf.keras.layers.Flatten(), 
            tf.keras.layers.Dense(512, activation="relu"), 
            tf.keras.layers.Dense(2, activation="softmax")])
model.summary()
```

```
Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d (Conv2D)              (None, 221, 221, 16)      784       
_________________________________________________________________
max_pooling2d (MaxPooling2D) (None, 110, 110, 16)      0         
_________________________________________________________________
dropout (Dropout)            (None, 110, 110, 16)      0         
_________________________________________________________________
conv2d_1 (Conv2D)            (None, 107, 107, 32)      8224      
_________________________________________________________________
max_pooling2d_1 (MaxPooling2 (None, 53, 53, 32)        0         
_________________________________________________________________
dropout_1 (Dropout)          (None, 53, 53, 32)        0         
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 50, 50, 64)        32832     
_________________________________________________________________
max_pooling2d_2 (MaxPooling2 (None, 25, 25, 64)        0         
_________________________________________________________________
dropout_2 (Dropout)          (None, 25, 25, 64)        0         
_________________________________________________________________
flatten (Flatten)            (None, 40000)             0         
_________________________________________________________________
dense (Dense)                (None, 512)               20480512  
_________________________________________________________________
dense_1 (Dense)              (None, 2)                 1026      
=================================================================
Total params: 20,523,378
Trainable params: 20,523,378
Non-trainable params: 0
_________________________________________________________________
```

注意，该型号将是定制型号。这意味着我将编写将在每一步中执行的函数，以及控制纪元训练的函数。第二个函数将在渴望和图形模式下执行。

```
# Custom training step. This function is executed in each step each epoch. 
def train_one_step(model, optimizer, x, y, train_loss, train_accuracy):
    with tf.GradientTape() as tape:
        <em># Run the model on input x to get predictions</em>
        predictions = model(x)
        <em># Compute the training loss using `train_loss`, passing in the true y and the predicted y</em>
        loss = train_loss(y, predictions)

    # Using the tape and loss, compute the gradients on model variables using tape.gradient
    grads = tape.gradient(loss, model.trainable_variables)

    # Zip the gradients and model variables, and then apply the result on the optimizer
    optimizer.apply_gradients(zip(grads, model.trainable_variables))

    # Call the train accuracy object on ground truth and predictions
    train_accuracy(y, predictions)
    return loss
```

上述功能将在每个步骤中执行。如你所见，它没有秘密。它进行预测，恢复损失，并计算传递给优化器的梯度，优化器决定如何修改权重。

```
def train_eager(model, optimizer, epochs, train_ds, train_loss, train_accuracy, valid_ds, val_loss, val_accuracy):
    step = 0
    loss = 0.0
    for epoch <strong>in</strong> range(epochs):
        for x, y <strong>in</strong> train_ds:
            # training step number increments at each iteration
            step += 1

            # Run one training step by passing appropriate model parameters
            # required by the function and finally get the loss to report the results
            loss = train_one_step(model, optimizer, x, y, train_loss, train_accuracy)

            # Use tf.print to report your results.</em>
            # Print the training step number, loss and accuracy
            print('Step', step, 
                   ': train loss', loss, 
                   '; train accuracy', train_accuracy.result())

        for x, y <strong>in</strong> valid_ds:
            # Call the model on the batches of inputs x and get the predictions
            y_pred = model(x)
            loss = val_loss(y, y_pred)
            val_accuracy(y, y_pred)
        # Print the validation loss and accuracy

        tf.print('val loss', loss, '; val accuracy', val_accuracy.result())

@tf.function
def train_graph(model, optimizer, epochs, train_ds, train_loss, train_accuracy, valid_ds, val_loss, val_accuracy):
    step = 0
    loss = 0.0
    for epoch in range(epochs):
        for x, y in train_ds:
            # training step number increments at each iteration
            step += 1

            # Run one training step by passing appropriate model parameters
            # required by the function and finally get the loss to report the results
            loss = train_one_step(model, optimizer, x, y, train_loss, train_accuracy)

            # Use tf.print to report your results.
            # Print the training step number, loss and accuracy
            tf.print('Step', step, 
                   ': train loss', loss, 
                   '; train accuracy', train_accuracy.result())

        for x, y in valid_ds:
            # Call the model on the batches of inputs x and get the predictions
            y_pred = model(x)
            loss = val_loss(y, y_pred)
            val_accuracy(y, y_pred)

        # Print the validation loss and accuracy
        tf.print('val loss', loss, '; val accuracy', val_accuracy.result())
```

可以看到，两个函数的代码几乎是一样的。**唯一需要的修改是用 *tf.print()*** 函数替换 *print()* 函数。这些功能在每个步骤调用 ***train_eager*** ，并在指定的时期内执行。

让我们看看在渴望模式下执行该函数的结果:

```
#Solving the model in eager mode, and printing the time elapsed.
st = time.time()
train_eager(model, optimizer, 6, train_ds_eager, 
            train_loss, train_accuracy, valid_ds_eager, 
            val_loss, val_accuracy)
et = time.time()
print('Eager mode spent time: ' et - st)
```

```
......
Step 137 : train loss tf.Tensor(0.00049685716, shape=(), dtype=float32) ; train accuracy tf.Tensor(0.9509188, shape=(), dtype=float32)
Step 138 : train loss tf.Tensor(0.0001548939, shape=(), dtype=float32) ; train accuracy tf.Tensor(0.9510895, shape=(), dtype=float32)
val loss 4.05896135e-05 ; val accuracy 0.98780489
Eager mode spent time: 21.57599711418152
```

图表模式:

```
#Solving the model in graph mode, and printing the time elapsed.
st = time.time()
train_graph(model, optimizer, 6, train_ds_graph, 
            train_loss, train_accuracy, valid_ds_graph, 
            val_loss, val_accuracy)
et = time.time()
print('Graph mode spent time: ' et - st)
```

```
.............
Step 137 : train loss 0.000154053108 ; train accuracy 0.975502133
Step 138 : train loss 3.81469249e-07 ; train accuracy 0.975544751
val loss 2.89767604e-06 ; val accuracy 0.993902445
11.941826820373535
```

正如您所观察到的，模型执行中的性能改进是相当可观的。从 21 秒到 12 秒，提高了大约 50%。

你知道这些数字有些不准确。我们使用玩具数据集。

想象一下您在大型数据集中可以节省的容量。除了这种提高不仅体现在训练时间上，还体现在推理时间上。

# 结论。

老实说，我认为让我们的模型支持图形模式势在必行。不一定要土生土长，但是要支持亲笔签名。

在性能上获得的改进可能非常可观，我们的模型在图形模式下的训练速度比在 Eager 模式下快 50%。如果我们想一想修改代码来实现这一改进是多么容易，很明显，我们必须尝试修改我们所有的笔记本。

我们发现不仅性能有所提高，而且获得的精度值也有所不同。我无法解释为什么。但这是我们必须控制的事情，如果获得的指标不相同，我们必须考虑在每次将函数从渴望模式传递到图形模式时重新评估模型，反之亦然。

这是关于 TensorFlow 和 Keras 中的高级主题的系列文章的一部分，**如果你喜欢它，可以考虑在** [**Medium**](https://medium.com/@peremartra) 上关注我以获得关于新文章的更新。当然，也欢迎你**在** [**LinkedIn**](https://www.linkedin.com/in/pere-martra-0310631) 上与我连线。

![Pere Martra](img/92b0a2efbdea5f262a3b203de380857b.png)

[佩雷·马特拉](https://medium.com/@peremartra?source=post_page-----288ee35dddae--------------------------------)

## 张量流超越基础

[View list](https://medium.com/@peremartra/list/tensorflow-beyond-the-basics-24c4c6a844d8?source=post_page-----288ee35dddae--------------------------------)3 stories![](img/a6cc8494220dde3f66b935ddf24ef15d.png)![](img/a0ef9ec52ab60f8a8c436e6dcafd270b.png)![](img/641c560d79ca678019b7ddabb33854e2.png)