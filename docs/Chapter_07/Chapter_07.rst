第7章 2048的游戏制作
=========

7.1 函数的定义和调用
--------------------

前面所学习的程序都是为了实现某些功能而编写的，但是这种程序如何能被很容易的被其他人使用或嵌入自己的程序中呢，这就需要对代码块进行命名，方便进行使用，这就是函数，函数是带名字的代码块，用于完成具体的特定工作。

要执行函数定义的特定任务，可调用该函数。需要在程序中多次执行同一项任务时，无需反复编写完成该任务的代码，而只需调用执行该任务的函数，让Python运行其中的代码。通过使用函数，程序的编写、阅读、测试和修复都将更容易。

7.1.1 定义函数

下面是一个打印问候语的简单函数，名为greet_user()
::

   def greet_user():
      """显示简单的问候语"""
      print("Hello!")
      print("This is function")
      greet_user()

这个示例演示了最简单的函数结构。使用关键字def来告诉Python你要定义一个函数。这是函数定义，向Python指出了函数名，还可能在括号内指出函数为完成其任务需要什么样的信息。在这里，函数名为greet_user()，它不需要任何信息就能完成其工作，因此括号是空的（即便如此，括号也必不可少）。最后，定义以冒号结尾。

紧跟在defgreet_user():后面的所有缩进行构成了函数体。"""的文本是被称为文档字符串的注释，描述了函数是做什么的。文档字符串用三引号括起，Python使用它们来生成有关程序中函数的文档。

代码行print("Hello!")和print("This isfunction")是函数体内的代码，greet_user()只做一项工作：打印Hello!和This is function。

要使用这个函数，可以调用它。函数调用让Python执行函数的代码。要调用函数，可依次指定函数名以及用括号括起的必要信息，由于这个函数不需要任何信息，因此调用它时只需输入greet_user()即可。和预期的一样，它的功能是打印如下结果：
::

   Hello!
   This is function

7.1.2 调用过程

上面那个例子的最后一行是对函数的调用，这句中的greet_user()可以认为是主程序，这里给出函数名和括号来调用这个函数。整个程序就从这行开始运行。正是这一行让程序开始运行刚才定义的函数中的代码。
::

   def greet_user():
      """显示简单的问候语"""
      print("Hello!")
      print("This is function")
      greet_user()
      print("This is end")

图7-1 函数调用执行的过程

主程序调用函数时，就像是这个函数在帮助主程序完成它的任务。def块中的代码并不是主程序的一部分，所以程序运行时，它会跳过这一部分，从def块以外的第一行代码开始运行。如图显示了调用函数时会发生什么。我在程序最后额外增加了一行代码，它会在函数完成后打印一条消息。

这个图7-1中包括以下步骤。

Step 1.：从这里开始。这是主程序的开始。

Step 2.：调用函数时，跳到函数中的第一行代码。

Step 3.：执行函数中的每一行代码。

Step 4.：函数完成时，从离开主程序的那个位置继续执行。

调用函数是指运行函数里的代码。如果我们定义了一个函数，但是从来不调用它，这些代码就永远也不会运行。调用函数时要使用函数名和一对括号。有时括号里还会有些东西，有时也可能什么也没有下面我们会介绍这部分知识。

7.2 函数的参数和返回值
----------------------

在上面的例子中函数的定义中函数名后面有一对括号，括号里可以传入一些信息，或者什么也不传。那么在编程中，交给函数的一条信息就可以叫做参数。我们把这称为：向函数传递参数。

7.2.1 形参和实参

我们可以对greet_user()进行升级，在定义函数greet_user()时，如果在括号中增加一个username变量，给变量username指定一个值。调用这个函数并提供这个值（人名）时，函数功能变成打印相应的问候语。

那么在函数greet_user()的定义中，变量username是一个形参——函数完成其工作所需的一项信息。在代码greet_user('jesse')中，值'jesse'是一个实参。实参是调用函数时传递给函数的信息。我们调用函数时，将要让函数使用的信息放在括号内。在greet_user('jesse')中，将实参'jesse'传递给了函数greet_user()，这个值被存储在形参username中。

鉴于函数定义中可能包含多个形参，因此函数调用中也可能包含多个实参。向函数传递实参的方式很多，可使用位置实参，这要求实参的顺序与形参的顺序相同；也可使用关键字实参，其中每个实参都由变量名和值组成；还可使用列表和字典。下面来依次介绍这些方式。

7.2.2 传递实参的几种方式

调用函数时，Python必须将函数调用中的每个实参都关联到函数定义中的一个形参，最常用的传递方式是根据参数的位置来和形参关联，例如下面的例子

【案例7-1】 编写函数打印宠物类型和名字

分析：传入一种动物类型和一个名字，打印相关的宠物信息，需要两个参数一种动物类型和一个名字。
::

   def describe_pet(animal_type, pet_name):
      """显示宠物的信息"""
      print("\nI have a " + animal_type + ".")
      print("My " + animal_type + "'s name is " + pet_name.title() + ".")
      describe_pet('hamster', 'harry')

调用describe_pet()时，需要按顺序提供一种动物类型和一个名字。例如，在前面的函数调用中，实参'hamster'存储在形参animal_type中，而实参'harry'存储在形参pet_name中。在函数体内，使用了这两个形参来显示宠物的信息。输出描述了一只名为Harry的仓鼠：
::

   I have a hamster.
   My hamster's name is Harry.

你可以根据需要调用函数任意次。要再描述一个宠物，只需再次调用describe_pet()即可：
::

   describe_pet('dog', 'willie')

第二次调用describe_pet()函数时，我们向它传递了实参'dog'和'willie'。与第一次调用时一样，Python将实参'dog'关联到形参animal_type，并将实参'willie'关联到形参pet_name。与前面一样，这个函数完成其任务，但打印的是一条名为Willie的小狗的信息。至此，我们有一只名为Harry的仓鼠，还有一条名为Willie的小狗：
::
   I have a dog.
   My dog's name is Willie.

调用函数多次是一种效率极高的工作方式。我们只需在函数中编写描述宠物的代码一次，然后每当需要描述新宠物时，都可调用这个函数，并向它提供新宠物的信息。即便描述宠物的代码增加到了10行，依然只需使用一行调用函数的代码，就可描述一个新宠物。

在函数中，可根据需要使用任意数量的位置实参，Python将按顺序将函数调用中的实参关联到函数定义中相应的形参。但是如果调用者不知道参数的位置顺序，就很容易将实参的位置搞错，会使函数的使用出错，那么为了解决这个问题，又引入了新的传递方式。

关键字实参是传递给函数的名称—值对。你直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆（不会得到名为Hamster的harry这样的结果）。关键字实参让你无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。

下面来重新编写，在其中使用关键字实参来调用describe_pet()：
::

   def describe_pet(animal_type, pet_name):
      """显示宠物的信息"""
      print("\nI have a " + animal_type + ".")
      print("My " + animal_type + "'s name is " + pet_name.title() + ".")
      describe_pet(animal_type='hamster', pet_name='harry')

函数describe_pet()还是原来那样，但调用这个函数时，我们向Python明确地指出了各个实参对应的形参。看到这个函数调用时，Python知道应该将实参'hamster'和'harry'分别存储在形参animal_type和pet_name中。输出正确无误，它指出我们有一只名为Harry的仓鼠。关键字实参的顺序无关紧要，因为Python知道各个值该存储到哪个形参中。下面两个函数调用是等效的：
::

   describe_pet(animal_type='hamster', pet_name='harry')
   describe_pet(pet_name='harry', animal_type='hamster')

编写函数时，可给每个形参指定默认值。在调用函数中给形参提供了实参时，Python将使用指定的实参值；否则，将使用形参的默认值。因此，给形参指定默认值后，可在函数调用中省略相应的实参。使用默认值可简化函数调用，还可清楚地指出函数的典型用法。

例如，如果你发现调用describe_pet()时，描述的大都是小狗，就可将形参animal_type的默认值设置为'dog'。这样，调用describe_pet()来描述小狗时，就可不提供这种信息
::

   def describe_pet(pet_name, animal_type='dog'):
      """显示宠物的信息"""
      print("\nI have a " + animal_type + ".")
      print("My " + animal_type + "'s name is " + pet_name.title() + ".")
      describe_pet(pet_name='willie')

这里修改了函数describe_pet()的定义，在其中给形参animal_type指定了默认值'dog'。这样，调用这个函数时，如果没有给animal_type指定值，Python将把这个形参设置为'dog'：
::

   I have a dog.
   My dog's name is Willie.

请注意，在这个函数的定义中，修改了形参的排列顺序。由于给animal_type指定了默认值，无需通过实参来指定动物类型，因此在函数调用中只包含一个实参——宠物的名字。然而，Python依然将这个实参视为位置实参，因此如果函数调用中只包含宠物的名字，这个实参将关联到函数定义中的第一个形参。这就是需要将pet_name放在形参列表开头的原因所在。现在，使用这个函数的最简单的方式是，在函数调用中只提供小狗的名字
::

   describe_pet('willie')

如果要描述的动物不是小狗，可使用类似于下面的函数调用：
::

   describe_pet(pet_name='harry', animal_type='hamster')

由于显式地给animal_type提供了实参，因此Python将忽略这个形参的默认值。

基于这种定义，在任何情况下都必须给pet_name提供实参；指定该实参时可以使用位置方式，也可以使用关键字方式。如果要描述的动物不是小狗，还必须在函数调用中给animal_type提供实参；同样，指定该实参时可以使用位置方式，也可以使用关键字方式。下面对这个函数的所有调用都可行：
::

   # 一条名为Willie的小狗
   describe_pet('willie')
   describe_pet(pet_name='willie')
   # 一只名为Harry的仓鼠
   describe_pet('harry', 'hamster')
   describe_pet(pet_name='harry', animal_type='hamster')
   describe_pet(animal_type='hamster', pet_name='harry')

这些函数调用的输出与前面的示例相同。

7.2.3 返回值

函数并非总是直接显示输出，相反，它可以处理一些数据，并返回一个或一组值。函数返回的值被称为返回值。在函数中，可使用return语句将值返回到调用函数的代码行。返回值让你能够将程序的大部分繁重工作移到函数中去完成，从而简化主程序。下面来看一个案例：

【案例7-2】 编写函数接受名和姓并返回完整的姓名

分析：这个函数接收两个参数名和姓。它将姓和名合二为一，在它们之间加上一个空格并将结果返回给调用者。
::

   def get_formatted_name(first_name, last_name):
      """返回整洁的姓名"""
      full_name = first_name + ' ' + last_name
      return full_name.title()
      musician = get_formatted_name('jimi', 'hendrix')
      print(musician)

函数get_formatted_name()的定义通过形参接受名和姓。将姓名组合后将结果存储在变量full_name中。然后，将full_name的值转换为首字母大写格式，并将结果返回到函数调用行。调用返回值的函数时，需要提供一个变量，用于存储返回的值。在这里，将返回值存储在了变量musician中。输出为完整的姓名：
::

   Jimi Hendrix

我们将上面的例子进一步扩展，外国人的姓名可以分为三部分first_name,middle_name,last_name，last_name一般是姓，名字可以由两部分组成first_name和middle_name，具体的要求如下：

【案例7-3】 编写函数接受first_name, middle_name,last_name并返回完整的姓名

分析：有时候，需要让实参变成可选的，这样使用函数的人就只需在必要时才提供额外的信息。可使用默认值来让实参变成可选的。假设我们要扩展函数get_formatted_name()，使其还处理中间名。为此，可将其修改成类似于下面这样：
::

   def get_formatted_name(first_name, middle_name, last_name):
      """返回整洁的姓名"""
      full_name = first_name + ' ' + middle_name + ' ' + last_name
      return full_name.title()
      musician = get_formatted_name('john', 'lee', 'hooker')
      print(musician)

再对这个函数进行优化，目前只要同时提供名、中间名和姓，这个函数就能正确地运行。它根据这三部分创建一个字符串，在适当的地方加上空格，并将结果转换为首字母大写格式。然而，并非所有的人都有中间名，但如果你调用这个函数时只提供了名和姓，它将不能正确地运行。为让中间名变成可选的，可给形参middle_name指定一个默认值——空字符串，并在用户没有提供中间名时不使用这个形参。为让get_formatted_name()在没有提供中间名时依然可行，可给实参middle_name指定一个默认值——空字符串，并将其移到形参列表的末尾：
::

   def get_formatted_name(first_name, last_name, middle_name=''):
      """返回整洁的姓名"""
      if middle_name:
         full_name = first_name + ' ' + middle_name + ' ' + last_name
      else:
         full_name = first_name + ' ' + last_name
         return full_name.title()
      musician = get_formatted_name('jimi', 'hendrix')
      print(musician)
      musician = get_formatted_name('john', 'hooker', 'lee')
      print(musician)

在这个示例中，姓名是根据三个可能提供的部分创建的。由于人都有名和姓，因此在函数定义中首先列出了这两个形参。中间名是可选的，因此在函数定义中最后列出该形参，并将其默认值设置为空字符串。在函数体中，我们检查是否提供了中间名。Python将非空字符串解读为True，因此如果函数调用中提供了中间名，if
middle_name将为True。如果提供了中间名，就将名、中间名和姓合并为姓名，然后将其修改为首字母大写格式，并返回到函数调用行。在函数调用行，将返回的值存储在变量musician中；然后将这个变量的值打印出来。如果没有提供中间名，middle_name将为空字符串，导致if测试未通过，进而执行else代码块：只使用名和姓来生成姓名，并将设置好格式的姓名返回给函数调用行。在函数调用行，将返回的值存储在变量musician中；然后将这个变量的值打印出来。调用这个函数时，如果只想指定名和姓，调用起来将非常简单。如果还要指定中间名，就必须确保它是最后一个实参，这样Python才能正确地将位置实参关联到形参。

函数可返回任何类型的值，包括列表和字典等较复杂的数据结构。例如，下面的函数接受姓名的组成部分，并返回一个表示人的字典：
::

   def build_person(first_name, last_name):
      """返回一个字典，其中包含有关一个人的信息"""
      person = {'first': first_name, 'last': last_name}
      return person
   musician = build_person('jimi', 'hendrix')
   print(musician)

函数build_person()接受名和姓，并将这些值封装到字典中。存储first_name的值时，使用的键为'first'，而存储last_name的值时，使用的键为'last'。最后，返回表示人的整个字典。打印这个返回的值，此时原来的两项文本信息存储在一个字典中：
::

   {'first': 'jimi', 'last': 'hendrix'}

7.2.4 传递可变数量的实参

上面我们已经讨论过各种实参的传递方式，但是我们经常有些需求，对参数的个数要求是可变的，并不能确定有几个参数，对于这种需求，就需要我们传递参数时做一些特殊的处理，例如将列表传递给函数后，函数就可对其进行修改。在函数中对这个列表所做的任何修改都是永久性的，这让你能够高效地处理大量的数据。

【案例7-4】
一家为用户提交的设计制作3D打印模型的公司。需要打印的设计存储在一个列表中，打印后移到另一个列表中。

分析：传统的编程方式可以不使用函数实现这一需求，具体代码如下：

# 首先创建一个列表，其中包含一些要打印的设计
::

   unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
   completed_models = []

   # 模拟打印每个设计，直到没有未打印的设计为止
   # 打印每个设计后，都将其移到列表completed_models中
   while unprinted_designs:
      current_design = unprinted_designs.pop()
   #模拟根据设计制作3D打印模型的过程
   print("Printing model: " + current_design)
   completed_models.append(current_design)
   # 显示打印好的所有模型
   print("\nThe following models have been printed:")
   for completed_model in completed_models:
      print(completed_model)

这个程序首先创建一个需要打印的设计列表，还创建一个名为completed_models的空列表，每个设计打印都将移到这个列表中。只要列表unprinted_designs中还有设计，while循环就模拟打印设计的过程：从该列表末尾删除一个设计，将其存储到变量current_design中，并显示一条消息，指出正在打印当前的设计，再将该设计加入到列表completed_models中。循环结束后，显示已打印的所有设计：
::

   Printing model: dodecahedron
   Printing model: robot pendant
   Printing model: iphone case
   The following models have been printed:
   dodecahedron
   robot pendant
   iphone case

为重新组织这些代码，我们可编写两个函数，每个都做一件具体的工作。大部分代码都与原来相同，只是效率更高。第一个函数将负责处理打印设计的工作，而第二个将概述打印了哪些设计：
::

   def print_models(unprinted_designs, completed_models):
      """
      模拟打印每个设计，直到没有未打印的设计为止
      打印每个设计后，都将其移到列表completed_models中
      """
      while unprinted_designs:
         current_design = unprinted_designs.pop()
         # 模拟根据设计制作3D打印模型的过程
         print("Printing model: " + current_design)
         completed_models.append(current_design)
   def show_completed_models(completed_models):
      """显示打印好的所有模型"""
      print("\nThe following models have been printed:")
      for completed_model in completed_models:
         print(completed_model)
         unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
         completed_models = []
         print_models(unprinted_designs, completed_models)
         show_completed_models(completed_models)

在上面，我们定义了函数print_models()，它包含两个形参：一个需要打印的设计列表和一个打印好的模型列表。给定这两个列表，这个函数模拟打印每个设计的过程：将设计逐个地从未打印的设计列表中取出，并加入到打印好的模型列表中。我们定义了函数show_completed_models()，它包含一个形参：打印好的模型列表。给定这个列表，函数show_completed_models()显示打印出来的每个模型的名称。这个程序的输出与未使用函数的版本相同，但组织更为有序。完成大部分工作的代码都移到了两个函数中，让主程序更容易理解。只要看看主程序，你就知道这个程序的功能容易看清得多：
::

   unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
   completed_models = []
   print_models(unprinted_designs, completed_models)
   show_completed_models(completed_models)

我们创建了一个未打印的设计列表，还创建了一个空列表，用于存储打印好的模型。接下来，由于我们已经定义了两个函数，因此只需调用它们并传入正确的实参即可。我们调用print_models()并向它传递两个列表；像预期的一样，print_models()模拟打印设计的过程。接下来，我们调用show_completed_models()，并将打印好的模型列表传递给它，让其能够指出打印了哪些模型。描述性的函数名让别人阅读这些代码时也能明白，虽然其中没有任何注释。相比于没有使用函数的版本，这个程序更容易扩展和维护。如果以后需要打印其他设计，只需再次调用print_models()即可。如果我们发现需要对打印代码进行修改，只需修改这些代码一次，就能影响所有调用该函数的地方；与必须分别修改程序的多个地方相比，这种修改的效率更高。

这个程序还演示了这样一种理念，即每个函数都应只负责一项具体的工作。第一个函数打印每个设计，而第二个显示打印好的模型；这优于使用一个函数来完成两项工作。编写函数时，如果你发现它执行的任务太多，请尝试将这些代码划分到两个函数中。别忘了，总是可以在一个函数中调用另一个函数，这有助于将复杂的任务划分成一系列的步骤。

【案例7-5】一个制作比萨的函数，它需要接受很多配料，但你无法预先确定顾客要多少种配料，函数内打印所有的配料信息。

分析：生活中经常会遇到这种不确定性的问题，例如题目中的配料的个数，那就需要程序能够适应这些变化，好在Python为我们提供了传入可变数量的参数的方式。下面的函数只有一个形参*toppings，但不管调用语句提供了多少实参，这个形参都将它们统统收入囊中：
::

   def make_pizza(*toppings):
      """打印顾客点的所有配料"""
      print(toppings)
      make_pizza('pepperoni')
      make_pizza('mushrooms', 'green peppers', 'extra cheese')

形参名*toppings中的星号让Python创建一个名为toppings的空元组，并将收到的所有值都封装到这个元组中。函数体内的print语句通过生成输出来证明Python能够处理使用一个值调用函数的情形，也能处理使用三个值来调用函数的情形。它以类似的方式处理不同的调用，注意，Python将实参封装到一个元组中，即便函数只收到一个值也如此：
::

   ('pepperoni',)
   ('mushrooms', 'green peppers', 'extra cheese')

现在，我们可以将这条print语句替换为一个循环，对配料列表进行遍历，并对顾客点的比萨进行描述：
::

   def make_pizza(*toppings):
      """概述要制作的比萨"""
      print("\nMaking a pizza with the following toppings:")
      for topping in toppings:
         print("- " + topping)
         make_pizza('pepperoni')
         make_pizza('mushrooms', 'green peppers', 'extra cheese')
不管收到的是一个值还是三个值，这个函数都能妥善地处理，不管函数收到的实参是多少个，这种语法都管用。
::

   Making a pizza with the following toppings:
   - pepperoni
   Making a pizza with the following toppings:
   - mushrooms
   - green peppers
   - extra cheese

7.3 将函数存储在模块中
----------------------

函数的优点之一是，使用它们可将代码块与主程序分离。通过给函数指定描述性名称，可让主程序容易理解得多。你还可以更进一步，将函数存储在被称为模块的独立文件中，再将模块导入到主程序中。import语句允许在当前运行的程序文件中使用模块中的代码。

通过将函数存储在独立的文件中，可隐藏程序代码的细节，将重点放在程序的高层逻辑上。

这还能让你在众多不同的程序中重用函数。将函数存储在独立文件中后，可与其他程序员共享这些文件而不是整个程序。知道如何导入函数还能让你使用其他程序员编写的函数库。

导入模块的方法有多种，下面作简要介绍。

7.3.1 导入模块

要让函数是可导入的，得先创建模块。模块是扩展名为.py的文件，包含要导入到程序中的代码。

【案例7-6】将上节的制作比萨的函数放入模块，在新的程序中导入模块，使用模块中的制作比萨的函数。

分析：首先要创建一个包含函数make_pizza()的模块。为此，我们将文件pizza.py中除函数make_pizza()之外的其他代码都删除，剩下函数主体部分如下：
::

   **pizza.py**
   def make_pizza(*toppings):
      """概述要制作的比萨"""
      print("\nMaking a pizza with the following toppings:")
      for topping in toppings:
         print("- " + topping)
接下来，我们在pizza.py所在的目录中创建另一个名为making_pizzas.py的文件，这个文件导入刚创建的模块，再调用make_pizza()两次
::
 
   **making_pizzas.py**
   import pizza
   pizza.make_pizza(16, 'pepperoni')
   pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

Python读取这个文件时，代码行import
pizza让Python打开文件pizza.py，并将其中的所有函数都复制到这个程序中。你看不到复制的代码，因为这个程序运行时，Python在幕后复制这些代码。你只需知道，在making_pizzas.py中，可以使用pizza.py中定义的所有函数。要调用被导入的模块中的函数，可指定导入的模块的名称pizza和函数名make_pizza()，并用句点分隔它们。这些代码的输出与没有导入模块的原始程序相同：
::

   Making a 16-inch pizza with the following toppings:
   - pepperoni
   Making a 12-inch pizza with the following toppings:
   - mushrooms
   - green peppers
   - extra cheese

这就是一种导入方法：只需编写一条import语句并在其中指定模块名，就可在程序中使用该模块中的所有函数。如果你使用这种import语句导入了名为module_name.py的整个模块，就可使用下面的语法来使用其中任何一个函数
::

   import module_name
   module_name.function_name()

你还可以导入模块中的特定函数，这种导入方法的语法如下：
::

   from module_name import function_name

通过用逗号分隔函数名，可根据需要从模块中导入任意数量的函数：
::

   from module_name import function_0, function_1, function_2

对于前面的making_pizzas.py示例，如果只想导入要使用的函数，代码将类似于下面这样：
::

   **making_pizzas.py**
   from pizza import make_pizza
   make_pizza(16, 'pepperoni')
   make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

若使用这种语法，调用函数时就无需使用句点。由于我们在import语句中显式地导入了函数make_pizza()，因此调用它时只需指定其名称。

这里要注意在引用时不要加“py”，不能写成import myModule.py，被引用的模块要放在与引用程序相同的目录下，或者放在Python能够找到的目录下，如果被引用的模块和当前模块不在同一目录，需要增加目录名，例如：
::

   from directories.module_name import function_name

7.3.2 使用as指定别名

如果要导入的函数的名称可能与程序中现有的名称冲突，或者函数的名称太长，可指定简短而独一无二的别名——函数的另一个名称，类似于外号。要给函数指定这种特殊外号，需要在导入它时这样做。

下面给函数make_pizza()指定了别名mp()。这是在import语句中使用make_pizza
as mp实现的，关键字as将函数重命名为你提供的别名：
::

   from pizza import make_pizza as mp
   mp(16, 'pepperoni')
   mp(12, 'mushrooms', 'green peppers', 'extra cheese')

上面的import语句将函数make_pizza()重命名为mp()；在这个程序中，每当需要调用
make_pizza()时，都可简写成mp()，而Python将运行make_pizza()中的代码，这可避免与这个程序可能包含的函数make_pizza()混淆。指定别名的通用语法如下：
::

   from module_name import function_name as fn

你还可以给模块指定别名。通过给模块指定简短的别名（如给模块pizza指定别名p），让你能够更轻松地调用模块中的函数。相比于pizza.make_pizza()，p.make_pizza()更为简洁：
::

   import pizza as p
   p.make_pizza(16, 'pepperoni')
   p.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

上述import语句给模块pizza指定了别名p，但该模块中所有函数的名称都没变。调用函数make_pizza()时，可编写代码p.make_pizza()而不是pizza.make_pizza()，这样不仅能使代码更简洁，还可以让你不再关注模块名，而专注于描述性的函数名。这些函数名明确地指出了函数的功能，对理解代码而言，它们比模块名更重要。给模块指定别名的通用语法如下：
::

   import module_name as mn

7.4 全局变量和局部变量
----------------------

你可能已经注意到，有些变量在函数之外，还有一些变量在函数内部。那么这些变量之间有什么关系，怎样在函数内使用外部的变量，下面将对这些知识做具体的介绍。

7.4.1 变量作用域

之前我们讲过变量，但变量是什么时候创建的呢，对于函数而言，函数内的变量只是在函数运行时才会创建。在函数运行之前或者完成运行之后甚至根本不存在。Python
提供了内存管理，可以自动完成这个工作。Python
在函数运行时会创建新的变量在函数内使用，当函数完成时会把它们删除。最后这部分很重要：函数运行结束时，其中的所有变量都不再存在。函数运行时，函数之外的变量被搁置一边，函数内部的变量会被用到。所以程序中使用（或者可以使用）变量的部分称为这个变量的作用域。

7.4.2 局部变量

局部变量也成为内部变量。局部变量是在函数内作定义说明的，其作用域仅限于函数内，离开了函数后再使用这种变量是非法的。

【案例7-7】局部变量的使用，编写一个求和函数。

分析：设计一个函数传入参数m，函数对1+2+3+...+m求和，这里应该会用到循环具体代码如下：
::

   def sum(m):
      s=0
      # 计算1+2+3+...+m的和
      for p in range(m+1)：
         s=s+p
         return s
         m=10
         s=sum(m)
      print(s)

其函数中的m，p，s变量都是局部变量，注意函数中定义的变量只能在函数中使用，不能在其他函数中使用，同时一个函数中也不能使用其他函数中定义的变量，各个函数之间是平行的关系，每个函数都封装了自己的区域，互补干扰。形参变量是属于被调用函数的局部变量，而实参变量是属于调用函数的局部变量。允许在不同的函数中使用相同的变量名，但是他们代表的是不同的对象，分配不同的存储单元，互不干扰，也不会发生混淆，在本例中sum函数的m、s变量和主程序的m、s变量同名，但是他们是不同的变量。

7.4.3 全局变量

如果一个函数内部要用到主程序的变量，那么可以在该函数内部声明这个变量为global变量，这样函数内部使用的这个变量就是主程序的变量，当在函数改变了全局变量的值的时候，会直接影响主程序中的变量的值。例如下面这个例子：
::

   def A(x):
      global y
      y=0
      x=0
   def B(x):
      global y
      y=10
      x=0
      x=1
      y=2
      A(x)
      B(x)
   print(x,y)

在A，B函数中都使用了global y声明A，B中使用的y不是本地的y变量而是主程序的y变量，所以执行结果为：110。

这里要注意全局变量的作用域是整个程序，它在程序开始时就存在，任何函数都可以访问它，而且所有函数访问的同名称的全局变量是用一个变量，全局变量只有在程序结束时才销毁，局部变量是函数内部范围内的变量，当执行此函数时才有效，退出函数后局部变量就被销毁。不同函数之间的局部变量是不同的，即使同名的也互不相干。

局部变量有局部性，这使得函数有独立性，函数与外界的接口只有函数参数与它的返回值，使程序的模块化更突出，这样有利于开发大型的程序。

全局变量具有全局性，是实现函数之间数据交换的公共途径，但大量的使用全局变量会破坏函数的独立性，导致程序的模块化程度下降，因此要尽量减少使用全局变量，多使用局部变量，函数之间应尽量保持独立性，建议在函数之间只通过接口参数来传递数据。

7.5 制作2048游戏
----------------

《2048》是一款热门的数字益智游戏，最早于2014年3月20日发行。原版《2048》首先在GitHub网站上发布，后被移植到各个平台。这款游戏是基于《1024》和《小传奇》的玩法开发而成的新型数字游戏，游戏规则很简单，操作容易，玩家要想办法不断的叠加最终拼凑出2048这个数字就算成功。

7.5.1 预备知识

游戏的画面很简单，如图7-2所示，界面包含16个方格，当网格出现初始数字之后即可以开始游戏，整体格调简单。

.. image:: /Chapter/picture/image105.png

图7-2 游戏界面

游戏的玩法规则也非常的简单，一开始方格内会出现2或者4等这两个小数字，玩家只需要上下左右其中一个方向来移动出现的数字，所有的数字就会向滑动的方向靠拢，相同的数字相撞时会叠加靠拢，如图7-3、7-4所示。

.. image:: /Chapter/picture/image106.png

图7-3 右移变化 

.. image:: /Chapter/picture/image107.png

图7-4 左移变化


而滑出的空白方块就会随机出现一个数字如图7-5所示，然后一直这样，不断的叠加最终拼凑出2048这个数字就算成功。

.. image:: /Chapter/picture/image108.png

图7-5 下移的同时随机产生2和4

7.5.2 任务要求

1. 界面绘制：生成2048的游戏界面；

2. 按键控制：四个按键是方向键，分别代表上下左右；

3. 游戏控制：游戏不间断运行，当触发按键时计算相应的值并控制界面变化，统计新的总分数，当达成胜利条件或失败条件时结束游戏；

4. 胜利条件：当出现2048这个数字时游戏胜利并结束；

5. 失败条件：棋盘填满数字，无法再进行变换，也就是变换之后的矩阵和变换前的相同，则游戏结束；

7.5.3 任务实施

1. 网格类

构造Grid类，主要功能是绘制背景及网格、得分情况信息，并提供了在网格中绘制数字的方法，更新网格下方得分的方法。
::

   class Grid(object):
      def __init__(self, master = None, x = 10, y = 10, w = 222, h = 222):
         self.x = x
         self.y = y
         self.w = w
         self.h = h
         self.width = w//35 - 1
         self.height = h//55 - 1
         self.bg = 0x000000
         print(self.width, self.height)
         #画背景
         for i in range(320):
            screen.drawline(0, i, 239, i, 1, self.bg)
            self.initial()

在构造函数__init__()中，调用了screen.drawline函数来画直线，通过循环画出最外层的边框。
::

   def initial(self):
      for i in range(0, 4):
         for j in range(0, 4):
            x = i * 55 + self.x + 1
            y = j * 55 + self.y + 1
            #画边界
            screen.drawline(x,y,x + 55 - 1,y,1, 0xFFFFFF)
            screen.drawline(x + 55 - 1,y,x + 55 - 1, y + 55,1,0xFFFFFF)
            screen.drawline(x,y + 55,x + 55 - 1,y + 55,1, 0xFFFFFF)
            screen.drawline(x,y,x,y + 55, 1,0xFFFFFF)
            
initial主要实现画内部的棋盘，通过双重循环画出网格状棋盘。
::
   
   def draw(self, pos, color, num):
       x = pos[0] * 55 + self.x
       y = pos[1] * 55 + self.y
       text.draw("", x + 3, y + 19, color, 0x000000)
       if num < 16:
          text.draw(str(num), x + 19, y + 19, color, 0x000000)
       elif num < 128:
          text.draw(str(num), x + 11, y + 19, color, 0x000000)
       elif num < 1024:
          text.draw(str(num), x + 3, y + 19, color, 0x000000)
       elif num == 1024:
          text.draw("1K", x + 11, y + 19, color, 0x000000)
       else:
          text.draw("2K", x + 11, y + 19, color, 0x000000)

draw方法是将pos列表中的两个值转换成实际屏幕坐标，再在这个坐标上显示传入的num数字，但是数字长度不一，会根据数字长度对实际坐标位置进行修正。
::

   def printscore(self, msg, score):
      print(msg + str(score))
      text.draw(msg + str(score), 20, 250, 0xFF0000, 0x000000)

printscore方法主要是将当前成绩score显示在屏幕网格下方。

2. 矩阵类

矩阵类Matrix，是游戏的主要实现类。实际网格中的数字可以看做一个4*4的矩阵，对网格的上下左右的移动就是对矩阵的操作，矩阵根据算法产生变化，在矩阵变化的同时要计算网格中应该显示数字，再将数字显示到网格中。这样就完成了游戏的互动操作。
::

   class Matrix(object):
      def __init__(self, grid):
         self.grid = grid
         self.matrix = [[0 for i in range(4)] for i in range(4)]
         self.matrix_o = [[0 for i in range(4)] for i in range(4)]
         self.vacancy = []
         self.gamewin = False
         #使用一个字典将数字与其对应的颜色存放起来
         self.color ={
         0 : 0xFFFFFF,
         2 : 0x000099,
         4 : 0x009900,
         8 : 0x990000,
         16 : 0x999900,
         32 : 0x990099,
         64 : 0x00FFFF,
         128 : 0x0000FF,
         256 : 0x00FF00,
         512 : 0xFF0000,
         1024 : 0xFFFF00,
         2048 : 0xFF00FF
         }

__init__函数主要进行初始化操作，初始化矩阵，字体颜色，0值的列表，胜利标志等参数。
::

   def void(self):
      self.vacancy = []
      for x in range(0, 4):
         for y in range(0, 4):
            if self.matrix[x][y] == 0:
               self.vacancy.append((x, y))
               return len(self.vacancy)
   
void方法主要是双重循环遍历矩阵，当发现值为0的点时将坐标加到vacancy列表中。
::

   def generate(self):
      pos = choice(self.vacancy)
      if randint(0, 5) == 4:
         self.matrix[pos[0]][pos[1]] = 4
      else:
         self.matrix[pos[0]][pos[1]] = 2
         del self.vacancy[self.vacancy.index((pos[0], pos[1]))]

generate方法在vacancy列表中取随机的点，并根据随机数的值来判断生成的是2还是4，并将vacancy列表删除新生成的点的坐标。
::

   def draw(self):
      for i in range (0, 4):
         for j in range (0, 4):
            pos = (i, j)
            num = self.matrix[i][j]
            color = self.color[int(self.matrix[i][j])]
            self.grid.draw(pos, color, num)
   
draw方法就是遍历矩阵，通过调用grid类的draw方法将矩阵中的数据显示到网格中。
::

   def initial(self):
      self.matrix = [[0 for i in range(4)] for i in range(4)]
      self.void()
      self.generate()
      self.generate()
      self.draw()
      self.gamewin = False
      for i in range(0, 4):
         for j in range(0, 4):
            self.matrix_o[i][j] = self.matrix[i][j]

initial方法综合调用前面定义的各种方法，初始化矩阵，并收集0值列表，产生两个随机的2或者4放入0值位置上，并调用draw在网格中显示矩阵，并将当前矩阵记录在原始矩阵matrix_o中。
::

   def up(self):
      ss = 0
      for i in range(0, 4):
         for j in range(0, 3):
            s = 0
            if not self.matrix[i][j] == 0:
               for k in range(j + 1, 4):
                if not self.matrix[i][k] == 0:
                  if self.matrix[i][j] == self.matrix[i][k]:
                     ss = ss + self.matrix[i][k]
                     self.matrix[i][j] = self.matrix[i][j] * 2
                     if self.matrix[i][j] == 2048:
                           self.gamewin = True
                           self.matrix[i][k] = 0
                           s = 1
                           break
                     else:
                           break
              if s == 1:
                   break
     for i in range(0, 4):
         s = 0
         for j in range(0, 3):
            if self.matrix[i][j - s] == 0:
               self.matrix[i].pop(j - s)
               self.matrix[i].append(0)
               s = s + 1
      return ss

up函数实现点击向上按钮之后的矩阵变换。首先循环遍历所有的点，s为判断标志用来跳出循环，当发现某个位置的值不为0时，循环遍历这列当前节点之下的所有位置，当发现临近的点的值和当前的值相等时则当前值翻倍，当到达2048时则结束游戏。然后重新调整矩阵，将矩阵上移，并将值为0的点删除，在底部用0补全如图7-6所示。

.. image:: /Chapter/picture/image136.jpg

图7-6 上移矩阵变化
::

   def down(self):
      for i in range(0, 4):
         self.matrix[i].reverse()
         ss = self.up()
      for i in range(0, 4):
         self.matrix[i].reverse()
      return ss

下移过程将矩阵颠倒，然后调用上移方法，完成后再颠倒过来。
::

   def left(self):
      ss = 0
      for i in range(0, 4):
         for j in range(0, 3):
            s = 0
            if not self.matrix[j][i] == 0:
               for k in range(j + 1, 4):
                  if not self.matrix[k][i] == 0:
                     if self.matrix[j][i] == self.matrix[k][i]:
                        ss = ss + self.matrix[k][i]
                        self.matrix[j][i] = self.matrix[j][i] * 2
                        if self.matrix[j][i] == 2048:
                           self.gamewin = True
                           self.matrix[k][i] = 0
                           s = 1
                           break
                     else:
                        break
               if s == 1:
                  break
      for i in range(0, 4):
         s = 0
         for j in range(0, 3):
            if self.matrix[j - s][i] == 0:
               for k in range(j - s, 3):
                  self.matrix[k][i] = self.matrix[k + 1][i]
                  self.matrix[3][i] = 0
                  s = s + 1
          return ss
   def right(self):
      ss = 0
      for i in range(0, 4):
         for j in range(0, 3):
            s = 0
            if not self.matrix[3-j][i] == 0:
               k = 3-j-1
               while k >= 0:
                  if not self.matrix[k][i] == 0:
                     if self.matrix[3-j][i] == self.matrix[k][i]:
                        ss = ss + self.matrix[k][i]
                        self.matrix[3-j][i] = self.matrix[3-j][i] * 2
                        if self.matrix[3-j][i] == 2048:
                           self.gamewin = True
                           self.matrix[k][i] = 0
                           s = s+1
                           break
                     else:
                        break
                  k = k -1
         if s == 1:
            break
      for i in range(0, 4):
         s = 0
         for j in range(0, 3):
            if self.matrix[3 - j + s][i] == 0:
               k = 3 - j + s
               while k > 0:
                  self.matrix[k][i] = self.matrix[k - 1][i]
                  k = k - 1
                  self.matrix[0][i] = 0
                  s = s + 1
      return ss

矩阵左移和右移方式和上移相似，就不再具体描述了。

3. 游戏类

游戏类主要是负责按键控制的对应操作，同时聚合了上面两个类。
::

   class Game():
      def __init__(self):
         self.grid = Grid()
         self.matrix = Matrix(self.grid)
         self.status = ['run', 'stop']
         #界面左侧显示分数
         self.initial()
初始化当前状态，聚合网格类和矩阵类。
::

   def initial(self):
      self.score = 0
      self.grid.printscore("成绩为：", self.score)
      self.matrix.initial()
   
初始化成绩并显示，初始化矩阵
::

   def key_release(self, key):
      keymatch=["Down", "Left", "Up", "Right"]
      if keymatch[key] == "Up":
         ss = self.matrix.up()
         self.run(ss)
      elif keymatch[key] == "Down":
         ss = self.matrix.down()
         self.run(ss)
         elif keymatch[key] == "Left":
            ss = self.matrix.left()
            self.run(ss)
         elif keymatch[key] == "Right":
            ss = self.matrix.right()
            self.run(ss)

按键控制不同的按键对应调用矩阵类的不同的变换。
::

   def run(self, ss):
      if not self.matrix.matrix == self.matrix.matrix_o:
         self.score = self.score + int(ss)
         self.grid.printscore("成绩为：", self.score)
         if self.matrix.gamewin == True:
            self.matrix.draw()
            self.grid.printscore("恭喜获胜，成绩为：", self.score)
            if message == 'ok':
            self.initial()
         else:
            self.matrix.void()
            self.matrix.generate()
            for i in range(0, 4):
               for j in range(0, 4):
               self.matrix.matrix_o[i][j] = self.matrix.matrix[i][j]
               self.matrix.draw()
      else:
         v = self.matrix.void()
         if v < 1:
            self.grid.printscore("你输了，成绩为：", self.score)

Run方法首先判判断变换前后是否相同，相同则游戏失败，不同，则判断是否已经生成2048达成胜利条件，如果没有则继续生成随机的2或4，记录当前的矩阵到matrix_o中。

4. 主循环

主循环是游戏的入口，开始后不断循环监听按键输入，并调用游戏类的按键处理方法。
::

   if __name__ == '__main__':
      game = Game()
      while True:
         gc.collect()
         i = 0
         j = -1
         for k in keys:
            if k.value() == 0:
            if i != j:
               print("i=", i)
               print("j=", j)
               j = i
               game.key_release(i)
               i = i+ 1
            if i > 3:
               i = 0
               time.sleep_ms(125)

.. _本章小结-6:

7.6 本章小结
------------

在本章节中，主要学习了Python语言中的函数以及如何传递实参，让函数能够访问完成其工作所需的信息，如何使用实参和形参，以及如何接受任意数量的实参，输出函数的返回值，如何将函数放入模块，以及全局变量和局部变量的区别，通过制作2048游戏了解了函数及变量在游戏中的具体使用。

函数是经常使用的一种编程方法。它使代码的重复利用率得以提高，使编程更有效率，程序更加模块化，便于后期维护和升级。

.. _练习题目-6:

7.7 练习题目
------------

| 1. 编写一个名为collatz()的函数,它有一个名为number的参数
| 如果参数是偶数,那么collatz()就打印出number//2
| 如果number是奇数,那么collatz()就打印3*number+1

2. 编写一个函数cacluate,
可以接收任意多个数，返回的是一个元组。元组的第一个值为所有参数的平均值,
第二个值是大于平均值的所有数。

3. 编写函数, 接收一个列表(包含10个整形数)和一个整形数k, 返回一个新列表。

函数需求：将列表下标k之前对应(不包含k)的元素逆序；将下标k及之后的元素逆序；

5. 模拟轮盘抽奖游戏

轮盘分为三部分: 一等奖, 二等奖和三等奖;

轮盘转的时候是随机的：

如果范围在[0,0.08)之间,代表一等奖。

如果范围在[0.08,0.3)之间,代表2等奖。

如果范围在[0, 1.0)之间,代表3等奖。

模拟本次活动1000人参加, 输出游戏时需要准备各等级奖品的个数。
