第6章 贪吃蛇游戏制作
=========

6.1 认识列表
------------



Python中有一类基本的数据结构：序列。序列都可以进行索引，切片，加，乘，检查成员等操作。序列中的每个元素都具备一个索引，从0开始，依此类推。一个具备N个元素的序列，索引号从0到N- 1。Python中序列还可以细分成6个内置类型，列表就是其中之一。

列表是最常用的Python数据类型，它可以作为一个方括号内的逗号分隔值出现。与C语言中的数组不同，列表的数据项不需要具有相同的类型。创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：

>>> list1 = ['english', 'maths',99,85]
>>> list2 = [34,32,65,52,-9]
>>> print ("list1[0]: ", list1[0] )
list1[0]: english
>>> print ("list2[1:5]: ", list2[1:5])
list2[1:5]: [32, 65, 52, -9]

6.2 列表的遍历和操作
--------------------

6.2.1 访问列表中的值

列表使用下标索引来访问列表中的值，可以使用方括号的形式截取字符。

【案例6-1】 访问列表值

>>> list1 = ['english','maths',99,85]
>>> list2 = [34,32,65,52,-9]
>>> print("list1[0]",list1[0])
list1[0] english
>>> print(list2[1:3])
[32, 65]

需要注意的是，在使用list2[1:3]访问列表值时，中括号中的值是半闭半开的。

6.2.2 添加列表元素

列表的元素可以使用append()方法来添加。

【案例6-2】 添加列表元素

>>> list1 = ['english','maths',99,85]
>>> list1.append('france')
>>> print(list1)
['english', 'maths', 99, 85, 'france']

append()方法是在列表的末尾加入元素，如果想在列表的中间插入元素，就需要用到方法insert()，该方法有两个参数，第一个参数代表要插入元素的索引位置，第二个参数代表列表元素的值。如下示例：

>>> list1 = ['english','maths',99,85]
>>> print(list1)
['english', 'maths', 99, 85]
>>> list1.insert(1,'history')
>>> print(list1)
['english', 'history', 'maths', 99, 85]

6.2.3 删除列表元素

可以使用del语句来删除列表的元素。

【案例6-3】 删除列表元素

>>> list1 = ['english','maths',99,85]
>>> print(list1)
['english', 'maths', 99, 85]
>>> del list1[2]
>>> print(list1)
['english', 'maths', 85]

除了用del语句外，还可以用列表的方法remove()来删除列表元素，需要注意的是，使用remove()方法时，括号里面的参数不是列表元素的索引值，而是列表元素的实际值，否则会发生错误。

>>> list1 = ['english','maths',99,85]
>>> print(list1)
['english', 'maths', 99, 85]
>>> list1.remove(99)
>>> print(list1)
['english', 'maths', 85]

列表还有一个删除元素的方法是pop()，方法的参数同样是索引值，这里面举了一个负数的例子，负数的参数从右向左删除列表元素。如下示例：

>>> list1 = ['english','maths',99,85]
>>> print(list1)
['english', 'maths', 99, 85]
>>> list1.pop(-2)
99
>>> print(list1)
['english', 'maths', 85]

6.2.4 列表脚本操作符

列表有两个操作符“+”和“*”；“+”号用于组合列表，“*”号用于重复列表。

【案例6-4】 访问脚本操作符

>>> list1 = ['english','maths',99,85]
>>> list2 = [34,32,65,52,-9]
>>> list1 +list2
['english', 'maths', 99, 85, 34, 32, 65, 52, -9]
>>> list1 * 2
['english', 'maths', 99, 85, 'english', 'maths', 99, 85]

6.2.5 列表切片

切片操作需要提供起始索引位置和最后索引位置，然后用冒号 :
将两者分开。如果未输入步长，则默认步长为
1。切片操作返回一系列从起始索引位置开始到最后索引位置结束的数据元素。需要注意的是，起始索引位置的值包含在返回结果中，而最后索引位置的值不包含在返回结果中。

【案例6-5】 访问切片

>>> list1 = ['english','maths',99,85]
>>> print(list1[1:3])
['maths', 99]

切片也可以进行逆向切片，如下示例：

>>> list1 = ['english','maths',99,85]
>>> print(list1[-3:-1])
['maths', 99]

