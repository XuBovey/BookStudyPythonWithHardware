第1章 基础知识
=========

Python是什么？为什么要学习它？在学习Python之前，我们首先要解决的问题就是这几个。可能很多人听说过Python，知道它是一门编程语言，但却说不清它究竟是什么，好在哪，为什么有这么多人愿意花时间去学习它掌握它，那么就让我们带着这些问题开始本章的学习，希望通过这个章节的学习，将会帮助你了解什么是Python，学会使用集成开发环境，熟悉skids开发板，并学会固件的烧写，知道MicroPython与交互式的解释器，并完成你的第一个Python程序。

1.1 认识Python
--------------

1.1.1 起源

Python 的创始人为吉多·范罗苏姆（Guido van Rossum）。于1989年底始创了Python，那时他还在荷兰的CWI（Centrum voorWiskunde enInformatica，国家数学和计算机科学研究院）工作，1989年的圣诞节期间，吉多·范罗苏姆为了在阿姆斯特丹打发时间，决心开发一个新的解释程序，作为ABC语言的一种继承。ABC是由吉多参加设计的一种教学语言，就吉多本人看来，ABC这种语言非常优美和强大，是专门为非专业程序员设计的。但是ABC语言并没有成功，究其原因，吉多认为是非开放造成的。吉多决心在Python中避免这一错误，并获取了非常好的效果。

1991年，第一个Python解释器诞生，它是用C语言实现的，并能够调用C语言的库文件，吉多·范罗苏姆选中Python（蟒蛇）作为程序的名字，Python的标识也是由两条蛇组成如图1-1所示，这主要是因为他是BBC电视剧——巨蟒剧团之飞翔的马戏团（MontyPython's FlyingCircus）的爱好者，他希望这门新的语言能实现他的理念，一种在C和Shell之间，功能全面，易学易用，全面开放的可拓展的语言。

.. image:: /Chapter/picture/image002.png

图1-1 Python的标识

1.1.2 特点

1. 高级语言

伴随着每一代编程语言的产生，我们会达到一个新的高度。汇编语言使人们从繁杂的机器代码中解脱出来，后来有了FORTRAN、C和Pascal语言，它们将计算提升到了崭新
的高度，并且开创了软件开发行业。伴随着C语言诞生了更多的像C++、Java这样的现代编译语言。我们没有止步于此，于是有了强大的、可以进行系统调用的解释型脚本语言，例如Perl和Python。

这些语言都有高级的数据结构，这样就减少了以前“框架”开发需要的时间。像Python中的列表（大小可变的数组）和字典（哈希表）就是内建于语言本身的。在核心语言中提供这些重要的构建单元，可以鼓励人们使用它们，缩短开发时间与代码量，产生出可读性更好的代码。在C语言中，对于混杂数组（Python中的列表）和哈希表（Python中的字典）还没有相应的标准库，所以它们经常被重复实现，并被复制到每个新项目中去。这个过程混乱而且容易产生错误。C++使用标准模板库改进了这种情况，但是标准模版库是很难与Python内建的列表和字典的简洁和易读相提并论的。

2. 面向对象

面向对象编程为数据和逻辑相分离的结构化和过程化编程添加了新的活力。面向对象编程支持将特定的行为、特性以及“和/或”功能与它们要处理或所代表的数据结合在一起。Python的面向对象的特性是与生俱来的。然而，Python绝不像Java或Ruby仅仅是一门面向对象语言，事实上它融汇了多种编程风格。例如，它甚至借鉴了一些像Lisp和Haskell这样的函数语言的特性。

3. 可扩展

首先就算你的项目中有大量的Python代码，你也依旧可以有条不紊地通过将其分离为多个文件或模块加以组织管理。而且你可以从一个模块中选取代码，而从另一个模块中读取属性。更棒的是，对于所有模块，Python的访问语法都是相同的。不管这个模块是Python标准库中的还是你一分钟之前创造的，哪怕是你用其他语言写的扩展都没问题！借助这些特点，你会感觉自己根据需要“扩展”了这门语言。

