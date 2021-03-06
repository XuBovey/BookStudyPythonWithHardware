第8章 开发俄罗斯方块游戏
=========

8.1 面向对象的思想
------------------

我们以前学习的编程方式都是面向过程的，为了解决问题而编程，但很少考虑可扩展性、可维护性、可复用性，一旦需求变化了就要修改代码，程序没有适应变化的能力，那么这章我们将接触一个流行的编程思想，面向对象的编程，简称OOP，它和我们之前的思路差别很大，需要仔细体会其中的理念，反复练习使用这种思想去解决各种问题，你会发现它的强大之处，在应对不断变化的需求的过程中，面向对象编程为我们提供了良好的解决思路，它的继承、封装、多态这三大武器使程序变得更灵活更健壮，并且通过类的使用使编程更接近现实世界的处理问题的思路。

8.1.1 面向过程与面向对象

我们在学习面向对象思想之前一般的编程思路都是面向过程的。那么我来回顾一下我们一般是怎么做的：

1. 把完成某一个需求的所有步骤从头到尾逐步实现。

2. 根据开发需求，将某些功能独立的代码封装成一个又一个函数。

3. 最后完成的代码，就是顺序地调用不同的函数。

.. image:: /Chapter/picture/image113.png

图8-1 面向过程的函数调用执行的过程

如图8-1所示，面向过程的程序开发过程，注重步骤和过程，会将问题划分成多个模块，再逐步细化，对于简单的问题是可以很好处理解决的，但存在的问题是不注重职责的分工，如果需求复杂的话，代码会变得很复杂，并且代码的复用会变得很困难，如果开发复杂项目，就不会形成固定的套路，开发难度会不断增大。

那么面向对象的编程思路又有什么不同呢？

1. 在完成某一个需求前，首先确定职责——要做的事情（方法）。

2. 根据职责确定不同的对象，在对象内部封装不同的方法（多个）。

3. 最后完成的代码，就是顺序地让不同的对象调用不同的方法。

相比较过程，面向对象是更大的封装，根据职责在一个对象中封装多个方法，注重对象和职责，不同的对象承担不同的职责，更加适合应对复杂的需求变化，是专门应对复杂项目开发，提供的固定套路。例如下面的这个游戏。

.. image:: /Chapter/picture/image115.jpg
.. image:: /Chapter/picture/image137.jpg

图8-2 面向对象思想对游戏的抽象

如图8-2所示，在编写这个有系的时候，其实我们可以根据不同的职责确定出很多对象，例如向日葵、豌豆射手、冰冻射手、各种僵尸等等。每个对象负责不同的人物，每个对象有自己可以做的事情和自己的属性，这些都封装在对象内部，这样就可以将复杂的需求简单化，同时又增加了复用的可能，为类似的游戏提供了一个固定的解决套路。

8.1.2 类和对象

学习面向对象的编程思想，就绕不开两个概念类和对象，类和对象是面向对象编程的核心概念。

类：是对一群具有相同特征或者行为的事物的一个统称，是抽象的，不能直接使用。类由两部分组成，特征和行为，我们也可以称作属性和方法，由于我们不能使用抽象的东西，所以在使用的时候通常会找到这个类的一个具体的存在，使用这个具体的存在。

对象：是由类创建出来的一个具体存在，可以直接使用，由哪一个类创建出来的对象，就拥有在哪一个类中定义的属性、方法。

如图8-3所示，类就相当于制造飞机时的图纸，是一个模板，是负责创建对象的。对象就相当于用图纸制造的飞机。在程序开发中应该先有类，再有对象。

.. image:: /Chapter/picture/image116.png
.. image:: /Chapter/picture/image117.png

图8-3 面向对象思想对战斗机的抽象

8.2 面向对象的基本语法
----------------------

要想灵活运用面向对象编程思想，就需要掌握面向对象的基本语法，其中包括类的定义，对象的使用方法，一些内置方法和属性的使用等等。

8.2.1 类的定义

类（Class）由3个部分构成：类的名称（类名）、类的属性（一组数据）、类的方法
(行为)。

例如对人这个类可以这样设计：

人类设计,只关心3样东西：

事物名称（类名）：人（Person）。

属性:身高（height）、年龄（age）。

方法（行为/功能）：跑（run）、打架（fight）。

对狗类的设计可以是这样：

类名：狗（Dog）。

属性：品种 、毛色、性别、名字、 腿儿的数量。

方法（行为/功能）：叫 、跑、咬人、吃、摇尾巴。

具体到程序中如何定义一个类呢？定义一个类的格式如下：
::

   class 类名:
      def 方法1(self, 参数列表):
         pass
      def 方法2(self, 参数列表):
         pass
         
定义一个Car类：
::

   class Car:
      # 方法
      def getCarInfo(self):
         print('车轮子个数:%d, 颜色%s'%(self.wheelNum, self.color))
      def move(self):
         print("车正在移动...")

方法的定义格式和之前学习过的函数几乎一样，区别在于第一个参数是 self，大家暂时先记住，稍后介绍。这里还要对类名和方法名的命名方式做一下介绍。一般类名是一个名词，可以提炼这一类事物的名称作为类名，方法名可以使动词表示某种操作。同时类名的命名一般遵循大驼峰命名法。

8.2.2 创建对象

