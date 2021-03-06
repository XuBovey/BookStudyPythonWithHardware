第2章 Python画国旗
=========

2.1 认识turtle库
----------------


turtle是Python内置的一个比较有趣味的模块，俗称海龟绘图，它是基于tkinter模块打造，提供一些简单的绘图工具，海龟作图最初源自20世纪60年代的Logo编程语言，之后一些很酷的Python程序员构建了turtle库，让其他程序员只需要在代码头部加入importturtle，就可以在Python中使用海龟作图。由于在SKIDS开发板下开发实际是一种嵌入式开发，所以SKIDS固件在turtle的包的基础上进行了针对ESP32微控制器的命令封装，屏蔽掉了硬件的环节，使开发人员可以像在PC机那样调用turtle库，从而实现对LCD液晶显示器的绘图。

在海龟作图中，我们可以编写指令让一个虚拟的（想象中的）海龟在屏幕上来回移动。这个海龟带着一只钢笔，我们可以让海龟无论移动到哪都使用这只钢笔来绘制线条。通过编写代码，以各种很酷的模式移动海龟，我们可以绘制出令人惊奇的图片。使用海龟作图，我们不仅能够只用几行代码就创建出令人印象深刻的视觉效果，而且还可以跟随海龟看看每行代码如何影响到它的移动。这能够帮助我们理解代码的逻辑。所以海龟作图也常被用作新手学习Python的一种方式。

2.1.1 画布(canvas)

画布就是turtle为我们展开用于绘图区域，我们可以设置它的大小和初始位置。常用的设置画布参数的方法有两个：turtle.screensize()和turtle.setup()

第一个方法是：turtle.screensize(canvwidth=None, canvheight=None,bg=None)，参数分别为画布的宽(单位像素), 高, 背景颜色。

【案例2-1】 设置画布
::

   turtle.screensize(800,600, "green")
   turtle.screensize() #返回默认大小(400, 300)
   
另外一个设置的方法是turtle.setup(width=None,
height=None,startx=None,starty=None)，参数：width, height:
输入宽和高为整数时，表示像素。为小数时，表示占据电脑屏幕的比例。(startx,
starty)这一坐标表示矩形窗口左上角顶点的位置，如果为空，则窗口位于屏幕中心。
::

   turtle.setup(width=0.6,height=0.6)
   turtle.setup(width=800,height=800, startx=100, starty=100)

2.1.2 画笔

1. 画笔的状态

在画布上，默认有一个坐标原点为画布中心的坐标轴，坐标原点上有一只面朝x轴正方向小乌龟。这里我们描述小乌龟时使用了两个词语：坐标原点(位置)，面朝x轴正方向(方向)，turtle绘图中，就是使用位置方向描述小乌龟(画笔)的状态。

2. 画笔的属性

画笔的属性有颜色、画线的宽度等。

1) turtle.pensize()：设置画笔的宽度；
2) turtle.pencolor()：这里可以有参数也可以没有，如果没有参数传入，返回当前画笔颜色，如果传入参数设置画笔颜色，可以是字符串如"green"，"red"，也可以是RGB 3 元组。

3. 绘图命令

操纵海龟绘图有着许多的命令，这些命令可以划分为3种：一种为画笔运动命令，如表2-1所示；一种为画笔控制命令，如表2-2所示；还有一种是全局控制命令。如表2-3所示。

表2-1 画笔运动命令