其次，对于项目中那些性能要求极高的部分，可以用C语言来编写作为对Python的扩展。这种扩展需要Python调用C语言的接口，这些接口和纯Python模块的接口是一模一样的，乃至代码和对象的访问方法也是如出一辙的。唯一不同的是，这些C语言的代码为性能带来了显著的提升。很多时候，使用编译型代码重写程序的瓶颈部分绝对是益处多多的，因为它能明显提升项目的整体性能。

所以程序设计语言中的这种可扩展性使得工程师能够灵活附加或定制工具，缩短开发周期。虽然像C、C++乃至Java等主流第三代语言都拥有该特性，但是这么容易地使用C编写扩展确实是Python的优势。此外，还有像PyRex这样的工具，允许C和Python混合编程，使编写扩展更加轻而易举，因为它会把所有的代码都转换成C语言代码。

除此之外Python可以使用多种语言进行扩展，由于标准实现是使用C语言完成的（也就是CPython），所以可以使用C和C++编写Python扩展。Python的Java实现被称作Jython，可以使用Java编写其扩展。最后，还有IronPython，这是针对.NET或Mono平台的C#实现。你可以使用C#或者VB.Net扩展
IronPython。

4. 丰富的库

Python内置了众多预编译并可移植的功能模块，涵盖了从字符模式到网络编程等一系列应用级编程任务，此外，Python可通过自行开发的库和众多的第三方库简化编程，Python社区提供了大量的第三方库，这些库的使用方式与标准库类似，功能涵盖科学计算、人工智能、机器学习、Web开发、数据库接口、图形系统多个领域。因为Python拥有大量第三方库，所以开发人员不必重复造轮子，就像搭积木一样，只要擅于利用这些库就可以完成绝大部分工作。

1.1.3 解释型语言

计算机是不能够识别高级语言的，所以当我们运行一个高级语言程序的时候，就需要一个“翻译机”来从事把高级语言转变成计算机能读懂的机器语言的过程。这个过程分成两类，第一种是编译，第二种是解释。

如图1-2所示，编译型语言在程序执行之前，先会通过编译器对程序执行一个编译的过程，把程序转变成机器语言。运行时就不需要翻译，而直接执行就可以了。最典型的例子就是C语言。

解释型语言就没有这个编译的过程，而是在程序运行的时候，通过解释器对程序逐行作出解释，然后直接运行，最典型的例子是Ruby。

.. image:: /Chapter/picture/image003.jpg

图1-2 编程语言执行过程

Python是一种解释型语言，这意味着开发过程中没有了编译这个环节。一般来说，由于不是以本地机器码运行，纯粹的解释型语言通常比编译型语言运行的慢。然而，类似于Java，Python实际上是字节编译的，其结果就是可以生成一种近似机器语言的中间形式。这不仅改善了Python的性能，还同时使它保持了解释型语言的优点。

1.1.4 为什么学习Python

1. 易学、易读

Python关键字少、结构简单、语法清晰。这样就使得学习者可以在相对更短的时间内轻松上手。对初学者而言，可能感觉比较新鲜的东西可能就是Python 的面向对象特点了。那些还未能全部精通 OOP（Object OrientedProgramming，面向对象的程序设计）的人对径直使用Python还是有所顾忌的，但是OOP并非必须或者强制的。入门也是很简单的，你可以先稍加涉猎，等到有所准备之后才开始使用。

Python与其他语言显著的差异是，它没有其他语言通常用来访问变量、定义代码块和进行模式匹配的命令式符号。通常这些符号包括：美元符号（$）、分号（;）、波浪号（~）等等。没有这些符号，Python代码变得更加定义清晰和易于阅读。让很多程序员欣慰的是，不像其他语言，Python没有给你多少机会使你能够写出晦涩难懂的代码，而是让其他人很快就能理解你写的代码。如前所述，一门语言的可读性让它更易于学习。我们甚至可以说，即使对那些之前连一行Python代码都没看过的人来说，Python代码也是相当容易理解的。

2. 用途广泛