定义了一个Car类；就好比有车一个张图纸，那么接下来就应该把图纸交给生成工人们去生成了python中，可以根据已经定义的类去创建出一个个对象创建对象的格式为：
::

   对象变量 = 类名()
   例如刚才创建Car类，我们可以创建Car类的对象：
   ::
   
      BMW = Car()

【案例8-1】编写一个小猫类，小猫爱吃鱼，小猫可以喝水。

分析：定义一个猫类Cat、定义两个方法eat和drink、按照需求不需要定义属性。eat和drink分别可以输出“小猫爱吃鱼”，“小猫在喝水”。
::

   class Cat:
      """这是一个猫类"""
      def eat(self):
         print("小猫爱吃鱼")
      def drink(self):
         print("小猫在喝水")
         tom = Cat()
         tom.drink()
         tom.eat()

上面的例子中用Cat类创建了一个对象Tom，Tom对象再调用喝水和吃饭的方法drink()和eat()，其实Cat类可以创建多个对象。而且这些对象都有相同的属性和方法，但是可能会有不同的属性值和方法的实参。下面使用Cat类再创建一个对象。
::

   lazy_cat = Cat()
   lazy_cat.eat()
   lazy_cat.drink()

在这个实例中，我们创建了两只猫tom和lazy_cat，每只猫都是一个独立的实例或者对象，有自己的属性，能够执行相同的操作，但是它们并不是同一个对象。

8.2.3 __init__方法和self参数

通过上节的学习我们已经掌握了如何将类实例化成对象，但是大家可能发现，目前的类里面只有方法没有属性，那么如何在类里面创建属性行呢，这就需要学习__init__方法，注意这里__是两个下划线，其实当使用类名()创建对象时，会自动执行以下操作：

1. 为对象在内存中分配空间 —— 创建对象。

2. 为对象的属性设置初始值 —— 初始化方法(init)。

这个初始化方法就是__init__方法，__init__是对象的内置方法，__init__方法是专门用来定义一个类具有哪些属性的方法。具体使用方式如下：
::

   def 类名:
   #初始化函数，用来完成一些默认的设定
   def __init__(self):
      pass
   例如在Cat中增加__init__方法，可以自行验证一下该方法在创建对象时会被自动调用。
   class Cat:
      """这是一个猫类"""
      def __init__(self):
      print("初始化方法")

那么如何在__init__方法中设置属性呢，请看下面的例子：

【案例8-2】
编写一个猫类cat，设置name属性为“Tom”，创建eat方法，打印“Tom”爱吃鱼，实例化对象，并调用eat方法。

分析：需要为cat类设置name属性，并将name赋值为“Tom”，创建eat方法，通过print格式化输出name和“爱吃鱼”。
::

   class Cat:
      def __init__(self):
         print("这是一个初始化方法")
         # 定义用 Cat 类创建的猫对象都有一个 name 的属性
         self.name = "Tom"
      def eat(self):
         print("%s 爱吃鱼" % self.name)
         # 使用类名()创建对象的时候，会自动调用初始化方法 \__init_\_
         tom = Cat()
         tom.eat()

这样已经实现了属性的定义，但存在一个问题就是再创建一个对象的话name也是“Tom”，那么我们可以将这个程序进行改造，将name通过参数传入进行赋值，代码如下：
::

   class Cat:
      def __init__(self, name):
         print("初始化方法 %s" % name)
         self.name = name
      def eat(self):
         print("%s 爱吃鱼" % self.name)
         tom = Cat("Tom")
         tom.eat()
         lazy_cat = Cat("大懒猫")
         lazy_cat.eat()

这样如果希望在创建对象的同时，就设置对象的属性，可以对__init__方法进行改造

1. 把希望设置的属性值，定义成__init__方法的参数。

2. 在方法内部使用self.属性=形参接收外部传递的参数。

3. 在创建对象时，使用类名(属性1, 属性2...)调用。

在调用__init__方法时会传入一个默认参数self，self表示的是什么呢？self表示的是对象的引用，由哪一个对象调用的方法，方法内的self就是哪一个对象的引用，在类封装的方法内部，self就表示当前调用方法的对象自己，调用方法时，程序员不需要传递self参数，

在方法内部可以通过self.访问对象的属性，也可以通过self.调用其他的对象方法。在刚才的例子中，两个对象都调用eat()方法，在其中self就分别指向调用的对象，也就是调用方法的对象的引用，所以打印出的self.name就分别是每个对象自己的属性值。

8.2.4 内置方法和属性

除了上面我们介绍的__init__方法，还有哪些内置方法呢？比较常用的还有下面两个：

__del__方法，在对象被从内存中销毁前，会被自动调用。

__str__方法，在返回对象的描述信息，结合print函数输出使用。

在 Python
中当使用类名()创建对象时，为对象分配完空间后，自动调用__init__方法，

当一个对象被从内存中销毁前，会自动调用__del__方法，__init__方法可以让创建对象更加灵活，如果希望在对象被销毁前，再做一些事情，可以考虑一下__del__方法。这两个方法好像是一对前后呼应的方法，一个在对象出生时调用，一个在对象死亡时调用。对象就好像一个有生命的生物一样，那么对象也可以说是有生命周期的，一个对象从调用类名()创建，生命周期开始，一个对象的__del__方法一旦被调用，生命周期结束。在对象的生命周期内，可以访问对象属性，或者让对象调用方法。例如下面这个例子可以体现对象的生命周期：
::

   class Cat:
      def __init__(self, new_name):
         self.name = new_name
         print("%s 来了" % self.name)
      def __del__(self):
         print("%s 去了" % self.name)
         # tom 是一个全局变量
         tom = Cat("Tom")
         print(tom.name)
         # del 关键字可以删除一个对象
      del tom
         print("-" \* 50)

