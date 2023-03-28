# WIN32 包第 1 部分的包装

> 原文：<https://pub.towardsai.net/wrapper-for-win32-package-part-1-cb3148df8dd5?source=collection_archive---------2----------------------->

使用 python 修改启用宏的 Excel 文件的自动化代码。！

![](img/9a5ebab856a4f143476319df4bd1fc34.png)

朱莉安娜·马尔他在 [Unsplash](https://unsplash.com/s/photos/wrapping-paper?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

# 什么是 Win32？

*   Win32 是 32 位和 64 位 Windows 操作系统的应用程序编程接口。有一个包封装了许多 Win32 应用程序编程接口调用，使 Dart 代码可以访问这些调用，而不需要任何 C 编译器或 Windows 软件开发工具包(SDK)。
*   通俗地说，win32 主要专注于 C 编程语言。然而，应用编程接口功能的内部实现已经以多种语言开发。

![](img/a7b45ea5a54525bd5a33164686cc3e2e.png)

照片由[塔达斯·萨](https://unsplash.com/@stadsa?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/windows-logo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 拍摄

# 这篇文章背后的意图

当我在做一个机器学习相关的项目时，我需要操作 excel 表中的值，但是 excel 表是启用宏的格式(。xlsm)。通常，当涉及到启用宏的文件时，可能包含一个模板，该模板在工作表中有许多公式或图形，这些公式或图形根据工作表中的数据而变化。

如果你想操作这些类型的表，普通的包是不够的。即使您尝试用常规的包来操作，启用宏的 Excel 表也可能会损坏。我遇到了同样的挑战，然后我发现有一个名为“win32”的包，它可以帮助使用 python 代码处理启用宏的 Excel 文件。嗯，我花了很大的力气去理解那个包的功能，并通过浏览器找到代码。

然后，我想到为这个特殊的包创建一个包装器，它可以帮助其他遇到同样问题的人。

# 我们开始吧

这篇文章是关于我为 win32 包创建的包装器，它可以帮助你使用 python 代码修改任何类型的 excel 文件。接下来，我详细解释了我们可以使用下面的代码对 excel 文件执行的所有操作。

## 功能

*   **打开工作簿**
    ***定义:***
    -该方法用于打开 excel 工作表中的工作簿。
    -工作簿只不过是多个工作表的集合。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . open _ workbook()*

*   **打开工作表**
    ***定义:*** *——该方法用于打开 excel 工作表中的工作表。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -工作表名称:它应该是特定工作簿中现有工作表的名称。
    ***语法:****excel . open _ worksheet(sheet _ name = " trail ")**

*   ***添加工作簿**
    ***定义:*
    -** 该方法用于在 excel 表中创建工作簿。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . add _ workbook()**

*   ***添加工作表**
    ***定义:*** *——该方法用于根据指定的名称在 excel 中创建工作表。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -工作表名称:创建工作表的名称。
    ***语法:****excel . add _ worksheet(sheet _ name = ' sheet 1 ')***

*   ****显示**
    ***定义:*** *——此方法用于显示 excel。
    -一旦您调用此方法，将显示一个弹出窗口，您可以在其中看到您正在对 excel 文件进行的修改。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . display()****

*   ****隐藏
    *定义:*** -该方法用于隐藏 excel。
    -一旦您调用此方法，弹出窗口将被关闭，您对 excel 文件所做的修改将在后台完成。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . hide()***

*   ****显示提醒**
    ***定义:*** -该方法用于打开和关闭 excel 的提醒。
    -一些启用宏的 excel 文件有很多限制，需要手动允许修改 excel 文件的权限。
    ***参数:*** - Self:是对 Excel 对象的引用。
    - Action:布尔值，可以根据需求指定。
    ***语法:****excel . display _ alerts(action = True)***

*   ****清除内容
    *定义:*** -该方法用于清除 excel 表中已有的内容，从一个位置到另一个位置执行。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    -结束行:结束位置的行索引。
    -结束列:结束位置的列索引。
    ***语法:****excel . clear _ content(start _ row = 5，start_column=2，end_row=10，
    end_column=10)***

*   ****替换单个单元格内容
    *定义:*** -该方法用于将 excel 表中的现有内容替换为新内容，在特定位置执行。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    -内容:可以是任何需要替换的字符串或数字。
    ***语法:****excel . replace _ single _ cell _ content(start _ row = 5，start_column=2，
    content= '这是被替换的内容')***

*   ****替换行式内容
    *定义:*** -该方法用于将 excel 表中现有的行式内容替换为新的内容。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    -内容:这是需要按行替换的元素列表。
    ***语法:****Excel . replace _ row _ content(start _ row = 5，start_column=2，
    content=[1，2，3，' four '，5，True，'这是一张 excel 表'])***

*   ****替换列式内容
    *定义:*** -该方法用于将 excel 表中现有的列内容替换为新的内容。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    -内容:是需要替换的元素列表。
    ***语法:****Excel . replace _ column _ content(start _ row = 5，start_column=2，
    content=[1，2，3，' four '，5，True，'这是一张 excel 表'])***

*   ****替换内容
    *定义:*** -该方法用于在 excel 表的两个方向用新内容替换现有内容。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    - Row Wise:这是一个布尔值，指定沿着行的替换方向。
    - Column Wise:这是一个布尔值，指定沿着列的替换方向。
    -内容:是需要替换的元素列表。
    ***语法:****Excel . replace _ content(start _ row = 5，start_column=2，
    row_wise=True，column_wise=True，
    content=[[1，2，3]，['four '，5]，[True，'这是 excel 工作表'])***

*   ****设置字体格式
    *定义:*** -该方法用于根据 excel 表中的位置设置文本的格式。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    - Style:是字体样式的名称。例如:Arial、Bahnschrift 等。
    - Size:是字体的大小。例如:- 10、20、16 等。
    -垂直对齐:垂直对齐文本。
    For ex:-win32 . constants . XL top，win32.constants.xlBottom，
    win32 . constants . XL center .
    -水平对齐:是文本水平对齐。
    For ex:-win32 . constants . XL left，win32.constants.xlRight，
    win32 . constants . XL center .
    ***语法:****excel . set _ font _ format(start _ row = 5，start_column=2，style='Arial '，
    size=25，verical _ alignment =*win32 . constants . XL center，
    *horizan***

*   ****设置行高
    *定义:*** -该方法用于设置 excel 表格中指定行的高度。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    - Size:是行的大小。例如:- 3、4、10 等。
    ***语法:****excel . set _ row _ height(start _ row = 5，size=2)***

*   ****设置列宽
    *定义:*** -该方法用于设置 excel 表格中指定列的宽度。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始列:起始位置的列索引。
    - Size:是列的大小。例如:- 3、4、10 等。
    ***语法:****excel . set _ column _ width(start _ column = 5，size=2)***

*   ****设置自动行高
    *定义:*** -该方法用于在 excel 表格中自动设置所有行的高度。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . set _ auto _ row _ height()***

*   ****设置自动列宽
    *定义:*** -该方法用于自动设置 excel 表格中所有列的宽度。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . set _ auto _ column _ width()***

*   ****插入图像
    *定义:*** -该方法用于在 excel 表中的某个位置插入图像。
    ***参数:*** - Self:是对 Excel 对象的引用。
    -起始行:起始位置的行索引。
    -起始列:起始位置的列索引。
    -图像路径:是图像的路径，应该是 raw 字符串格式。
    - Height:是图像的高度属性。
    - Width:是图像的宽度属性。
    - Left:该参数表示图像可以从特定位置向左移动。
    - Top:这是一个参数，图像可以从特定位置移动到顶部。
    ***语法:****excel . insert _ image(start _ row = 5，start_column=2，
    img _ path = r '*C:\ Users \巴鲁\ Pictures \ Camera Roll \ my pics \ aaqs 743 . jpg*'，
    height=100，widht=100，left=5，top=5)***

*   ****保存工作簿
    *定义:*** -该方法用于保存 excel 工作表的工作簿。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . save _ workbook()***

*   ****关闭
    *定义:*** ——该方法用于停止后台进程并关闭 excel 文件。
    ***参数:*** - Self:是对 Excel 对象的引用。
    ***语法:****excel . close()***

## **源代码**

**[](https://github.com/balupeddireddy08/ExcelWin) [## GitHub-balupeddireddy 08/ExcelWin](https://github.com/balupeddireddy08/ExcelWin) 

# 结论

我从互联网上获得了所有这些功能，然后我尽力以我自己的方式将它们合并，这样我们所有人都可以实际使用它们，而不用担心语法。由于这篇文章已经很长了，我将用 python 语言写另一篇关于这个包装器类的实际实现的文章，并尝试发布一个关于这个的包，直到复制这个类并使用它的功能。

我希望你有一个有趣的阅读，这篇文章对你有用…🤝

如果你有任何疑问，请告诉我，如果这篇文章有任何错误，请纠正我。所有的建议都是 accepted…✌

# 快乐学习😎**