我们可以省略起始索引位置，表示从最开始进行切片，当我们将两个索引都省略之后，我们将按原样复制一个列表，如果想要将列表的顺序颠倒，则可以使用::-1。如下示例：

>>> list1 = ['english','maths',99,85]
>>> print(list1[:3])
['english', 'maths', 99]
>>> print(list1[:])
['english', 'maths', 99, 85]
>>> print(list1[::-1])
[85, 99, 'maths', 'english']

6.2.6 列表的遍历

列表的遍历方法有很多种，这里面介绍两种最常用的方法。

【案例6-6】 访问的遍历
::

   list = ['html', 'js', 'css', 'python']
   # 方法1
   print('遍历列表方法1：')
   for i in list:
      print ("序号：%s 值：%s" % (list.index(i) + 1, i))
      print ('\n遍历列表方法2：')
   # 方法2
   for i in range(len(list)):
      print("序号：%s 值：%s" % (i + 1, list[i]))

运行结果如下：
::

   遍历列表方法1：
      序号：1 值：html
      序号：2 值：js
      序号：3 值：css
      序号：4 值：python
   遍历列表方法2：
      序号：1 值：html
      序号：2 值：js
      序号：3 值：css
      序号：4 值：python

6.2.7 列表内置函数和方法

Python列表中包含以下函数，如表6-1所示：

表6-1 列表内置函数

.. image:: /Chapter/picture/image152.jpg

Python列表中包含以下内置方法，如表6-2所示：

表6-2 列表内置方法

.. image:: /Chapter/picture/image153.jpg

6.3 元组及使用
--------------

6.3.1 认识元组

Python的序列中还有一个常用的类型就是元组。元组与列表类似，不同之处在于元组的元素不能修改。元组使用小括号，列表使用方括号。元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可，也可以不用括号。如下所示：

>>> tup1 = ('english','maths',95,85)
>>> tup2 = (1,2,3,4,0,-8)
>>> tup3 = "a","b","c"
>>> tup1('english', 'maths', 95, 85)
>>> tup2
(1, 2, 3, 4, 0, -8)
>>> tup3
('a', 'b', 'c')

6.3.2 访问元组

元组可以使用下标索引来访问元组中的值。

【案例6-7】 访问元组

>>> tup1 = ('english','maths',95,85)
>>> print("tup1[0]",tup1[0])
tup1[0] english
>>> print("tup1[1:3]",tup1[1:3])
tup1[1:3] ('maths', 95)

6.3.3 连接元组

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合。

【案例6-8】 修改元组

>>> tup1 = ('english','maths',95,85)
>>> tup2 = (1,2,3,4,0,-8)
>>> tup3 = tup1 + tup2
>>> tup3
('english', 'maths', 95, 85, 1, 2, 3, 4, 0, -8)

6.3.4 删除元组

元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组。

【案例6-9】 删除元组

>>> tup1 = ('english','maths',95,85)
>>> print(tup1)
('english', 'maths', 95, 85)
>>> del tup1
>>> print(tup1)
Traceback (most recent call last):
File "<pyshell#49>", line 1, in <module>
print(tup1)
NameError: name 'tup1' is not defined

可以看出，在删除元组tup1后，再次输出元组tup1会出现错误。

6.3.5 元组运算符

与列表一样，元组之间可以使用“+”号和“*”号进行运算。这就意味着他们可以组合和复制，运算后会生成一个新的元组，元祖的运算符如表6-3所示。

表6-3 元组运算符

.. image:: /Chapter/picture/image154.jpg

6.3.6 元组内置函数

Python元组包含了以下内置函数，如表6-4所示：

表6-4 元组内置函数

.. image:: /Chapter/picture/image155.jpg

6.4 字典及基本操作
------------------

6.4.1 认识字典

Python中字典是一种可变容器模型，可存储任意类型对象。字典中的元素是由键值对构成的，每个键值对用冒号“:”分割，每个元素之间用逗号“,”分割，整个字典包括在花括号 {} 中，格式如下所示：
::

d = {key1 : value1, key2 : value2 }

需要注意的是，字典中的各元素的键一般是唯一的，值可以不是唯一的。