+-----------------------------------+-----------------------------------+
| **命令**                          | **解释**                          |
+-----------------------------------+-----------------------------------+
| turtle.forward(distance)          | 向当前画笔方向移动distance像素长度 |
+-----------------------------------+-----------------------------------+
| turtle.backward(distance)         | 向当前画笔相反方向移动distance像素长度 |
+-----------------------------------+-----------------------------------+
| turtle.right(degree)              | 顺时针移动degree°                 |
+-----------------------------------+-----------------------------------+
| turtle.left(degree)               | 逆时针移动degree°                 |
+-----------------------------------+-----------------------------------+
| turtle.pendown()                  | 将笔落下使移动时绘制图形          |
+-----------------------------------+-----------------------------------+
| turtle.goto(x,y)                  | 将画笔移动到坐标为x,y的位置       |
+-----------------------------------+-----------------------------------+
| turtle.penup()                    | 提起笔移动，不绘制图形，用于另起一个地方绘制 |
+-----------------------------------+-----------------------------------+
| turtle.circle()                   | 画圆，半径为正(负)，表示圆心在画笔的左边(右边)画圆 |
+-----------------------------------+-----------------------------------+
| setx( )                           | 将当前x轴移动到指定位置           |
+-----------------------------------+-----------------------------------+
| sety( )                           | 将当前y轴移动到指定位置           |
+-----------------------------------+-----------------------------------+
| setheading(angle)                 | 设置当前朝向为angle角度           |
+-----------------------------------+-----------------------------------+
| home()                            | 设置当前画笔位置为原点，朝向东。  |
+-----------------------------------+-----------------------------------+
| dot(r)                            | 绘制一个指定直径和颜色的圆点      |
+-----------------------------------+-----------------------------------+

表2-2 画笔控制命令

+-------------------------------+-------------------------------------------+
| **命令**                      | **解释**                                  |
+-------------------------------+-------------------------------------------+
| turtle.fillcolor(colorstring) | 绘制图形的填充颜色                        |
+-------------------------------+-------------------------------------------+
| turtle.color(color1, color2)  | 同时设置pencolor=color1, fillcolor=color2 |
+-------------------------------+-------------------------------------------+
| turtle.filling()              | 返回当前是否在填充状态                    |
+-------------------------------+-------------------------------------------+
| turtle.begin_fill()           | 准备开始填充图形                          |
+-------------------------------+-------------------------------------------+
| turtle.end_fill()             | 填充完成                                  |
+-------------------------------+-------------------------------------------+
| turtle.hideturtle()           | 隐藏画笔的turtle形状                      |
+-------------------------------+-------------------------------------------+
| turtle.showturtle()           | 显示画笔的turtle形状                      |
+-------------------------------+-------------------------------------------+

表2-3 全局控制命令

+--------------------+------------------------------------------------+
| **命令**           | **解释**                                       |
+--------------------+------------------------------------------------+
| turtle.clear()     | 清空turtle窗口，但是turtle的位置和状态不会改变 |
+--------------------+------------------------------------------------+
| turtle.reset()     | 清空窗口，重置turtle状态为起始状态             |
+--------------------+------------------------------------------------+
| turtle.undo()      | 撤销上一个turtle动作                           |
+--------------------+------------------------------------------------+
| turtle.isvisible() | 返回当前turtle是否可见                         |
+--------------------+------------------------------------------------+
| stamp()            | 复制当前图形                                   |
+--------------------+------------------------------------------------+

2.2 用海龟画线和圆
------------------

.. image:: /Chapter/picture/image047.jpg

图2-1 海龟画正方形

2.2.1 画线

利用海龟画线，首先要明确几个问题：抬笔和落笔、画笔颜色、画笔速度、起始位置、画笔初始方向、画线的长度以及如何转向等。例如，利用海龟绘图画一个正方形，边长100像素，左上角是坐标原点，如图2-1所示。

1. 函数原型：penup( )

功能说明：抬起笔，海龟移动时没有绘图。

参数说明：无。

2. 函数原型：pendown( )

功能说明：落下笔，海龟移动时有绘图。

参数说明：无。

3. 函数原型：speed(s)

功能说明：设置海龟移动的速度为 0..10
表示的整型数值。如未指定参数则返回当前速度。

参数说明：一个 0..10 范围内的整型数或速度字符串，速度值从 1 到
10，画线和海龟转向的动画效果逐级加快。注意：speed= 0
表示没有动画效果。字符串与整形数的对应关系如表2-4所示。

表2-4 speed( )速度值

+------------+------------+----------+
| **字符串** | **整型数** | **效果** |
+------------+------------+----------+
| ‘fastest’  | 0          | 最快     |
+------------+------------+----------+
| ‘fast’     | 10         | 快       |
+------------+------------+----------+
| ‘normal’   | 6          | 正常     |
+------------+------------+----------+
| ‘slow’     | 3          | 慢       |
+------------+------------+----------+
| ‘slowest’  | 1          | 最慢     |
+------------+------------+----------+

【案例2-2】 设置画笔速度。