在Python中，使用print输出对象变量，默认情况下，会输出这个变量引用的对象是由哪一个类创建的，以及在内存中的地址（十六进制表示），如果在开发中，希望使用print输出对象变量时，能够打印自定义的内容，就可以利用__str__这个内置方法了：
::

   class Cat:
      def __init__(self, new_name):
         self.name = new_name
         print("%s 来了" % self.name)
      def __del__(self):
         print("%s 去了" % self.name)
      def __str__(self):
         return "我是小猫：%s" % self.name
   tom = Cat("Tom")
   print(tom)

print(tom)就会调用内置的__str__方法，只要自己定义了__str__(self)方法，那么就会打印从在这个方法中return的数据，也就是相当于print("我是小猫：%s"
% self.name)，输出“我是小猫：Tom”。

8.3 对象的封装
--------------

我们家里都有电视机，从开机，浏览节目，换台到关机，我们不需要知道电视机里面的具体细节，只需要在用的时候按下遥控器就可以完成操作，这就是功能的封装。

8.3.1 封装的概念

面向对象的思想是将所有的事物都看成对象，对象是一个整体，它会将一些属性和方法暴露出来，也会将一些属性和方法隐藏起来。这种具体对象的一种抽象，即将某些部分隐藏起来，在程序外部看不到，其含义是其他程序无法调用，这就是封装。封装不是单纯意义的隐藏，封装数据的主要原因是保护隐私，封装方法的主要有因是隔离复杂度。

封装是面向对象编程的一大特点，面向对象编程的第一步——将属性和方法封装到一个抽象的类中，外界使用类创建对象，然后让对象调用方法，对象方法的细节都被封装在类的内部。

【案例8-3】爱跑步的人，具体需求如下：

1. 小明体重75.0公斤。

2. 小明每次跑步会减肥0.5公斤。

3. 小明每次吃东西体重增加1公斤。

用类和对象实现这个例子。

分析：创建一个Person类，有个初始化方法，__str__方法，有两个属性name和体重weight，跑步和吃分别写成两个方法,跑步方法将体重减0.5，吃的方法将体重增加1。
::

   class Person:
      """人类"""
      def __init__(self, name, weight):
         self.name = name
         self.weight = weight
      def __str__(self):
         return "我的名字叫 %s 体重 %.2f 公斤" % (self.name, self.weight)
      def run(self):
         """跑步"""
         print("%s 爱跑步，跑步锻炼身体" % self.name)
         self.weight -= 0.5
      def eat(self):
         """吃东西"""
         print("%s 是吃货，吃完这顿再减肥" % self.name)
         self.weight += 1
         xiaoming = Person("小明", 75)
         xiaoming.run()
         xiaoming.eat()
         xiaoming.eat()
         print(xiaoming)

这个例子可以看出，将跑步和吃的实现封装成方法，外部只需要调用即可，具体的实现是在类的内部实现的体重的增减，而暴露给外部的只有这两个方法可供调用。

8.3.2 私有属性和方法

在实际开发中，对象的某些属性或方法可能只希望在对象的内部被使用，而不希望在外部被访问到，私有属性就是对象不希望公开的属性，私有方法就是对象不希望公开的方法。那么如何定义私有的属性和方法呢？在定义属性或方法时，在属性名或者方法名前增加两个下划线，定义的就是私有属性或方法，例如下面这个例子：
::

   class Women:
      def __init__(self, name):
         self.name = name
         # 不要问女生的年龄
         self.__age = 18
      def __secret(self):
         print("我的年龄是 %d" % self.__age)
         xiaofang = Women("小芳")
         # 私有属性，外部不能直接访问
         # print(xiaofang.__age)
         # 私有方法，外部不能直接调用
         # xiaofang.__secret()

上面的__age就是自由属性，外部不能直接访问，__secret()就是私有方法，外部也不能直接调用。但是在类的内部是可以访问私有的属性和方法的。

8.3.2 类属性和类方法

前面我们讲到当使用类名()创建对象，对象创建后，内存中就有了一个对象的实实在在的存在——实例。因此，通常也会把：创建出来的对象叫做类的实例，创建对象的动作叫做实例化，对象的属性叫做实例属性，对象调用的方法叫做实例方法。
在程序执行时：对象各自拥有自己的实例属性，在调用对象方法时，方法内部可以通过self.访问自己的属性，通过self.调用自己的其他方法。每一个对象都有自己独立的内存空间，保存各自不同的属性，多个对象的方法，在内存中只有一份，在调用方法时，需要把对象的引用传递到方法内部如图8-4所示。

.. image:: /Chapter/picture/image118.jpg

图8-4 实例属性和实例方法

在Python中一切都是对象，那么如果进一步的彻底的面向对象的话，其实类也是一种特殊的对象，在程序运行时，类同样会被加载到内存，在Python中，类是一个特殊的对象
——类对象。在程序运行时，类对象在内存中只有一份，使用一个类可以创建出很多个对象实例，除了封装实例的属性和方法外，类对象还可以拥有自己的属性和方法——类属性、类方法。通过类名.
的方式可以访问类的属性或者调用类的方法。类属性就是给类对象中定义的属性，通常用来记录与这个类相关的特征，类属性不会用于记录具体对象的特征，