>>> dict1 = {'a':2,'b':3,'c':4}
>>> dict1
{'a': 2, 'b': 3, 'c': 4}
>>> dict2 = {'a':2,'b':3,'c':4,'b':6}
>>> dict2
{'a': 2, 'b': 6, 'c': 4}

6.4.2 访问字典

由于字典的每一个元素都是键值对，所以可以通键来获得元素的值。

【案例6-10】访问字典

>>> dict = {'a':2,'b':3,'c':4}
>>> dict['a']
2
>>> dict['b']
3
>>> dict['c']
4

6.4.3 更新字典

字典的更新和字典的访问类似，直接可以通过元素键来修改元素值。如果这个键是当前字典中没有，那就会以这个键值对增加一个元素，这就相当于做了字典的添加。

【案例6-11】更新字典

#更新

>>> dict = {'a':2,'b':3,'c':4}
>>> dict['a'] = 8
>>> dict
{'a': 8, 'b': 3, 'c': 4}
#添加
>>> dict['d'] = 10
>>> dict
{'a': 8, 'b': 3, 'c': 4, 'd': 10}

6.4.4 删除字典元素

删除操作可以指定删除某个元素，也能直接清空字典，清空可以使用clear方法。删除一个字典需要用del命令。

【案例6-10】删除字典元素

>>> dict = {'a':2,'b':3,'c':4}
>>> del dict['a'] #删除a键内容
>>> dict.clear() #字典清空
>>> del dict #删除字典

6.4.5 字典内置函数与方法

Python字典包含了以下内置函数，如下表6-5所示。

表6-5 字典内置函数

.. image:: /Chapter/picture/image156.jpg

Python字典包含了内置方法，如下表6-6所示。

表6-6 字典内置函数

.. image:: /Chapter/picture/image157.jpg
-----------------

6.5.1 预备知识

贪食蛇是一款经典的小游戏，玩家使用方向键操控一条长长的蛇不断吞下豆子，同时蛇身随着吞下的豆子不断变长，当蛇头撞到蛇身时游戏结束。贪吃蛇最初为人们所知的是诺基亚手机附带的一个小游戏，它伴随着诺基亚手机走向世界。现在的贪吃蛇出现了许多衍生版本，并被移植到各种平台上。如今，在我们的SKIDS平台上，利用Python语言可以实现它。

在本项目中，因为涉及到屏幕的显示、填充和食物的随机产生，所以在程序设计前，首先要引入相关的模块，或者是模块中某些方法：
::

   #引入machine中关于pin的方法
   from machine import Pin
   #引入time模块所有方法
   import time
   #引入utime模块所有方法
   import utime
   #引入randint方法，目的是可以产生随机数，控制食物的产生
   from random import randint
   #引入帧缓冲模块，用于图像显示
   import framebuf
   #引入lcd操作的相关方法，控制图像显示
   from show.lcd import HW_SPI,ILI9341,color565

6.5.2 任务要求

1. 界面绘制：生成贪食蛇的游戏界面；

2. 按键控制：四个按键是方向键，分别代表上下左右；

3. 食物生成：每吃掉一颗食物，再自动随机生成一颗食物；

4. 运动控制：贪食蛇以一个适合的速度向指定方向前进；

5. 游戏控制：游戏不能无故间断；

6.5.3 任务实施

1. 定义类

1）定义网格类

游戏中的坐标系，原点在左上角 (0, 0)，x 轴水平方向向右，逐渐增加；y
轴垂直方向向下，逐渐增加。在游戏中，所有可见的元素都是以矩形区域来描述位置的要描述一个矩形区域有四个要素：(x,
y) (width,
height)，这两个坐标分别是矩形区域的左上角坐标和宽度高度。如图6-1所示。

.. image:: /Chapter/picture/image096.jpg

图6-1 坐标系

贪吃蛇的网格坐标：将屏幕分成若干10*10的网格，对指定网格在屏幕上填充蓝色形成蛇的身体，对指定网格在屏幕上填充红色形成食物。网格左上角坐标和屏幕坐标的示意图如图6-2所示：变换公式为：
::

   x = 网格横坐标 \* 10 + a
   y = 网格纵坐标 \* 10 + b

.. image:: /Chapter/picture/image097.jpg


图6-2 网络规划