>>> turtle.speed()
3
>>> turtle.speed('normal')
>>> turtle.speed()
6
>>> turtle.speed(9)
>>> turtle.speed()
9

4. 函数原型：goto\ *(*\ x, y=None)

功能说明：海龟移动到一个绝对坐标。如画笔已落下将会画线，不改变海龟的朝向。

参数说明：x：一个数值或数值对/向量；y：一个数值或 None,如果 y 为 None，x 应为一个表示坐标的数值对或类对象(例如 pos()返回的对象)。

【案例2-3】 设置画笔移动到一个绝对位置。

>>> turtle.goto(60,30)
>>> turtle.pos()
(60.00,30.00)

5. 函数原型：heading()

功能说明：返回海龟当前的朝向。

参数说明：无。

【案例2-4】 返回海龟当前的朝向。

>>> turtle.home()
>>> turtle.left(67)
>>> turtle.heading()
67.0

6. 函数原型：setheading(angle)

功能说明：设置海龟的朝向为 angle。

参数说明：angle: 一个角度数值
(整型或浮点型)，具体是顺时针或者逆时针取决于turtle.mode()的值，默认turtle.mode()=standard表示逆时针方向，logo表示顺时针，以下是以角度表示的几个常用方向如表2-5所示。

表2-5 角度设置

+--------------+--------------+
| **标准模式** | **logo模式** |
+--------------+--------------+
| 0-东         | 0-北         |
+--------------+--------------+
| 90-北        | 90-东        |
+--------------+--------------+
| 180-西       | 180-南       |
+--------------+--------------+
| 270-南       | 270-西       |
+--------------+--------------+

【案例2-5】 设置海龟当前的朝向。

>>> turtle.setheading(90)
>>> turtle.heading()
90.0

7. 函数原型：turtle.forward(distance)

函数功能：向正方向运动distance的距离。

参数说明：移动的距离。

函数原型：turtle. backward(distance)。

函数功能：向反方向运动distance的距离。

参数说明：移动的距离。

8. 函数原型：turtle.right(degree)

函数参数:degree：一个角度数值 (整型或浮点型)。