Python可以用来做网络爬虫。在制作网络爬虫方面，Python更为方便、快捷，这也正是如今Python被广泛使用的一大原因。并且在爬取的数据后，直接用Python进行对数据的解析处理也是十分方便。

Python可以用来做数据分析。现在迎来的是大数据时代。用数据发现问题、解决问题，是很多好公司的处世之道。他们深知，用户有时候会说假话，但是用户的行为不会说谎。数据可以说明一切问题，而Python语言由于其对数据挖掘的高效性，成为了数据分析师的第一首选语言。

Python可以应用于人工智能领域，当今人工智能领域展现出一片欣欣向荣的前景。而现在主流的人工智能开源框架，其实很多是Python完成的。另外Python和C/C++联系非常紧密，这使得Python在AI开发方面占据很大的优势：真正涉及到效率的，可直接通过Python调用底层的C/C++来完成。

此外Python还广泛应用于Web全栈开发、网络编程、游戏开发、Linux服务器、自动化运维、金融分析、科学运算等诸多领域中。如图1-3所示，Python的用途十分广泛。所以如果有这么一门语言即易学易懂，又应用广泛，如果让你选择，为什么不去学习它呢？

.. image:: /Chapter/picture/image004.jpg

图1-3 Python用途

1.1.5 Python的版本

Python有几种不同版本的实现方式，因为各种版本都在不断的迭代中，所以各种版本会定期发布更新。目前，有五种产品完备的、强大和稳定的主流Python实现：
CPython是常规的老版本Python，也是我们通常所称的Python。它既是编译器也是解释器，有自己的一套全部用标准C语言编写的标准程序包和模块。该版本可以直接用于所有流行的开发平台。大多数的Python第三方程序包和库与此版本兼容。

PyPy是Python实现的一个更快实现，它使用JIT编译器来使代码运行速度比CPython实现的速度更快——有时提供达10-100倍的加速。PyPy还有更高的内存效率，支持greenlet和stackless从而具有高并行性和并发性。

Jython是Java平台的Python实现，它支持Java虚拟机（Java Virtual
Machine，JVM），适用于任何版本的Java（版本最好是7以上）。通过使用Jython，你可以用所有类型的Java库、包和框架来编写代码。当你更多地了解Java语法和Java中广泛使用的OOP原则（如类、对象和接口）时，使用Jython的效果最好。

IronPython是流行的Microsoft
.NET框架的Python实现，也称为通用语言运行时（Common Language
Runtime，CLR）。你可以使用IronPython中的所有Microsoft
CLR库和框架，即使你实质上并不需要在C＃中编写代码，它也有助于你更多地了解C＃的语法和构造，以有效地使用IronPython。

MicroPython是 Python语言的精简高效实现
，可以让您的代码轻松运行在单片机或嵌入式系统，除了一系列核心Python库之外，MicroPython提供了访问硬件和操作底层设备的驱动库，实现了在单片机或嵌入式系统的Python快速开发。

默认的Python版本，即CPython实现，只有当你真的有兴趣与其它语言（如C＃和Java）进行接口并需要在代码库中使用它们时，才建议去尝试其它版本。

除了实现的不同之外，Python程序还有两个不同的版本：Python
2.x和较新的Python
3.x，它们是非常相似的，但是在3.x版本中出现了几个向后不兼容的变化，这导致在使用2.x的人和使用3.x的人之间产生了巨大迁移。PyPI上的大多数遗留代码和大部分的Python包都是在Python
2.7.x中开发的，因为所需的工作量不会很小，许多程序包的所有者没有时间或意愿将其将所有代码库移植到Python
3.x。

如果你的系统安装了这两个版本，请使用Python
3.x；如果没有安装Python，请安装Python 3.x；如果只安装了Python
2.x，也可直接使用它来编写代码，但还是尽快升级到Python
3.x为好，因为这样你就能使用最新的Python版本了。

1.2 搭建软件编程环境
--------------------

Python是一种跨平台的编程语言，这意味着它能够运行在所有主要的操作系统中。在所有安装了Python的计算机上，都能够运行你编写的任何Python程序。当然在不同的操作系统中，安装Python的方法存在细微的差别。