可以使用赋值语句在class关键字下方定义类属性。

【案例8-4】定义一个工具类，每件工具都有自己的name，现在需要知道使用这个类，创建了多少个工具对象？请编程实现。

分析：要统计一个类创建了多少对象，可以使用类属性，由于类属性是类对象的属性，所以可以用作计数。
::

   class Tool(object):
      # 使用赋值语句，定义类属性，记录创建工具对象的总数
      count = 0
      def __init__(self, name):
         self.name = name
         # 针对类属性做一个计数+1
         Tool.count += 1
         # 创建工具对象
         tool1 = Tool("斧头")
         tool2 = Tool("榔头")
         tool3 = Tool("铁锹")
         # 知道使用 Tool 类到底创建了多少个对象?
         print("现在创建了 %d 个工具" % Tool.count)

这里在类里面的count=0就是声明了一个类属性count并初始化为0，每个对象初始化时会调用__init__方法，就会对类属性count加一，就实现了对象个数的统计，注意这里面name是实例属性，而count是类属性。

类方法就是针对类对象定义的方法，在类方法内部可以直接访问类属性或者调用其他的类方法，类方法的声明方式如下：
::

   @classmethod
   def 类方法名(cls):
      pass

类方法需要用修饰器@classmethod来标识，告诉解释器这是一个类方法，类方法的第一个参数应该是cls，由哪一个类调用的方法，方法内的cls就是哪一个类的引用，这个参数和实例方法的第一个参数是self类似，使用其他名称也可以，不过习惯使用cls。通过类名.调用类方法，调用方法时，不需要传递cls参数，在方法内部可以通过cls.访问类的属性，也可以通过cls.调用其他的类方法。

那么将刚才的例子进行修改，在类中封装一个show_tool_count的类方法，输出使用当前这个类创建的对象个数。
::

   @classmethod
   def show_tool_count(cls):
      """显示工具对象的总数"""
      print("工具对象的总数 %d" % cls.count)

可以看到，在类方法内部，可以直接使用cls访问类属性或者调用类方法。

8.4 继承和多态
--------------

接下来，我们来看对象最为重要的两个方面：继承和多态。这两个词看似很深奥，不过正是因为有这两个方面，才使得对象如此有用。我会在下面几节清楚地解释它们的含义。

8.4.1 继承

编写类时，并非总是要从空白开始。如果你要编写的类是另一个现成类的特殊版本，可使用继承。一个类继承另一个类时，它将自动获得另一个类的所有属性和方法；原有的类称为父类，而新类称为子类。子类继承了其父类的所有属性和方法，同时还可以定义自己的属性和方法。继承实现代码的重用，相同的代码不需要重复的编写，继承的语法如下：
::

   class 类名(父类名):
   pass

子类继承自父类，可以直接享受父类中已经封装好的方法，不需要再次开发，子类中应该根据职责，封装子类特有的属性和方法。

在程序中，继承描述的是事物之间的所属关系，例如猫和狗都属于动物，程序中便可以描述为猫和狗继承自动物；同理，波斯猫和巴厘猫都继承自猫，而沙皮狗和斑点狗都继承自狗，如图8-5所示：

.. image:: /Chapter/picture/image119.png

图8-5 动物继承的关系图

以波斯猫继承自猫为例我们看一下代码的实现：
::

   # 定义一个父类，如下:
   class Cat(object):
      def __init__(self, name, color="白色"):
         self.name = name
         self.color = color
      def run(self):
         print("%s--在跑"%self.name)
         # 定义一个子类，继承Cat类如下:
   class Bosi(Cat):
      def setNewName(self, newName):
         self.name = newName
      def eat(self):
         print("%s--在吃"%self.name)
         bs = Bosi("印度猫")
         print('bs的名字为:%s'%bs.name)
         print('bs的颜色为:%s'%bs.color)
         bs.eat()
         bs.setNewName('波斯')
         bs.run()

可以发现Bosi类继承自Cat就拥有了Cat的属性name和color，并且拥有了父类的run方法，子类又增加了一个eat方法，这样Bosi就拥有了run和eat方法。在后面对实例化对象bs之后就可以直接调用这两个方法。

继承也有传递性：C类从B类继承，B类又从A类继承，那么C类就具有B类和A类的所有属性和方法。

子类对象不能在自己的方法内部，直接访问父类的私有属性或私有方法，子类对象可以通过父类的公有方法间接访问到私有属性或私有方法，私有属性、方法是对象的隐私，不对外公开，外界以及子类都不能直接访问，私有属性、方法通常用于做一些内部的事情。

那么子类是否可以同时继承自多个父类呢？当然可以，这种继承叫多继承，子类可以拥有多个父类，并且具有所有父类的属性和方法，就想孩子会继承自己父亲和母亲的特性一样，多继承的语法如下：
::

   class 子类名(父类名1, 父类名2...)
      pass

多继承会存在一个问题，如果不同的父类中存在同名的方法，子类对象在调用方法时，会调用哪一个父类中的方法呢？Python提供了多种的搜索方式，当找到适合的方法，就直接执行不再搜索，如果没有找到，就查找下一个类中是否有对应的方法，如果找到，就直接执行不再搜索，如果找到最后一个类，还没有找到方法，程序报错。其实在开发时，应该尽量避免这种容易产生混淆的情况。如果父类之间存在同名的属性或者方法，应该尽量避免使用多继承。

