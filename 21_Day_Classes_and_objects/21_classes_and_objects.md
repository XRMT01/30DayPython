<div align="center">
  <h1> 30 Days Of Python: Day 21 - Classes and Objects</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

<sub>Author:
<a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
<small>Second Edition: July, 2021</small>
</sub>

</div>

[<< 第二十天](../20_Day_Python_package_manager/20_python_package_manager.md) | [第二十二天 >>](../22_Day_Web_scraping/22_web_scraping.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 第二十一天](#-day-21)
  - [Classes and Objects](#classes-and-objects)
    - [Creating a Class](#creating-a-class)
    - [Creating an Object](#creating-an-object)
    - [Class Constructor](#class-constructor)
    - [Object Methods](#object-methods)
    - [Object Default Methods](#object-default-methods)
    - [Method to Modify Class Default Values](#method-to-modify-class-default-values)
    - [Inheritance](#inheritance)
    - [Overriding parent method](#overriding-parent-method)
  - [💻 Exercises: Day 21](#-exercises-day-21)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)
    - [Exercises: Level 3](#exercises-level-3)

# 📘 第二十一天

## Classes and Objects

Python是一种面向对象的编程语言。Python中的一切都是一个对象，有它的属性和方法。程序中使用的数字、字符串、列表、字典、元组、集合等是相应内置类的对象。我们创建类来创建对象。类就像一个对象构造函数，或者是创建对象的“蓝图”。我们实例化一个类来创建一个对象。类定义了对象的属性和行为，而对象则表示类。

我们从一开始就在不知不觉中处理类和对象。Python程序中的每个元素都是类的对象。
让我们检查一下python中的所有内容是否都是类：

```py
asabeneh@Asabeneh:~$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> num = 10
>>> type(num)
<class 'int'>
>>> string = 'string'
>>> type(string)
<class 'str'>
>>> boolean = True
>>> type(boolean)
<class 'bool'>
>>> lst = []
>>> type(lst)
<class 'list'>
>>> tpl = ()
>>> type(tpl)
<class 'tuple'>
>>> set1 = set()
>>> type(set1)
<class 'set'>
>>> dct = {}
>>> type(dct)
<class 'dict'>
```

### 创建类

要创建一个类，我们需要关键字**class**，后跟名称和冒号。类名应为**CamelCase**。

```sh
# syntax
class ClassName:
  code goes here
```

**Example:**

```py
class Person:
  pass
print(Person)
```

```sh
<__main__.Person object at 0x10804e510>
```

### 创建对象

我们可以通过调用类来创建对象。

```py
p = Person()
print(p)
```

### 类构造函数

在上面的示例中，我们从Person类创建了一个对象。然而，没有构造函数的类在实际应用程序中并没有真正的用处。让我们使用构造函数使我们的类更有用。与Java或JavaScript中的构造函数一样，Python也有一个内置的**__init__**（）构造函数。**__init__**构造函数具有self参数，该参数是对类当前实例的引用
**示例：**

```py
class Person:
      def __init__ (self, name):
        # self allows to attach parameter to the class
          self.name =name

p = Person('Asabeneh')
print(p.name)
print(p)
```

```sh
# output
Asabeneh
<__main__.Person object at 0x2abf46907e80>
```

让我们向构造函数添加更多参数。

```py
class Person:
      def __init__(self, firstname, lastname, age, country, city):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city


p = Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
print(p.firstname)
print(p.lastname)
print(p.age)
print(p.country)
print(p.city)
```

```sh
# output
Asabeneh
Yetayeh
250
Finland
Helsinki
```

### 对象方法

对象可以有方法。方法是属于对象的函数。

**示例:**

```py
class Person:
      def __init__(self, firstname, lastname, age, country, city):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city
      def person_info(self):
        return f'{self.firstname} {self.lastname} is {self.age} years old. He lives in {self.city}, {self.country}'

p = Person('Asabeneh', 'Yetayeh', 250, 'Finland', 'Helsinki')
print(p.person_info())
```

```sh
# output
Asabeneh Yetayeh is 250 years old. He lives in Helsinki, Finland
```

### 对象默认方法

有时，您可能希望为对象方法设置默认值。如果我们在构造函数中为参数提供默认值，我们就可以避免在没有参数的情况下调用或实例化类时出错。让我们看看它是什么样子的：

**Example:**

```py
class Person:
      def __init__(self, firstname='Asabeneh', lastname='Yetayeh', age=250, country='Finland', city='Helsinki'):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city

      def person_info(self):
        return f'{self.firstname} {self.lastname} is {self.age} years old. He lives in {self.city}, {self.country}.'

p1 = Person()
print(p1.person_info())
p2 = Person('John', 'Doe', 30, 'Nomanland', 'Noman city')
print(p2.person_info())
```

```sh
# output
Asabeneh Yetayeh is 250 years old. He lives in Helsinki, Finland.
John Doe is 30 years old. He lives in Noman city, Nomanland.
```

### 修改类默认值的方法

在下面的示例中，person类的所有构造函数参数都有默认值。除此之外，我们还有技能参数，我们可以使用方法访问它。让我们创建add_skill方法将技能添加到技能列表中。

```py
class Person:
      def __init__(self, firstname='Asabeneh', lastname='Yetayeh', age=250, country='Finland', city='Helsinki'):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city
          self.skills = []

      def person_info(self):
        return f'{self.firstname} {self.lastname} is {self.age} years old. He lives in {self.city}, {self.country}.'
      def add_skill(self, skill):
          self.skills.append(skill)

p1 = Person()
print(p1.person_info())
p1.add_skill('HTML')
p1.add_skill('CSS')
p1.add_skill('JavaScript')
p2 = Person('John', 'Doe', 30, 'Nomanland', 'Noman city')
print(p2.person_info())
print(p1.skills)
print(p2.skills)
```

```sh
# output
Asabeneh Yetayeh is 250 years old. He lives in Helsinki, Finland.
John Doe is 30 years old. He lives in Noman city, Nomanland.
['HTML', 'CSS', 'JavaScript']
[]
```

### 继承

使用继承，我们可以重用父类代码。继承允许我们定义一个从父类继承所有方法和属性的类。父类或超类或基类是提供所有方法和属性的类。子类是从另一个类或父类继承的类。
让我们通过继承人类来创建一个学生类。

```py
class Student(Person):
    pass


s1 = Student('Eyob', 'Yetayeh', 30, 'Finland', 'Helsinki')
s2 = Student('Lidiya', 'Teklemariam', 28, 'Finland', 'Espoo')
print(s1.person_info())
s1.add_skill('JavaScript')
s1.add_skill('React')
s1.add_skill('Python')
print(s1.skills)

print(s2.person_info())
s2.add_skill('Organizing')
s2.add_skill('Marketing')
s2.add_skill('Digital Marketing')
print(s2.skills)

```

```sh
output
Eyob Yetayeh is 30 years old. He lives in Helsinki, Finland.
['JavaScript', 'React', 'Python']
Lidiya Teklemariam is 28 years old. He lives in Espoo, Finland.
['Organizing', 'Marketing', 'Digital Marketing']
```

我们没有在子类中调用**__init__**（）构造函数。如果我们没有调用它，那么我们仍然可以从父级访问所有属性。但是，如果我们确实调用了构造函数，我们可以通过调用_super_来访问父属性。
我们可以向子类添加一个新方法，也可以通过在子类中创建相同的方法名来覆盖父类方法。当我们添加**__init__**（）函数时，子类将不再继承父类的**__init__**（）功能。

### 覆盖父类方法

```py
class Student(Person):
    def __init__ (self, firstname='Asabeneh', lastname='Yetayeh',age=250, country='Finland', city='Helsinki', gender='male'):
        self.gender = gender
        super().__init__(firstname, lastname,age, country, city)
    def person_info(self):
        gender = 'He' if self.gender =='male' else 'She'
        return f'{self.firstname} {self.lastname} is {self.age} years old. {gender} lives in {self.city}, {self.country}.'

s1 = Student('Eyob', 'Yetayeh', 30, 'Finland', 'Helsinki','male')
s2 = Student('Lidiya', 'Teklemariam', 28, 'Finland', 'Espoo', 'female')
print(s1.person_info())
s1.add_skill('JavaScript')
s1.add_skill('React')
s1.add_skill('Python')
print(s1.skills)

print(s2.person_info())
s2.add_skill('Organizing')
s2.add_skill('Marketing')
s2.add_skill('Digital Marketing')
print(s2.skills)
```

```sh
Eyob Yetayeh is 30 years old. He lives in Helsinki, Finland.
['JavaScript', 'React', 'Python']
Lidiya Teklemariam is 28 years old. She lives in Espoo, Finland.
['Organizing', 'Marketing', 'Digital Marketing']
```

我们可以使用super（）内置函数或父名称Person来自动继承其父对象的方法和属性。在上面的例子中，我们重写了父方法。child方法有一个不同的特点，它可以识别性别是男性还是女性，并指定适当的代词（He/She）。

🌕 现在，你完全掌握了编程的超能力。现在做一些锻炼你的大脑和肌肉。

## 💻 练习：第21天

### 练习：1级

1. Python有一个名为_statistics_的模块，我们可以使用这个模块进行所有的统计计算。然而，为了学习如何制作函数和重用函数，让我们尝试开发一个程序，该程序计算样本的集中趋势度量（均值、中位数、众数）和变异性度量（范围、方差、标准差）。除了这些测量值外，还要找到样本的最小值、最大值、计数、百分位数和频率分布。您可以创建一个名为Statistics的类，并创建所有执行统计计算的函数作为Statistics类的方法。检查下面的输出。

```py
ages = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

print('Count:', data.count()) # 25
print('Sum: ', data.sum()) # 744
print('Min: ', data.min()) # 24
print('Max: ', data.max()) # 38
print('Range: ', data.range() # 14
print('Mean: ', data.mean()) # 30
print('Median: ', data.median()) # 29
print('Mode: ', data.mode()) # {'mode': 26, 'count': 5}
print('Standard Deviation: ', data.std()) # 4.2
print('Variance: ', data.var()) # 17.5
print('Frequency Distribution: ', data.freq_dist()) # [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

```sh
# you output should look like this
print(data.describe())
Count: 25
Sum:  744
Min:  24
Max:  38
Range:  14
Mean:  30
Median:  29
Mode:  (26, 5)
Variance:  17.5
Standard Deviation:  4.2
Frequency Distribution: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

### 练习：2级

1. 创建一个名为PersonAccount的类。它有名字、姓氏、收入、支出属性，还有total_income、total_expense、account_info、add_income，add_expense和account_balance方法。收入是一组收入及其描述。费用也是如此。

### Exercises: Level 3


🎉 CONGRATULATIONS ! 🎉

[<< Day 20](../20_Day_Python_package_manager/20_python_package_manager.md) | [Day 22 >>](../22_Day_Web_scraping/22_web_scraping.md)