海龟右转degree个单位。(单位默认为角度，但可通过 degrees() 和 radians()
函数改变设置。角度的正负由海龟模式确定。

【案例2-6】 设置海龟运动距离。
::
   turtle.penup()
   turtle.goto(x,y)
   turtle.pendown()
   turtle.pencolor(color)
   turtle.setheading(0)
   turtle.forward(height)
   turtle.right(90)
   turtle.forward(height)
   turtle.right(90)
   turtle.forward(width)
   turtle.right(90)

2.2.2 画圆

函数原型：turtle.circle(radius\ *, *\ extent=None\ *, *\ steps=None)。

功能说明：绘制一个radius指定半径的圆。圆心在海龟左边radius个单位；extent为一个夹角，用来决定绘制圆的一部分。如未指定extent则绘制整个圆。如果extent不是完整圆周，则以当前画笔位置为一个端点绘制圆弧。如果radius为正值则朝逆时针方向绘制圆弧，否则朝顺时针方向。最终海龟的朝向会依据extent的值而改变。steps为边数，做半径为radius的圆的内切正多边形，多边形边数为steps，extent和step参数可有可无。

参数说明：radius：半径数值；extent：夹角数值 (或None)；steps：边数整型数
(或 None)。【案例2-7】 设置海龟画圆。

>>> turtle.home()
>>> turtle.position()
(0.00,0.00)
>>> turtle.heading()
0.0
>>> turtle.circle(50)
>>> turtle.position()
(-0.00,0.00)
>>> turtle.heading()
0.0
>>> turtle.circle(120, 180) # 画一个半圆
>>> turtle.position()
(0.00,240.00)
>>> turtle.heading()
180.0

2.3 如何上颜色
--------------

2.3.1 设置填充颜色

函数原型：turtle.fillcolor( )

功能说明：返回或设置画笔的颜色。在没有参数传入，返回当前画笔颜色，传入参数设置画笔颜色，可以是字符串如"green"，"red"，例如fillcolor("red")，也可以是RGB
3元组，例如fillcolor((255, 255, 210))或fillcolor(255, 255, 210)。

参数说明：参数可以为空，也可以是一个字符串，这个字符串应该是Tkinter控件中的颜色描述字符串，如"green"，"red"等；也可以是一个RGB的元祖，参数传入形式为fillcolor((r, g, b))，或者直接写成三个参数fillcolor(r, g, b)，色彩取值范围为0-255的整数或者0-1的小数，这取决于颜色模式。turtle.colormode(mode)，mode值可以为1.0，则RGB为小数模式，mode值可以为255，则RGB为整数模式。

2.3.2 颜色填充

函数原型：turtle.begin_fill( )

功能说明：在绘制要填充的形状之前调用，表示填充开始，下面的语句开始绘制形状。

参数说明：无参数。

函数原型：turtle.end_fill( )

功能说明：填充上次调用之后绘制的形状。

参数说明：无参数。

【案例2-8】 设置颜色填充。

>>> turtle.color("black", "red")
>>> turtle.begin_fill()
>>> turtle.circle(80)
>>> turtle.end_fill()

2.4 在开发板上画德国国旗
------------------------

2.4.1 预备知识

德国国旗长方形。旗面自上而下由黑、红、金三个平行相等的横长方形组成。黑红金为 民族所喜爱的颜色，在德国历史上都有着重要的意义，也常常获得不同的解释。最新的解释是：黑、红、金代表二战后的共和民主政体体制，也代表德国联邦和自由的联合体，这种自由不仅仅是德国的自由，还包含了德国人民的民主自由。

2.4.2 任务要求

1. 绘制德国国旗，如图2-2所示；

2. 国旗处在屏幕中间，德国国旗比例100:60=5:3；

3. 三个等高矩形，颜色是黑红金三色；

.. image:: /Chapter/picture/image048.jpg

图2-2 德国国旗

2.4.3 任务实施

1. 确定矩形坐标

如图2-3所示：德国国旗由三个矩形框组成，首先需要确定三个矩形框的左上角和右下角坐标，在这里，屏幕中心为坐标原点（0，0），同时，国旗处在屏幕的中心，所以，各点坐标为：

.. image:: /Chapter/picture/image049.png

图2-3 矩形坐标点

A: (-75,50)

B: (75,16)

C: (-75,16)

D: (75,-16)

E: (-75,-17)

F: (75,-50)

2. 填充三个矩形

首先，画矩形实际上是画四条直线，形成矩形。首先需要根据坐标知道第一个黑色矩形的长与宽，这里面利用一个abs()绝对值函数来进行计算，已经两个点A,B分别为左上角和右下角的坐标，那么矩形的宽度为abs(75-(-75))，这里面定义了一个变量width变量用于存储宽度。abs(75-(-75))。同理，黑色矩形的高度为abs(15-44)。并赋值给一个变量height=abs(15-44)。之后，依次进行画笔颜色设置，抬笔，移动海龟到起点处，设置默认海龟方向，设置填充颜色，画矩形，填充。代码如下：
::

   turtle.fillcolor(color)
   turtle.begin_fill()
   turtle.fd(width)
   turtle.right(90)
   turtle.forward(height)
   turtle.right(90)
   turtle.forward(width)
   turtle.right(90)
   turtle.forward(height)
   turtle.end_fill()

程序运行效果如图2-4所示。

.. image:: /Chapter/picture/image052.jpg 
.. image:: /Chapter/picture/image053.jpg
.. image:: /Chapter/picture/image054.jpg
图2-4 绘图效果

3. 改进

在上面的程序中，需要重复画三个矩形，代码显得过于笨拙。可以定义一个画矩形的函数，然后三次调用这个函数，传入相应的参数，就可以实现画国旗了。关于函数的详细介绍，会在后面章节中体现。函数定义如下：
::

   def rect(x, y, color, x2, y2):
      width = abs(x2 - x)
      height = abs(y2 - y)
      turtle.pencolor(color)
      turtle.penup()
      turtle.goto(x,y)
      turtle.pendown()
      turtle.setheading(0)
      turtle.fillcolor(color)
      turtle.begin_fill()
      turtle.fd(width)
      turtle.right(90)
      turtle.forward(height)
      turtle.right(90)
      turtle.forward(width)
      turtle.right(90)
      turtle.forward(height)
      turtle.end_fill()

定义好函数，只需要三次调用该函数，传入相应的坐标参数即可。
::

   rect(-75,50,'black',75,16)
   rect(-75,16,'red',75,-16)
   rect(-75,-17,'gold',75,-50)

4. 源程序设计
::

   import uturtle
   turtle = uturtle.Turtle() 
   def rect(x, y, color, x2, y2): 
      width =abs(x2 - x) 
      height = abs(y2 - y) 
      turtle.pencolor(color)
      turtle.penup() 
      turtle.goto(x,y) 
      turtle.pendown() 
      turtle.setheading(0)
      turtle.fillcolor(color) 
      turtle.begin_fill() 
      turtle.fd(width)
      turtle.right(90) 
      turtle.forward(height) 
      turtle.right(90)
      turtle.forward(width) 
      turtle.right(90) 
      urtle.forward(height)
      turtle.end_fill() 
   def germany(): 
      rect(-75,50,'black',75,16)
      rect(-75,16,'red',75,-16) 
      rect(-75,-17,'gold',75,-50) 
      turtle.reset()
      turtle.speed(0) 
      germany()

2.5 在开发板上画中国国旗
------------------------

2.5.1 预备知识

中华人民共和国国旗的设计者是曾联松来自浙江随着中国共产党 在解放战争中取得胜利，新政治协商会议筹备会在1949年7月发出了征集国旗图案的通告，曾联松设计并提交了他的国旗样稿。在2992幅应征国旗图案中，曾联松的设计被选入38幅候选草图。经过多次讨论和少量修改，他的设计被选为了新政权的国旗。

五星红旗旗面为红色，长宽比例为3:2。左上方缀黄色五角星五颗，四颗小星环拱在一颗大星的右面，并各有一个角尖正对大星的中心点，如图2-5所示。红色代表革命，及烈士的鲜血。黄色是为了在红地上显出光明。大五角黄星代表中国共产党，四颗小五角黄星代表中国人民的四个阶级：工人阶级、农民阶级、小资产阶级和民族资产阶级。四星环绕大星象征中国共产党领导下的革命人民大团结。

.. image:: /Chapter/picture/image055.jpg

图2-5 五星红旗

2.5.2 任务要求

1. 五星红旗长宽比例为3:2，长度为180像素，宽度为120像素；

2. 图中每个小格长宽为6个像素，各五角星的相对位置如图2-6所示；

3. 五星红旗底色为红色，星星为黄色；

4.
大五角星有一个角垂直向上，其它四个小五角星各有一个角对准大五角星中心；

.. image:: /Chapter/picture/image056.jpg

图2-6 参考坐标

2.5.3 任务实施

1. 确定五角星的坐标位置和半径

由于整个屏幕的长度和宽度分别为240和320像素，五星红旗的宽度和高度分别为180和120像素，并没有占满屏幕。变量width和变量height分别代表国旗的宽和高，变量pice代表图中的单位小格，将宽度30等分，每小格的宽为6像素。

所以具体设置为：
::

   width = 180 
   height = 120
   pice = width/30

在本项目中，屏幕中心点为坐标原点，而国旗处在屏幕的中心，所以国旗的中心点就是坐标原点，因此五颗星的坐标和半径分别为：
::

   A: (-width/3，height/4)，半径为pice*3。
   B: (-width/6，height*2/5)，半径为pice。
   C: (-width/10，height*3/10)，半径为pice。
   D: (-width/10，height*3/20)，半径为pice。
   E: (-width/6，height/20)，半径为pice。

2. 填充红色底色矩形框

画底色函数定义如下：

函数原型：draw_rect(x1, y1, color, x2, y2)。

参数说明：x1: 左上角横坐标。

y1: 左上角纵坐标。

x2: 右下角横坐标。

y2: 右下角纵坐标。

在该函数中，通过调用海龟绘图中的内置函数实现图形的绘制的。步骤如下：

1）计算国旗的宽度和高度的绝对值。
::

   width = abs(x2 - x1) 
   height = abs(y2 - y1)

2）抬笔，并移动到左上角位置，落笔。
::

   turtle.penup() 
   turtle.goto(x1,y1) 
   turtle.pendown()

3. 设置海龟初始方向

turtle.setheading(0)是海龟绘图中的内置函数，前面章节有详细介绍。0代表海龟头的方向向东。需要注意的是，海龟头的方向不会随着海龟移动发生变化，默认方向是向东，也就是说，即使海龟向南，北，西移动，海龟头也不会改变方向。如图2-7所示。

.. image:: /Chapter/picture/image057.png

图2-7 海龟头方向

4. 设置颜色

利用turtle.color(color1,color2)内置函数实现颜色的设置，两个参数分别代表画线颜色和填充颜色。

5. 画图并进行填充
::

   turtle.begin_fill() 
   for i in range(2): 
      turtle.forward(width)
      turtle.right(90) 
      turtle.forward(height) 
      turtle.right(90)
      turtle.end_fill()

6. 画五角星

画五角星通过调用以下函数来实现。
::

   def star(center_x, center_y, radius, big_center_x, big_center_y):
      turtle.penup() 
      turtle.goto(center_x, center_y) 
      turtle.pendown()
      turtle.left(turtle.towards(big_center_x,big_center_y)-turtle.heading())
      turtle.forward(radius) 
      turtle.right(90) 
      draw_star(turtle.pos().x,turtle.pos().y, radius, 'yellow')

首先，画大五角星需要确定五个顶点的坐标。计算坐标的方法是首先确定五角星中心，然后利用五角星中心和半径，每次画72度的圆弧，以此来确定各个顶点的坐标。由于大五角星有一个角是垂直向上的，因此，采用两个坐标的连线来确认起始画圆弧的角度。这两个坐标是：(big_center_x,
big_center_y-1)和(big_center_x,
big_center_y)，然后再利用turtle.circle(-radius,
72)内置函数，实现五个顶点坐标的确定。
::

   turtle.penup() 
   pt1=turtle.pos() 
   turtle.circle(-radius, 72)
   pt2=turtle.pos() 
   turtle.circle(-radius, 72) 
   pt3=turtle.pos()
   turtle.circle(-radius, 72) 
   pt4=turtle.pos() 
   turtle.circle(-radius,72) 
   pt5=turtle.pos()

然后，再绘制4个小五角星，在本项目中，要求每个小五角星有一个角指向大五角星中心，所以，同样需要利用两点连线坐标确认起始角度，然后利用turtle.circle(-radius,
72)函数确定五个顶点坐标，与大五角星同理。

7. 源程序设计
::

   import uturtle
   turtle = uturtle.Turtle()
   def draw_rect(x1, y1, color, x2, y2):
      width = abs(x2 - x1) 
      height = abs(y2 - y1) 
      turtle.penup()
      turtle.goto(x1,y1) 
      turtle.pendown() 
      turtle.setheading(0)
      turtle.color(color, color) 
      turtle.begin_fill() 
      for i in range(2):
      turtle.forward(width) 
      turtle.right(90) 
      turtle.forward(height)
      turtle.right(90) 
      turtle.end_fill()
   def draw_star(center_x, center_y,radius, color): 
         turtle.penup() 
         pt1=turtle.pos()
         turtle.circle(-radius, 72) 
         pt2=turtle.pos() 
         turtle.circle(-radius,72) 
         pt3=turtle.pos() 
         turtle.circle(-radius, 72) pt4=turtle.pos()
         turtle.circle(-radius, 72) 
         pt5=turtle.pos() 
         turtle.pendown()
         turtle.color(color, color) 
         turtle.begin_fill() 
         turtle.goto(pt3)
         turtle.goto(pt1) 
         turtle.goto(pt4) 
         turtle.goto(pt2) 
         turtle.goto(pt5)
         turtle.end_fill()
   def star(center_x, center_y, radius, big_center_x,big_center_y): 
         turtle.penup() turtle.goto(center_x, center_y)
         turtle.pendown() 
         turtle.left(turtle.towards(big_center_x,big_center_y) - turtle.heading()) 
         turtle.forward(radius)
         turtle.right(90) 
         draw_star(turtle.pos().x, turtle.pos().y, radius,'yellow')turtle.reset()
         turtle.speed(0)
         width = 180 height =120draw_rect(-width/2, height/2, 'red', width/2, -height/2)
         pice =width/30big_center_x = -width/3big_center_y =eight/4
         star(big_center_x, big_center_y-1, pice*3, big_center_x,big_center_y)
         star(-width/6, height*2/5, pice, big_center_x,big_center_y)
         star(-width/10,height*3/10,pice,big_center_x,big_center_y)
         star(width/10,height*3/20,pice,big_center_x,big_center_y)
         star(-width/6, height/20, pice, big_center_x,big_center_y)

8. 运行效果

程序运行效果如图2-8所示。

.. image:: /Chapter/picture/image058.jpg
.. image:: /Chapter/picture/image059.jpg
.. image:: /Chapter/picture/image060.jpg
图2-8 五星红旗运行效果

2.6 认识和使用变量
------------------

2.6.1 了解Python变量

与其他语言不同，PYTHON中定义变量不需要提前声明，创建时直接对其赋值即可，变量类型由赋给变量的值决定。一旦创建了一个变量，就需要给该变量赋值。变量好比一个标签，指向内存空间的一个特定的地址。创建一个变量时，在机器的内存中，系统会自动给该变量分配一块内存，用于存放变量值，如图2-9所示。

.. image:: /Chapter/picture/image061.png

图2-9 变量的存储

通过id函数可以具体查看创建变量和变量重新赋值时内存空间的变化过程，如下所示：

>>> x=19
>>> id(x)
504538784
>>> y=x
>>> id(y)
504538784
>>> y
19
>>> x=30
>>> id(x)
504539136
>>> y
19

从上面代码可以直观的看出，一个变量在初次赋值时就会获得一块内存空间来存放变量值。当令变量y等于变量x时，其实是一种内存地址的传递，变量y获得的是存储变量x值的内存地址，所以当变量x改变时，变量y并不会发生改变。此外还可以看出，变量x的值改变时，系统会重新分配另一块内存空间存放新的变量值。

要创建一个变量，首先需要一个变量名和变量值（数据），然后通过赋值语句将值赋给变量。

2.6.2 变量名

变量的命名必须严格遵守标识符的规则，python中还有一类非保留字的特殊字符串（如内置函数名），这些字符串具有某种特殊功能，虽然用于变量名时不会出错，但会造成相应的功能丢失。如len函数可以用来返回字符串长度，但是一旦用来作为变量名，其就失去了返回字符串长度的功能。因此，在取变量名时，不仅要避免phthon中的保留字，还要避开具有特殊作用的保留字，以避免发生一些不必要的错误，如下所示：

>>> import keyword
>>> keyword.iskeyword("and")
True

如果一段代码中有大量变量名，而且这些变量没有错，只是取名都很随意，风格不一，这样的解读代码时就会出现一些混淆，接下来几种命名法：

1. 大驼峰（upper camel case）

所有首字母都是大写，例如：“MyName,YourFamily”，大驼峰命名法一般用于类的命名。

2. 小驼峰（lower camel case）

第一个单词的首字母为小写字母，其余单词的首字母都采用大写字母，例如“my_Name,your_Family”等。

关于要使用哪种方法对变量命名，并没有统一的说法，重要的是一旦选择好了一种命名方式，在后续的程序编写过程中一定要保持风格一致。

2.6.3 变量值

变量值就是赋给变量的数据，Python中有6个标准的数据类型，分别为数值（Number）、布尔值（Boolean）、字符串（String）、列表（List）、元组(Tuple)、字典(Dictionary)。其中，列表、元组、字典、集合属于复合数据类型。

2.6.4 变量赋值

最简单的变量赋值就是把一个变量值赋给一个变量名，只需要用（=）就可以实现。同时，Python还可以将一个值同时赋给多个变量，如下所示：

>>> a=b=c=10
>>> a
10
>>> b
10
>>> c
10
>>> e,f,g=11,12,"hello"
>>> e
11
>>> f
12
>>> g
'hello'

2.7 数字与数据类型
------------------

Python的数据类型主要包括数值类型、布尔类型、字符串类型、列表类型、字典类型和元组类型，本节我们主要将前两种类型，其中数值类型又包括：整形、浮点型、复数三种类型。

2.7.1 整型

     
整数类型（int）简称整型，它用于表示整数，例如，-5、106等。整数字面值的表示方式有四种：分别是十进制、二进制、八进制、十六进制。各个表示方式开头有不同的前缀，如表2-6所示。

表2-6 数制及前缀

+----------+----------+----------+----------+
| **序号** | **进制** | **前缀** | **举例** |
+----------+----------+----------+----------+
| 1        | 十进制   | 无       | a = 30   |
+----------+----------+----------+----------+
| 2        | 二进制   | 0b       | a = 0b   |
+----------+----------+----------+----------+
| 3        | 八进制   | 0o       | a = 0o   |
+----------+----------+----------+----------+
| 4        | 十六进制 | 0x       | a = 0x   |
+----------+----------+----------+----------+

接下来，看一些整形的示例代码，具体如下：

>>> a=30
>>> type(a)
<class 'int'>
>>> bin(a)
'0b11110'
>>> oct(a)
'0o36'
>>> hex(a)
'0x1e'

上述代码中，第1行代码的变量a的值是一个十进制整数，它属于int型，它点在第2~3行中的代码中得到了验证。第4~5行代码输出a的值，结果是二进制的30，通过二进制转换函数bin()来完成。第6~7行代码输出a的值，结果是八进制的30，通过八进制转换函数oct()来完成。第8~9行代码输出a的值，结果是十六进制的30，通过十六进制转换函数hex()来完成。

Python的整数可以表示的范围是有限的，它和系统的最大位数相关，例如，32位机上的整型是32位，可以表示的范围是-2\ :sup:`31`\ ~2\ :sup:`31`-1。在64位机上的整数是64位的，可以表示的数的范围是-2\ :sup:`64`\ ~2\ :sup:`64`-1。

**注意：**\ long 类型只存在于 Python2.X 版本中，在 2.2 以后的版本中，int
类型数据溢出后会自动转为long类型。在 Python3.X 版本中 long
类型被移除，使用 int 替代。

2.7.2 浮点型

浮点型(float)可用于表示实数。例如：2.5、9.9都属于浮点型。浮点型字面值可以用十进制或科学计数法表示。Python中的科学计数法表示如下：

<实数>E或者e<整数>

其中，E或e表示基是10，后面的整数表示指数，指数的正负使用“+”或者“-”表示，其中，“+”可以省略。例如，3.14e5表示的是3.14×10\ :sup:`5`\ ，9.9e-2表示的是9.9×10\ :sup:`-2`\ 。

>>> 3.14e5
315000.0
>>> 9.9e-2
0.099

2.7.3 布尔型

布尔类型可以看作是一种特殊的整型，布尔型数据只有两个取值：True和False，分别对应整型的1和0。每一个Python对象都天生具有布尔值（True或False），进而可用于布尔测试。以下对象的布尔值都是False:

1. NONE

2. False（布尔型）

3. 0（整型0）

4. 0L（长整型0）

5. 0.0（浮点型0）

6. 0.0+0.0j（复数0）

7. ""（空字符串）

8. []（空列表）

9. ()（空元组）

10. {}（空字典）

2.7.4 复数类型

复数类型用于表示数学中的复数，例如，5+3j、-3.4-6.8j都是复数类型。Python中的复数类型是一般计算机语言所没有的数据类型，它有以下两个特点：

1.复数由实数部分和虚数部分构成，表示为real+imagj或real+imagJ。

2.复数的实数部分real和虚数部分imag都是浮点型。

>>> a=1+2j
>>> a
(1+2j)

.. _本章小结-1:

2.8 本章小结
------------

本章以画国旗为项目，首先讲了turtle海龟画图的背景，然后利用海龟画图完成了简单的做图操作，如画线，画圆，移动，颜色等。最后利用这些基础知识完成了德国国旗和中国五星红旗。最后讲述了PYTHON中变量和数据类型的相关知识，本章以项目为中心，以应用为导向，通过本章学习，读者将会在SKIDS开发板上实现国旗的显示。

.. _练习题目-1:

2.9 练习题目
------------

1 画法国国旗

要求：比例2:3，宽和高分别为：180和120像素。如图2-10所示：

.. image:: /Chapter/picture/image062.jpg

图2-10 法国国旗

2 画巴勒斯坦国旗

要求：比例1:2，宽和高分别为：180和90像素。如图2-11所示：

.. image:: /Chapter/picture/image063.jpg

图2-11 巴勒斯坦国旗