8.4.2 方法重写

上一节说到了子类拥有父类的所有方法和属性，子类继承自父类，可以直接享受父类中已经封装好的方法，不需要再次开发。但是当父类的方法实现不能满足子类需求时如何处理呢？子类可以重写父类的方法，重写父类方法有两种情况：覆盖父类的方法，对父类方法进行扩展。

在开发中，父类的方法实现和子类的方法实现完全不同就可以使用覆盖的方式，在子类中重新编写父类的方法实现，具体的实现方式就相当于在子类中定义了一个和父类同名的方法并且实现，重写之后，在运行时只会调用子类中重写的方法，而不再会调用父类封装的方法，例如还是波斯猫的例子代码如下：
::

   class Cat(object):
      def sayHello(self):
         print("halou-----1")
   class Bosi(Cat):
      def sayHello(self):
         print("halou-----2")
         bosi = Bosi()
         bosi.sayHello()

子类重写的父类的sayHello方法，在调用时只会调用子类中重写的sayHello方法，而不再会调用父类的sayHello方法，注意重写的方法名和参数要和父类一致。

在开发中，如果父类的方法满足一部分需求，也就是父类原本封装的方法实现可以作为子类方法的一部分，就可以使用扩展的方式，在子类中重写父类的方法，在需要的位置使用super().父类方法来调用父类方法的执行，代码其他的位置针对子类的需求，编写子类特有的代码实现，例如刚才的例子再做一下修改：
::

   class Cat(object):
      def sayHello(self):
         print("halou-----1")
   class Bosi(Cat):
      def sayHello(self):
         super().sayHello()
         print("halou-----2")
      bosi = Bosi()
         bosi.sayHello()

这个例子中子类重写父类方法时，采用扩展的方式，先调用父类的方法，再执行自己添加的部分，这里面super是一个特殊的类，super()就是使用super类创建出来的对象，最常使用的场景就是在重写父类方法时，调用在父类中封装的方法实现。

8.4.3 多态

多态是指不同的子类对象调用相同的父类方法，产生不同的执行结果，也就是定义时的类型和运行时的类型不一样，此时就称为多态，多态可以增加代码的灵活度，多态以继承和重写父类方法为前提，是调用方法的技巧，不会影响到类的内部设计，多态的概念是应用于Java和C#这一类强类型语言中，而Python崇尚“鸭子类型”，“鸭子类型”可以这样表述：“当看到一只鸟走起来像鸭子、游泳起来像鸭子、叫起来也像鸭子，那么这只鸟就可以被称为鸭子”，也就是关注的不是对象的类型本身，而是它是如何使用的。

【案例8-5】需求如下：

1. 在Dog类中封装方法game，表示狗能玩耍。

2. 定义XiaoTianDog继承自Dog，并且重写game方法，表示哮天犬需要在天上玩耍。

3. 定义MuYangDog继承自Dog，并且重写game方法，表示牧羊犬需要在草地上玩耍。

4. 定义Person类，并且封装一个和狗玩的方法，在方法内部，直接让狗对象调用game方法。

分析：Person类中只需要让狗对象调用game方法，而不关心具体是什么狗，game方法是在Dog父类中定义的，在程序执行时，传入不同的狗对象实参，就会产生不同的执行效果。
::

   class Dog(object):
      def __init__(self, name):
         self.name = name
      def game(self):
         print("%s 蹦蹦跳跳的玩耍..." % self.name)
   class XiaoTianDog(Dog):
      def game(self):
         print("%s 飞到天上去玩耍..." % self.name)
   class MuYangDog(Dog):
      def game(self):
         print("%s 在草地上玩耍..." % self.name)
   class Person(object):
      def __init__(self, name):
         self.name = name
      def game_with_dog(self, dog):
         print("%s 和 %s 快乐的玩耍..." % (self.name, dog.name))
      # 让狗玩耍
         dog.game()
         # 1. 创建两个狗对象
         wangcai = XiaoTianDog("飞天旺财")
         xiaohua=MuYangDog("小花狗")
         # 2. 创建一个小明对象
         xiaoming = Person("小明")
         # 3. 让小明调用和狗玩的方法
         xiaoming.game_with_dog(wangcai)
         xiaoming.game_with_dog(xiaohua)

8.5 开发俄罗斯方块游戏
----------------------

《俄罗斯方块》是一款休闲游戏，游戏规则很简单，《俄罗斯方块》基本规则是移动、旋转和摆放游戏自动输出的各种方块，使之排列成完整的一行或多行并且消除得分。

8.5.1 预备知识

俄罗斯方块屏幕有两个区域，如图8-6所示，一个是游戏区域，一个是方块预览区域。游戏区域用于下落方块进行堆积。预览区域用于显示下一个要下落的方块类型。

.. image:: /Chapter/picture/image120.png

图8-6 游戏界面

将界面拆分成若干个的网格，如图8-7所示，每个格是10*10的大小，将预览窗口也同样拆分成网格，游戏就是控制在不同的时机渲染不同的网格。

消除机制：当某行没有空的方块时，会消除这行，同时对这行以上的所有行进行移动，向下移动一行。

失败条件：当第0行不为空时，则游戏结束。

.. image:: /Chapter/picture/image121.png

图8-7 界面网格化

8.5.2 任务要求

1. 界面绘制：生成游戏界面，游戏界面如图8-8所示；

2. 按键控制：四个按键是方向键，分别代表上下左右；