贪吃蛇在移动时，在移动方向上填充身体的屏幕颜色蓝色，在移动后蛇尾部填充背景的屏幕颜色白色，注意，不能向自己的反方向前进，如图6-3所示：

.. image:: /Chapter/picture/image098.jpg

图6-3 网络颜色填充

网格类示例代码如下：在类初始化代码中，定义了起始坐标，矩形宽度，填充颜色及显示填充的初始化。在draw(self,pos,color)方法中给出了计算各个单元格坐标的方法，并调用display的填充方法进行单元格的填充。
::

   class Grid(object):
      def __init__(self, master=None,x=10, y=10, w=222, h=303):
         self.x = x
         self.y = y
         self.w = w
         self.h = h
         self.width=w//10-1
         self.height=h//10-1
         self.bg=color565(0x00, 0x00, 0x00)
         print(self.width,self.height)
         display.fill(self.bg)
         display.fill_cell(x,y,w,h,color565(0xff, 0xff, 0xff))
         def draw(self, pos, color):
         x = pos[0] * 10 + self.x+1
         y = pos[1] * 10 + self.y+1
         display.fill_rectangle(x,y,10,10,color)

2）定义食物类

食物类在初始化函数中，定义了几个变量分别用来初始化食物的网格、颜色和位置信息。除此以外，还定义了两个类方法，分别是set_pos(self)和display(self)。前者用来生成一个随机的变量，用来描述食物随机生成的位置。后者用来根据随机产生的位置，以指定的颜色进行网格单元格填充。示例代码如下所示：
::

   class Food(object):
      def __init__(self, grid, color = color565(0xff, 0x00, 0x00)):
         self.grid = grid
         self.color = color
         self.set_pos()
         self.type = 1
      def set_pos(self):
         x = randint(0, self.grid.width - 1)
         y = randint(0, self.grid.height - 1)
         self.pos = (x, y)
      def display(self):
         self.grid.draw(self.pos, self.color)

3）定义蛇类

蛇类的初始化代码中，定义了与蛇操作相关的网格、颜色，移动朝向以及初始化蛇的身体位置信息。在初始化以后，利用grid类的draw()方法，画出了指定颜色的三个蛇身体图案。三个身体信息的坐标分别是：(5,
5), (5, 6), (5,
7)。另外，在游戏重新开始时，也有一个类似的初始化函数initial(self)，与类初始化函数类似，定义了与蛇操作相关的网格、颜色，移动朝向以及初始化蛇的身体位置信息。如下所示：
::

   class Snake(object):
      def __init__(self, grid, color = color565(0xff, 0xff, 0xff)):
         self.grid = grid
         self.color = color
         self.body = [(5, 5), (5, 6), (5, 7)]
         self.direction = "Up"
         for i in self.body:
            self.grid.draw(i, self.color)
         #这个方法用于游戏重新开始时初始化贪吃蛇的位置
      def initial(self):
         while not len(self.body) == 0:
            pop = self.body.pop()
            self.grid.draw(pop, self.grid.bg)
            self.body = [(8, 11), (8, 12), (8, 13)]
            self.direction = "Up"
            self.color = color565(0xff, 0xff, 0xff)
            for i in self.body:
               self.grid.draw(i, self.color)

蛇类的成员方法中，move()的功能是随着画面的不断刷新，不断的改变蛇的身体位置，并不断修改self.body列表中蛇身体的数据，使蛇的身体实现移动的效果。蛇每向前走一步，前方的单元格将被渲染成蛇身的颜色，而蛇尾最后一个单元格将被渲染成背景色。该方法将在游戏类中的被循环调用。
::

   def move(self, new):
      self.body.insert(0, new)
      pop = self.body.pop()
      self.grid.draw(pop, self.grid.bg)
      self.grid.draw(new, self.color)

蛇类的成员方法中，add()方法的功能是在蛇吃到正常的食物时，将自身的长度加1，并将body列表进行插入更新，最后通过draw方法渲染所在的单元格。
::

   def add(self ,new):
      self.body.insert(0, new)
      self.grid.draw(new, self.color)