1.2.1 安装Python并使用交互式解释器

具体的安装步骤视使用的操作系统和安装方式而异，但最简单的方法是访问www.python.org，其中有下载页面的链接。安装过程非常简单，不管你使用的是Windows、macOS、Linux/UNIX还是其他操作系统，只需单击链接就可访问相应的最新版本。如果你使用的是Windows或Mac，将下载一个安装程序，可通过运行它来安装Python。如果你使用的是Linux/UNIX，将下载到源代码压缩文件，需要按说明进行编译，但通过使用Homebrew、APT等包管理器，可简化安装过程。

安装Python后，尝试启动交互式解释器。要从命令行启动Python，只需执行命令python。如果同时安装了较旧的版本，可能需要执行命令python3。启动Python后，可看到类似于下面的提示符：

>>> Python 3.6.4 (default, Jul 8 2017, 04:57:36)
[GCC 4.2.1 Compatible Apple LLVM 7.0.0 (clang-700.1.76)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
Python提供了交互式的解释器，可以尝试像下面这样做：
>>> print("Hello, world!")
等你按下回车键后，将出现如下输出：
>>> Hello, world!

上面的 >>> 是 Python提示符（prompt）。提示符是程序等待你键入信息时显示的符号。这个 >>> 提示符就是在告诉你，Python已经准备好了，在等着你键入Python指令，你输入print("Hello,world!")并按回车键，Python解释器将打印字符串"Hello,world!"，然后再次显示提示符，这种交互式的解释器方便我们了解程序的执行状态及各个变量的当前值，它可以提供交互环境实时运行程序，这样就可以在编程时实时测试，来发现问题解决问题。

1.2.2 集成开发环境

那么除了上面介绍的这种交互的方式在shell或者命令提示符下运行，Python有没有自己的集成开发环境呢？答案是有，而且有很多，Python就自带了一个IDLE，界面如图1-4所示。

.. image:: /Chapter/picture/image005.png

图1-4 IDLE界面

另一个交互式的开发环境是IPython，它的交互界面如图1-5所示所示，IPython是一个增强的Python交互shell，它拥有很多有趣的特性包括交互式的输入与输出，可使用shell命令，增强的调试和许多其它特性。

.. image:: /Chapter/picture/image006.png

图1-5 IPython界面

在IPython项目的基础上，又产生了Jupyter
notebook，界面如图1-6所示，notebook 的工作方式是，将来自 Web
应用（你在浏览器中看到的 notebook）的消息发送给 IPython
内核（在后台运行的 IPython 应用程序）。内核执行代码，然后将结果发送回
notebook。

Jupyter
notebook是基于Web技术的交互式计算文档格式，支持Markdown和Latex语法，支持代码运行、文本输入、数学公式编辑、内嵌式画图和其他如图片文件的插入，是一个对代码友好的笔记本。

.. image:: /Chapter/picture/image007.jpg

.. image:: /Chapter/picture/image008.png

图1-6 Jupyter notebook界面

最后真正称得上IDE的是PyCharm和Spyder，PyCharm是由JetBrains打造的一款Python IDE。它的运行界面如图1-7所示。我们知道VS2010的重构插件Resharper就是出自JetBrains。那么，PyCharm有什么吸引人的特点呢？首先，PyCharm用于一般IDE具备的功能，比如，调试、语法高亮、Project管理、代码跳转、智能提示、自动完成、单元测试、版本控制等等，另外PyCharm还提供了一些很好的功能用于Django 开发，同时支持Google AppEngine，支持IronPython。

.. image:: /Chapter/picture/image009.png

.. image:: /Chapter/picture/image010.png

图1-7 PyCharm界面

Spyder是Python(x,y)的作者为它开发的一个简单的集成开发环境。和其他的Python开发环境相比，它最大的优点就是模仿MATLAB的“工作空间”的功能，可以很方便地观察和修改数组的值。

Spyder的界面由许多窗格构成，如图1-8所示。用户可以根据自己的喜好调整它们的位置和大小。当多个窗格出现在一个区域时，将使用标签页的形式显示。例如在图1-7中，可以看到“Editor”、“Objectinspector”、“Variable explorer”、“File explorer”、“Console”、“History
log”以及两个显示图像的窗格。在View菜单中可以设置是否显示这些窗格。

.. image:: /Chapter/picture/image011.png

.. image:: /Chapter/picture/image012.jpg

图1-8 Spyder界面

1.3 认识skids硬件开发环境
-------------------------

除了以上的软件开发环境，Python也可以在硬件上运行，Skids就是一个Python可运行的硬件开发板。Skids是由沈阳牛艾科技有限公司自主研发的、高度集成的、用于教学领域的手持智能终端，采用高性能单片机系统做为控制核心，集成了Python开发环境和硬件支撑库，可以让Python编程教学变得更简单提高学生的学习兴趣，同时也降低物联网、嵌入式、软件工程、电子工程、通信等各类专业的教学入门难度。

1.3.1 Skids的硬件配置

Skids开发板的处理器为双核32位MCU，主频高达230MHz，计算能力可达600DMIPS，集成了WIFI和蓝牙功能；并可以扩展支持Zigbee协议，如图1-9所示正面搭配了2.8寸高清液晶屏，在屏幕下方集成了4个用户按键，在屏幕右侧提供了Micro
USB接口，可以很方便的与PC连接，在开发板右下角提供了3.5mm音频接口，在开发板背面右侧中间位置提供了TF卡插槽，支持TF卡，在背面预留了电池接口，因此Skids支持两种方式的供电，通过USB接口供电和采用电池供电，学习或开发过程，推荐使用USB接口来供电，开发板独特的电源管理和低功耗技术确保设备适用于各种物联网应用场景。

.. image:: /Chapter/picture/image013.jpg 
.. image:: /Chapter/picture/image014.jpg

图1-9 Skids开发板

1.3.2 Skids连接PC

Skids无需额外的调试器， Skids开发板的Micro
USB接口在侧面如图1-10所示，通过USB线连接至PC即可。

.. image:: /Chapter/picture/image015.jpg
.. image:: /Chapter/picture/image016.jpg

图1-10 Skids的Micro USB接口

Skids通过USB线连接至PC后，如图1-11所示开启电源开关（向上拨开关），设备上电启动，屏幕点亮。

.. image:: /Chapter/picture/image017.jpg
.. image:: /Chapter/picture/image018.jpg

图1-11 Skids电源开关

Skids连接至PC后，会自动进行驱动安装，无需人为操作，安装完驱动后，在设备管理器中会出现相应的串口，如图1-12所示。

.. image:: /Chapter/picture/image019.jpg

图1-12 PC显示的串口信息

1.3.3 Skids开发环境

Skids集成了Python解释器和驱动库，开发简单、使用方便，无需搭建复杂的交叉开发环境，就可实现快速入门，Skids只需要一个名为uPyCraft的工具即可进行代码编辑、下载和运行uPyCraft是一个可运行在Windows/MacOS平台的PythonIDE，界面简洁，操作便利，适合新手的学习和使用。uPyCraft内置了许多基础操作库，为众多的Python爱好者提供了一个简单实用的集成开发环境。

uPyCraft的下载地址：

https://raw.githubusercontent.com/DFRobot/uPyCraft/master/uPyCraft.exe

uPyCraft为绿色版软件，直接运行即可，无需安装，uPyCraft使用monaco编程字体，如果系统中没有这个字体，会弹出对话框提示安装，如图1-13所示，点击OK进行安装字体库或者选择Cancel取消安装均可。

.. image:: /Chapter/picture/image020.jpg

图1-13 monaco编程字体

uPyCraft的主界面共包含了5个区域：菜单栏、目录树、编辑区、终端框和工具栏。如图1-14所示。目录树在整个界面的左侧，可以通过不同的文件目录来管理文件，包括目录device，sd，uPy_lib，workSpace等。其中：

device：显示已连接上的开发板上存在的文件。

sd：目前版本尚未支持。

uPy_lib：显示IDE自带的库文件。

workSpace：用户自定义目录，保存用户自己的文件。

.. image:: /Chapter/picture/image021.jpg

图1-14 uPyCraft界面

终端框在界面的下方，用于命令行的执行，显示程序执行的信息，显示提示信息，如果有错误则显示错误信息等 。终端框相当于远程登录到了Skids上，可以在里面输入代码来直接运行，如图1-15所示。

.. image:: /Chapter/picture/image022.jpg

图1-15 终端显示界面

菜单栏在界面的上方，包含了uPyCraft的所有操作。编辑区域主要用于代码编辑，用户在这个区域中可以编辑修改文件，一般源程序的编辑及修改都在这个窗口完成。这个区域顶部是文件标签，显示当前打开了哪些文件，将鼠标停留在文件名上可以查看它的保存位置。在编辑窗口点击鼠标右键可对文件内容进行复制，粘贴等操作，工具栏在界面的最右侧，提供最常用的快捷操作以便于用户使用。

1.4 第一个Python程序
--------------------

在安装完开发环境之后，我们开始第一个Python程序的编写，学习编程的第一个程序都是Hello World，因为计算机科学家Brian W. Kernighan和C语言之父的Dennis M.Ritchie合著的《The C ProgrammingLanguage》(C程序设计语言)中使用它做为第一个演示程序，非常著名，所以后来的程序员在学习编程或进行设备调试时延续了这一习惯。那么在开始我们第一个程序之前先来学习一下交互式命令行及其基本操作。

1.4.1 Skids的交互命令行REPL

REPL意为读取-求值-打印-循环（Read Evaluate Print
Loop），是Python的交互式命令行，Skids通过USB线连接到电脑后，打开uPyCraft，主界面下部的终端框即为REPL，如图1-16所示。目前说来，调试和测试代码的最简便方法即使用REPL。

.. image:: /Chapter/picture/image023.jpg

图1-16 REPL界面

REPL是一个命令行形式的用户操作界面，类似Windows或Linux的命令行。RPEL的>>>箭头为命令输入提示符，此处表示您应在该提示符后输入命令或文本，在命令行中键入的任何内容都将在您点击Enter键后执行，如图1-17所示，即运行您输入的代码并打印出结果（若存在结果）。若输入的内容有误，则将打印错误信息。

.. image:: /Chapter/picture/image024.jpg 
.. image:: /Chapter/picture/image025.jpg

图1-17 正常和错误提示

1.4.2 REPL基本操作

编辑行：可使用左右箭头移动光标、删除键和退格键来编辑输入的当前行。可以点击Home键或按下Ctrl+A组合键来将光标移到行的开始，点击End键或按下Ctrl+E组合键将光标移到行的末尾。

输入历史：REPL储存您输入的前几行文本（在ESP32上可达8行）。可使用上下箭头键来召回之前输入的内容。

Tab补齐：点击Tab键将自动补齐正在输入的当前字。这对查找模块或对象的函数很有帮助。可尝试输入”ma”并点击Tab键，则会自动将其补齐为”machine”（假设已经输入了importmachine）。然后输入”.”，再次点击Tab键即可显示machine模块的所有函数的列表。

粘贴模式：按下Ctrl+E组合键将进入特殊的粘贴模式。这允许将文本块复制并粘贴到REPL。按下Ctrl+E组合键，如图1-18所示将看到粘贴模式提示。

.. image:: /Chapter/picture/image026.jpg

图1-18 粘贴提示

现在可粘贴（或输入）文本了。注意：任何特殊键或指令都无法再粘贴模式下运行（例如Tab或退格键）。复制完成后，按下Ctrl+D组合键以结束文本输入并执行粘贴文本。

其他控制指令：按下Ctrl+A组合键可进入原始REPL模式。这一模式类似于永久粘贴模式，只是字符不会回显。按下Ctrl+B组合键可开启常规REPL模式。按下Ctrl+C组合键取消所有输入，或中断当前运行代码。按下Ctrl+D组合键会启动软复位。

换行和自动缩进：输入的某些内容可能需要换行，即需要更多的文本行来创建适当的Python语句。此时提示符将从>>>变为…，如图1-19所示，光标将自动缩进正确数量，可直接开始输入下一行。

.. image:: /Chapter/picture/image027.jpg

图1-19 换行和缩进

连续三次输入Enter键，即可完成复合语句，返回到>>>提示符，如图1-20所示；完成复合语句的另一方式为点击退格键回到行的起始处，再点击Enter键；若要忽略所有的输入，直接按下Ctrl+C组合键即可。

.. image:: /Chapter/picture/image028.jpg

图1-20 返回提示符

输入Help()，则会显示Skids的帮助信息，如图1-21所示。

.. image:: /Chapter/picture/image029.jpg

图1-21 帮助信息

1.4.3 运行Hello World

那么对于Hello World这种小程序或者进行代码调试与验证，我们就在终端框中用REPL的方式来执行。在uPyCraft的终端框上输入语句，如图1-22所示。

.. image:: /Chapter/picture/image030.jpg

图1-22 uPyCraft的Hello wWorld

可以直接看到程序的执行结果如图1-23所示。

.. image:: /Chapter/picture/image031.jpg

图1-23 HellowWorld运行结果

程序对变量a进行赋值，并打印a，可以看到屏幕打印出Hello World这些字符，说明程序执行成功，大多数程序都可以直接在终端框中用REPL的方式来执行，但需要解决的问题比较复杂时，你可能需要编写.Py文件，将文件下载到开发板上执行。

1.3.4 Skids运行Python文件

如果要执行Skids上的某个Python文件，选中该文件后，点击鼠标右键，在弹出菜单中选择Run，即可执行该文件，如图1-24所示。

.. image:: /Chapter/picture/image032.jpg

图1-24 uPyCraft运行程序

如果要执行PC本地的某个Python文件，选中该文件后，点击右侧工具栏的DownloadAndRun按钮即可，如图1-25所示main.py文件将被下载到Skids并执行；在Device列表中可以看到main.py文件（因为已经被下载Skids开发板上）。

.. image:: /Chapter/picture/image033.jpg

图1-25 uPyCraft下载并运行程序

如果要执行PC本地的某个Python文件，选中该文件后，也可以直接将文件拖拽至device列表中，则该文件会被自动下载到Skids，然后在device的文件列表中，选中该文件，在鼠标右键的弹出菜单中选择Run即可执行该文件，如图1-26所示。如果终止正在运行的Python程序，则点击右侧工具栏的Stop按钮即可。

.. image:: /Chapter/picture/image034.jpg

图1-26 uPyCraft终止运行程序

另外在代码编辑完后可以点击工具栏的SyntaxCheck按钮对程序进行语法检查（注意：只会检查语法，不会对程序逻辑做检查），如图1-27所示，并可在终端框中看到打印信息。

.. image:: /Chapter/picture/image035.jpg

图1-27 uPyCraft语法检查

如果程序语法正确，则终端框中只打印“syntax finish”信息，如图1-28所示，否则还会打印出错误信息。

.. image:: /Chapter/picture/image036.jpg

图1-28 uPyCraft语法正确的显示信息

1.5 固件烧录和程序的自动执行
----------------------------

固件(Firmware)是指设备内部保存的设备“驱动程序”，通过固件，系统才能按照标准的设备驱动实现特定机器的运行动作，比如光驱、刻录机等都有内部固件。固件是担任着一个系统最基础最底层工作的软件。而在硬件设备中，固件就是硬件设备的灵魂，因为一些硬件设备除了固件以外没有其它软件组成，因此固件也就决定着硬件设备的功能及性能。

烧录的意思是将一些嵌入式启动所必须的硬件下载到嵌入式的储存设备中，当这些固件烧录到储存器中，板子下次启动的时候，直接从这些储存器中找到这些文件，嵌入式系统就能够直接跑起来。

1.5.1 uPyCraft访问Skids设备

要想对Skids进行固件烧录，首先要有烧录的软件工具，uPyCraft就为我们提供了固件烧录的功能，那么烧录之前先要让uPyCraft连接到Skids设备，具体的步骤如下：

1. 通过USB将Skids连接到PC。

2. 在uPyCraft的主菜单上，选择Tool s->
Serial，如图1-29所示，选中对应的串口即可。

.. image:: /Chapter/picture/image037.jpg

图1-29 uPyCraft的主菜单

3. 连接成功后，串口号前面会出现一个对号。

4.
同时，在左侧目录树中的Device选项，前面会出现小箭头，如图1-30所示，点击可显示Skids中的文件列表。

.. image:: /Chapter/picture/image038.jpg
.. image:: /Chapter/picture/image039.jpg

图1-30 uPyCraft连接成功

1.5.2 Skids固件烧录

为了确保Skids正常运行，需要为Skids烧录固件，Skids出厂时会统一烧录固件。但如果升级或者修复固件，则需要通过uPyCraft重新为Skids烧录固件，Skids的固件为二进制文件，通常命名为firmware.bin。具体烧录过程如下：

1. 在uPyCraft 的主菜单上，选择Tools-> BurnFireware，如图1-31所示。

.. image:: /Chapter/picture/image040.jpg

图1-31 uPyCraft烧录菜单

2. 烧录固件对话框将被弹出，在burn_addr选项中选择0x1000，在Firmware Choose选项中选中Users，如图1-32所示，点击Choose按钮，从本地目录中选择要烧录的firmware.bin固件。

.. image:: /Chapter/picture/image041.jpg

图1-32 uPyCraft烧录对话框

3.选中待烧录的固件后，点击OK将开始烧录固件，并弹出如下窗口显示进度，如图1-33所示。

.. image:: /Chapter/picture/image042.jpg

图1-33 uPyCraft烧录进度条

4.固件烧录完成后，该窗口自动关闭，返回uPyCraft主界面；同时，Skids设备将自动重启。

5. Skids重启后会与uPyCraft断开连接，用户重新在主菜单Tool s->
Serial中选择对应的串口进行连接。

1.5.3 程序开机自动执行

我们先来了解一下Skids的文件结构：

boot.py
：开发板启动时将执行这个该脚本，通常在该脚本中设置开发板的主要参数。

main.py
：python主程序的脚本文件，在boot.py运行后被执行。如果main.py不存在，则boot.py执行完成后，MCU处于空闲状态。

其它Python文件 ：python程序文件，由main.py调用运行或者通过uPyCraft手动运行。

假定Skids开机后要自动执行snake.py这个贪吃蛇游戏程序，就需要将文件命名为main.py，那么选择Device列表中的snake.py，在鼠标右键弹出菜单中选择Rename，在弹出的对话框中将文件名改为main.py，如图1-34所示。

.. image:: /Chapter/picture/image043.jpg
.. image:: /Chapter/picture/image044.jpg

图1-34 uPyCraft文件重命名

然后点击OK，关闭Skids电源开关，再打开Skids电源开关，重启启动Skids，贪吃蛇游戏就会自动运行，如图1-35所示。

.. image:: /Chapter/picture/image045.jpg

图1-35 开机运行贪吃蛇游戏

1.6 本章小结
------------

在本章节中，主要介绍了Python语言的起源和特点，学习Python的意义，Python的传统的软件学习环境的搭建。

并特别介绍了硬件学习Python的方式，认识了Skids开发板的结构、Skids的开发环境及配套的uPyCraft的使用方法，用REPL方式完成了第一个Python程序Hello
World。

在最后我们了解了固件的概念，及如何向开发板烧录新的固件，并学习了Skids的文件结构。学会设置自动运行了一个游戏程序。

本章的学习是后续课程的基础，在后续章节我们将通过各种有趣的硬件游戏来学习Python语言的相关知识，并通过动手操作学会编程的基本思想。

1.7 练习题目
------------

1. 什么是解释型语言？什么是编译型语言？两者有什么区别？

2. 对Skids进行新固件的烧录。

3. 在Skids上，通过新增.py文件来写一个Python程序，并运行该程序。

4. 将一个Python程序设置为在Skids启动后自动执行。

5. 将一个本地的Python程序文件传到Skids设备上，并运行该程序。