3. 游戏控制：游戏不间断运行，当触发按键时可以变换方块的角度，当满足消除条件时消除放满的行，当达成失败条件时结束游戏；

4. 失败条件：当第0行不为空时，则游戏结束；

.. image:: /Chapter/picture/image122.jpg

图8-8 完成效果

8.5.3 任务实施

1. 初始化

用嵌套列表声明可用的方块的数据，对按键进行初始化。
::

   from machine import Pin
   import time
   from random import randint
   import screen
   import text
   pins = [36,39,34,35]
   keys = []
   brick = [
   [
   [
   [1,1,1],
   [0,0,1],
   [0,0,0]
   ],
   [
   [0,0,1],
   [0,0,1],
   [0,1,1]
   ],
   [
   [0,0,0],
   [1,0,0],
   [1,1,1]
   ],
   [
   [1,1,0],
   [1,0,0],
   [1,0,0]
   ]
   ],
   [
   [
   [0,0,0],
   [0,1,1],
   [0,1,1]
   ],
   [
   [0,0,0],
   [0,1,1],
   [0,1,1]
   ],
   [
   [0,0,0],
   [0,1,1],
   [0,1,1]
   ],
   [
   [0,0,0],
   [0,1,1],
   [0,1,1]
   ]
   ],
   [
   [
   [1,1,1],
   [0,1,0],
   [0,1,0]
   ],
   [
   [0,0,1],
   [1,1,1],
   [0,0,1]
   ],
   [
   [0,1,0],
   [0,1,0],
   [1,1,1]
   ],
   [
   [1,0,0],
   [1,1,1],
   [1,0,0]
   ]
   ],
   [
   [
   [0,1,0],
   [0,1,0],
   [0,1,0]
   ],
   [
   [0,0,0],
   [1,1,1],
   [0,0,0]
   ],
   [
   [0,1,0],
   [0,1,0],
   [0,1,0]
   ],
   [
   [0,0,0],
   [1,1,1],
   [0,0,0]
   ]
   ]
   ]
   for p in pins:
      keys.append(Pin(p,Pin.IN))

2. 网格类

构造Grid类，主要功能是绘制背景及绘制界面，提供两个分别刷新游戏区域和预览区域的方法。
::

   class Grid(object):
      def __init__(self, master = None, x = 10, y = 10, w = 193, h = 303):
      	self.x = x
      	self.y = y
      	self.w = w
      	self.h = h
      	self.rows = h//10
      	self.cols = w//10
      	self.bg = 0x000000;
      	print(self.rows,self.cols)
      	#画背景
      	for i in range(320):
	 screen.drawline(0, i, 239, i, 1, self.bg);
         #画边界
         screen.drawline(x,y,x + w - 1,	y,1,0xFFFFFF)
         screen.drawline(x + w - 1,y,x + w - 1,y + h,1,0xFFFFFF)
         screen.drawline(x,y + h,x + w - 1,	y + h,1,0xFFFFFF)
         screen.drawline(x,y,x,y + h,1,	0xFFFFFF)
         #画预览框边界
         screen.drawline(204,10,	204 + 32 - 1,10,1,0xFFFFFF)
         screen.drawline(204 + 32 - 1,	10,204 + 32 - 1,10 + 32,	1,0xFFFFFF)
         screen.drawline(204,10 + 32,	204 + 32 - 1,10 + 32,1,0xFFFFFF)
         screen.drawline(204,10,	204,	10 + 32,1,0xFFFFFF)

在__init__方法中，调用了screen.drawline函数来画直线，画出游戏区域的边框、和预览区域的边框。
::

   def drawgrid(self, pos, color):
      x = pos[1] * 10 + self.x + 2
      y = pos[0] * 10 + self.y + 2
      for i in range(9):
         screen.drawline(x, y + i, x + 9 - 1, y + i, 1, color)
   def drawpre(self, pos, color):
      x = pos[1] * 10 + 204 + 2
      y = pos[0] * 10 + 10 + 2
      for i in range(9):
         screen.drawline(x, y + i, x + 9 - 1, y + i, 1, color)

drawgrid和drawpre提供列两个方法，去渲染游戏区域和预览区域的网格，首先需要将网格坐标转换成实际坐标，然后再通过screen.drawline去画网格。

3. 游戏类

继承自Grid类，可以使用Grid类的渲染网格的方法，主要实现方块的绘制，方块的变换，边缘检测，行的消除，按键控制等主要方法。
::

   class Game(Grid):
      def __init__(self):
         super().__init__()
         self.back = [[0 for i in range(0, self.cols)] for i in range(0,self.rows)]
         self.curRow = -10
         self.curCol = -10
         self.start = True
         self.shape = -1
         self.isDown = True
         self.oldrow = 0
         self.oldcol = 0
         #当前有方块的开始行
         self.haverow = 29
         self.nextBrick = -1
         self.shape = 0
         self.arr = [[0 for i in range(0,3)] for i in range(0,3)]
         self.nextarr = [[0 for i in range(0,3)] for i in range(0,3)]
         #使用一个字典将数字与其对应的颜色存放起来
         self.color = { 0:0x0000FF, 1:0x00FF00, 2:0xFF0000, 3:0xFFFF00 }