cut_down()方法的功能是在蛇吃到特殊食物1时，将自身的长度加1，并将body列表进行插入更新，最后通过draw方法渲染所在的单元格。然后，利用一个循环操作，将body列表弹出指定个数的元素，从而实现蛇身体减1.最后利用grid.draw(pop,
self.grid.bg)将弹出的元素渲染成背景色。
::

   def cut_down(self,new):
      self.body.insert(0, new)
      self.grid.draw(new, self.color)
      for i in range(0,3):
         pop = self.body.pop()
         self.grid.draw(pop, self.grid.bg)

init()方法的功能是在蛇吃到特殊食物2时，将自身的长度恢复成最初的样子，首先将body列表进行插入更新，最后通过draw方法渲染所在的单元格。然后，利用一个循环操作，将body列表弹出指定个数的元素，从而实现蛇身体长度为3.最后利用grid.draw(pop,
self.grid.bg)将弹出的元素渲染成背景色。
::

   def init(self, new):
      self.body.insert(0, new)
      self.grid.draw(new, self.color)
      while len(self.body) > 3:
         pop = self.body.pop()
         self.grid.draw(pop, self.grid.bg)

change()方法的功能是在蛇吃到特殊食物3时，改变自身颜色。首先将body列表进行插入更新，最后通过draw方法渲染所在的单元格。然后利用grid.draw(item,
self.color)将蛇身渲染成其他颜色。
::

   def change(self, new, color):
      self.color = color
      self.body.insert(0, new)
      for item in self.body:
         self.grid.draw(item, self.color)

4）定义游戏类

游戏类是整个项目的综合类，在初始化构造函数中定义了网格类，蛇类和食物类。并且定义了游戏状态，游戏速度等参数值：
::

   class SnakeGame():
      def \__init__(self):
         self.grid = Grid()
         self.snake = Snake(self.grid)
         self.food = Food(self.grid)
         self.gameover = False
         self.score = 0
         self.status = ['run', 'stop']
         self.speed = 300
         self.display_food()

display_food（）方法用于在网格中显示随机生成的食物。为了增加游戏的趣味性，食物分为四个类型，分别是type1:普通食物，颜色用self.food.color= color565(0x00, 0xff, 0x00)表示；type2:减少长度，颜色用self.food.color= color565(0xff, 0xff,0xff)表示；type3:大乐透，回到最初状态，颜色用self.food.color =color565(0x00, 0xff, 0x00)表示；type4:吃了会变色，颜色用self.food.color= color565(0x00, 0x00,0xff)表示。需要注意的是，随机在网格中生成食物以后，每次都要检查，该食物是否有蛇身体的列表重复。如果重复，则重新生成。如下示例代码：
::

   def display_food(self):
      self.food.color = color565(0xff, 0x00, 0x00)
      self.food.type = 1
      if randint(0, 40) == 5:
         self.food.color = color565(0x00, 0xff, 0x00)
         self.food.type = 3
         while (self.food.pos in self.snake.body):
            self.food.set_pos()
            self.food.display()
      elif randint(0, 4) == 2:
         self.food.color = color565(0x00, 0x00, 0xff)
         self.food.type = 4
         while (self.food.pos in self.snake.body):
            self.food.set_pos()
            self.food.display()
      elif len(self.snake.body) > 10 and randint(0, 16) == 5:
         self.food.color = color565(0xff, 0xff, 0xff)
         self.food.type = 2
         while (self.food.pos in self.snake.body):
            self.food.set_pos()
            self.food.display()
      else:
         while (self.food.pos in self.snake.body):
            self.food.set_pos()
            self.food.display()
            print(self.food.type)
   initial(self)方法用于游戏重新开始时初始化游戏，包括游戏标志位设置、成绩初始为0以及蛇类重新初始化：
   ::
   
   def initial(self):
      self.gameover = False
      self.score = 0
      self.snake.initial()