__init__方法初始化一个二维数组，用于保存屏幕上的网格数据，1表示这个网格需要被渲染，0表示不需要，并将这个数组保存到back属性中。其他属性大部分为基本参数，self.arr储存当前游戏区域的方块的网格数据，self.nextarr存储预览区域的方块的网格数据，self.color保存方块颜色，注意方块都是一个3*3大小的网格。
::

   def drawBack(self, rownum):
      for i in range(self.haverow, rownum + 1):
         for j in range(0, self.cols):
            pos = (i, j)
            if self.back[i][j] == 0:
               self.drawgrid(pos, self.bg)
            else:
               self.drawgrid(pos, 0x00FFFF)
               self.haverow += 1
         if self.haverow >= self.rows:
            self.haverow = self.rows - 1

drawBack方法是对已经下落到底部的方块的渲染，通过循环遍历所有已经固定的方块，根据back数组，如果为0则渲染背景色，为1则渲染蓝色。
::

   def drawRect(self):
      for i in range(0, len(self.nextarr)):
         for j in range(0, len(self.nextarr[i])):
            pos = (i, j)
            if self.nextarr[i][j] == 0:
               self.drawpre(pos, self.bg)
            elif self.nextarr[i][j] == 1:
               self.drawpre(pos, self.color[self.nextBrick])
               for i in range(0, 3):
                  for j in range(0, 3):
                     print("oldrow+i=", self.oldrow + i, self.oldcol + j)
                           if ((self.oldrow + i) >= self.rows) or ((self.oldcol + j) >=self.cols) or ((self.oldcol + j) < -1):
                              break
                     if self.oldcol+j < 0:
                           pos = (self.oldrow + i, 0)
                     else:
                           pos = (self.oldrow + i, self.oldcol + j)
                  if self.back[self.oldrow + i][self.oldcol + j] == 0:
                     self.drawgrid(pos, self.bg);
                     #绘制当前正在运动的方块
                     #print(self.curRow,self.curCol)
               if (self.curRow != -10) and (self.curCol != -10):
                  for i in range(0, len(self.arr)):
                     for j in range(0, len(self.arr[i])):
                        if self.arr[i][j] == 1:
                           pos = (self.curRow + i,self.curCol + j)
                           if self.isDown:
                              if i < self.haverow:
                                 self.haverow = i
                                 self.drawgrid(pos, 0x00FFFF)
                              else:
                                 self.drawgrid(pos, self.color[self.curBrick])
                                 #判断方块是否已经运动到达底部
                     if self.isDown:
                        for i in range(0, 3):
                           for j in range(0, 3):
                              if self.arr[i][j] != 0:
                                 self.back[self.curRow + i][self.curCol + j] = self.arr[i][j]
                                 self.oldrow = 0
                                 self.oldcol = 0
                                 #判断整行消除
                                 self.removeRow()
                                 self.isDead()
                                 #获得下一个方块
                                 self.getCurBrick()
                     else:
                        self.oldrow = self.curRow
                        self.oldcol = self.curCol

drawRect方法主要用于绘制方块，首先绘制预览区域的方块，双重循环遍历self.nextarr数组，调用父类的drawpre方法进行渲染，渲染渲染下一个要显示的方块前，先将当前的位置渲染成背景颜色，判断是否已经到达边界，如果到达边界调整坐标值，然后绘制当前正在下落的方块，循环遍历arr数组，根据arr中的数据进行渲染，如果方块已经到底则改变方块的颜色为蓝色，方块到底之后，更新back数组，back数组中存放当前所有固定的方块的位置，调用removeRow进行消除判断，调用isDead判断游戏失败条件，取下一个方块的数据，更新当前行和列的值。
::

   def getCurBrick(self):
      self.shape = 0
      if self.nextBrick == -1:
         self.curBrick = randint(0, len(brick)-1)
         self.nextBrick = randint(0, len(brick)-1)
      elif self.isDown:
         self.curBrick = self.nextBrick
         self.nextBrick = randint(0, len(brick)-1)
         self.nextarr = brick[self.nextBrick][self.shape]
         #self.curBrick = 3
         #当前方块数组
         self.arr = brick[self.curBrick][self.shape]
         #self.nextarr = self.arr
         self.curRow = -1
         self.curCol = 8
         #是否到底部为False
         self.isDown = False

getCurBrick方法第一次调用时，同时随机产生当前的方块和预览方块，当前方块已经落到底之后，则用预览方块替换当前方块，并随机产生新的预览方块，更新nextarr和arr两个数组的数据。
::

   def isEdge(self, direction):
      tag = True
      #print(direction)
      #向左，判断边界
      if direction == 1:
         for i in range(0, 3):
            for j in range(0, 3):
               if(self.arr[j][i]!=0) and (self.curCol + i < 0 or
                  self.back[self.curRow + j][self.curCol + i] != 0):
                  tag = False
                  break
                  #向右，判断边界
      elif direction == 3:
         for i in range(0, 3):
            for j in range(0, 3):
               if(self.arr[j][i]!=0)and(self.curCol+i>=self.colsorself.back[self.curRow+ j][self.curCol + i] != 0):
                  tag = False
                  break
                  #向下，判断底部
      elif direction == 4:
         for i in range(0, 3):
            for j in range(0, 3):
               if (self.arr[i][j] != 0) and (self.curRow + i >= self.rows or self.back[self.curRow + i][self.curCol + j] != 0):
                  tag = False
                  self.isDown = True
                  break
                  #进行变形，判断边界
      elif direction == 2:
         if self.curCol < 0:
            self.curCol = 0
            if self.curCol + 2 >= self.cols:
               self.curCol = self.cols - 3
               if self.curRow + 2 >= self.rows:
                  self.curRow = self.curRow - 3
         return tag

isEdge方法主要是判断当前方块是否到达边界，如果达到边界则返回False，进行形状变换时，如果变换之后超过边界，则更新当前位置为边界-3，使变换后图形仍然在边界内。
::

   def isDead(self):
      for j in range(0,len(self.back[0])):
         if self.back[0][j]!=0:
            print("GAME OVER")
            text.draw("GAME OVER", 34, 150, 0xFF0000, 0x000000)
            self.start = False
            break

isDead方法主要做游戏结束的判断，循环第0行，发现有网格已经渲染，则游戏结束。
::

   def removeRow(self):
      rownum = 0
      print("removeRow")
      for i in range(0, self.rows):
         tag1 = True
         for j in range(0, self.cols):
            if self.back[i][j]==0:
               tag1 = False
               break
      if tag1 == True:
         print(i, j)
         rownum = i
         #从上向下挪动
         for m in range(i-1, 0, -1):
            for n in range(0,self.cols):
               self.back[m + 1][n] = self.back[m][n]
               print(rownum)
               if rownum > 0:
                  self.drawBack(rownum)

removeRow方法的主要功能是对已经落满方块的行进行消除，从0行0列开始循环，发现有为空的网格，则说明本行没有被填满，不能消除直接break，可以消除则，从当前行向上到0行开始循环，将方块向下移动，可能存在同时消除多行的情况，处理完back数组之后调drawBack进行渲染。
::

   def onKeyboardEvent(self, key):
      keymatch=["Down", "Left", "Up", "Right"]
      #未开始，不必监听键盘输入
      if self.start == False:
         return
      #记录原来的值
      tempCurCol = self.curCol
      tempCurRow = self.curRow
      tempShape = self.shape
      tempArr = self.arr
      direction = -1
      print(keymatch[key])
      if keymatch[key] == "Left":
         #左移
         self.curCol -= 1
         direction = 1
      elif keymatch[key] == "Up":
         #变化方块的形状
         self.shape += 1
         direction = 2
      if self.shape >= 4:
         self.shape = 0
         self.arr = brick[self.curBrick][self.shape]
      elif keymatch[key] == "Right":
         direction = 3
         #右移
         self.curCol += 1
      elif keymatch[key] == "Down":
         direction = 4
      #下移
         self.curRow += 2
         if self.isEdge(direction) == False:
            self.curCol = tempCurCol
            self.curRow = tempCurRow
            self.shape = tempShape
            self.arr = tempArr
            #self.drawRect()
      return True

onKeyboardEvent方法主要对按键操作进行处理，向左，则更改当前列-1，方向为1，向上，则更改方块形状，shape+1方向还是向下，如果shape已经到4了则变回第一个形状0，调用isEdage进行边界判断，如果到达边界则恢复原始位置。

4. 主循环

主循环是游戏的入口，开始后不断循环监听按键输入，并调用游戏类的按键处理方法。
::

   def brickStart(self):
      while True:
         #需要进行垃圾回收
         gc.collect()
         if self.start == False:
            print("exit thread")
            break
         if self.isDown:
            self.getCurBrick()
            i = 0
            j = -1
            for k in keys:
               if k.value() == 0:
                  if i != j:
                     print("i=", i)
                     print("j=", j)
                     j = i
                     self.onKeyboardEvent(i)
                     i = i + 1
                     if i > 3:
                        i = 0
                     tempRow = self.curRow;
                     self.curRow += 1
                if self.isEdge(4) == False:
                     self.curRow = tempRow
                     #每一秒下降一格
                     time.sleep_ms(120)
                     self.drawRect()

brickStart方法中有程序的主循环，在循环中不断获取按键值，根据按键情况调用onKeyboardEvent函数处理，之后进行边界检测，方法默认在没有按下按键时方块也会向下移动，并且方法设置循环时间间隔为120毫秒。

剩下的就是实例化Game类，调用主函数。
::

   if __name__ == '__main__':
      game = Game()
      game.brickStart()

.. _本章小结-7:

8.6 本章小结
------------

在本章节中，主要学习了Python语言中的面向对象编程思想，了解什么是类和对象，并且重点学习了面向对象的三大特点：封装、继承、多态。最后通过开发俄罗斯方块游戏，使面向对象的理解更加具体深入。

要想熟练运用面向对象的思想来解决实际问题，需要不断的练习和总结，初学者往往体会不到面向对象的好处，但在实际的大型项目中就会体会到面向对象带来的强大的易维护、适应变化、易复用等诸多优点。

.. _练习题目-7:

8.7 练习题目
------------

1.
摆放家具需求：房子有户型，总面积和家具名称列表，新房子初始没有任何的家具，家具有名字和占地面积，其中床：占4平米、衣柜：占2平面、餐桌：占1.5平米，将以上三件家具添加到房子中，要求输出：户型，总面积，剩余面积，家具名称列表。

2.
需求：士兵瑞恩有一把AK47，士兵可以开火(士兵开火扣动的是扳机)，枪能够发射子弹(把子弹发射出去)，枪能够装填子弹——增加子弹的数量。

3. 
设计一个Game类

属性有：

定义一个属性top_score记录游戏的历史最高分

定义一个属性player_name记录当前游戏玩家姓名

方法有：

show_help显示游戏帮助信息

show_top_score显示历史最高分

show_game开始当前玩家的游戏