run(self)方法是游戏类的运行代码，在游戏开始时循环运行。首先循环判断是否有按键按下，并记录哪个按键按下，以决定蛇身体向哪个方向移动；然后判断游戏是否暂停或者结束，如果暂停则游戏类调用initial(self)函数。最后，根据按键按下的情况，处理蛇身体列表数据；并实时检查吃到的食物类型，进行相应的处理。当吃到的食物坐标属于自己本身体列表中的数据后，游戏结束。如下示例代码：
::

   def run(self):
      while True:
         i=0
         j=-1
         for k in keys:
            if k.value()==0:
               if i!=j:
                  print("i=",i)
                  print("j=",j)
                  j=i
                  self.key_release(i)
                  i=i+1
               if i>3:
                  i=0
                 #首先判断游戏是否暂停
            if not self.status[0] == 'stop':
               if self.gameover == True:
                  self.initial()
               else:
                  #判断游戏是否结束
                  self.move()
                  time.sleep_ms(125)
                  #self.after(self.speed, self.run)
   def move(self, color=color565(0xff, 0xff, 0xff)):
   # 计算蛇下一次移动的点
      head = self.snake.body[0]
      #print(self.snake.direction)
      if self.snake.direction == 'Up':
         if head[1] - 1 < 0:
            new = (head[0], 29)
         else:
            new = (head[0], head[1] - 1)
      elif self.snake.direction == 'Down':
         new = (head[0], (head[1] + 1) % 29)
      elif self.snake.direction == 'Left':
         if head[0] - 1 < 0:
            new = (21, head[1])
         else:
            new = (head[0] - 1, head[1])
         else:
            new = ((head[0] + 1) % 21, head[1])
   #撞到自己，设置游戏结束的标志位，等待下一循环
         if new in self.snake.body:
            self.gameover=True
         #吃到食物
            elif new == self.food.pos:
            print(self.food.type)
            if self.food.type == 1:
               self.snake.add(new)
            elif self.food.type == 2:
               self.snake.cut_down(new)
            elif self.food.type == 4:
               self.snake.change(new, color565(0x00, 0x00, 0xff))
            else:
               self.snake.init(new)
               self.display_food()
            #什么都没撞到，继续前进
         else:
            self.snake.move(new)
   def key_release(self, key):
      keymatch=["Down","Left","Up","Right"]
      key_dict = {"Up": "Down", "Down": "Up", "Left": "Right", "Right":"Left"}
      print(keymatch[key])
   #蛇不可以像自己的反方向走
      if keymatch[key] in key_dict and not keymatch[key] ==key_dict[self.snake.direction]:
         self.snake.direction = keymatch[key]
         self.move()
2. 设计程序流程

1）游戏初始化

程序开始时，首先进行初始化工作，如图6-4所示。初始化包括三个方面：

.. image:: /Chapter/picture/image099.jpg

图6-4 程序流程

（1）设置游戏窗口

程序在开始时，首先创建了蛇类，并进行构造函数初始化，在构造函数中，进行了网格的初始化，用来设置游戏窗口，如图6-5所示。示例代码如下：
#在程序运行时，首先创建游戏类，并进行构造函数初始化
::

   snake = SnakeGame()
   #构造函数中，调用网格类实现界面设置
   self.grid = Grid()

.. image:: /Chapter/picture/image100.jpg

图6-5 程序初始化

（2）绘制图像初始位置

通过构造函数调用蛇类和食物类代码，实现绘制图像初始位置，如下代码：
::

   self.snake = Snake(self.grid)
   self.food = Food(self.grid)

（3）设置游戏时钟

通过time.sleep_ms(125)延时函数，设置游戏时钟。

2）游戏循环

初始化设置后以后，就可以利用一个大循环实现程序的功能了，主要功能包括检测用户交互，更新图像位置，更新屏幕显示等。主要控制代码在上面已经完整讲述过。利用循环去实现的主要目的是保证游戏不会直接退出、实现变化图像位置的动画效果、每隔一段时间移动或更新一下所有图像的位置、检测用户交互，如按键、鼠标等。程序运行效果如图6-6所示。

.. image:: /Chapter/picture/image101.jpg

图6-6 程序运行

.. _本章小结-5:

6.6 本章小结
------------

本章的主要任务是设计贪食蛇游戏。在设计之前，首先讲述了关于列表、元组和字典的相关知识，这些是贪食蛇程序设计的基础。然后，利用面向对象的程序设计方法，定义了四个类：网格类、食物类、蛇类以及游戏类。利用一个无限循环实现了贪食蛇游戏的功能。

.. _练习题目-5:

6.7 练习题目
------------

1. 设计一个“坦克大赛”的游戏，实现坦克的移动功能。坦克撞墙后，游戏结束。
