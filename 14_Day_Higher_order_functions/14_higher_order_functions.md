<div align="center">
  <h1> 30 Days Of Python: Day 14 - Higher Order Functions</h1>
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
</div>

[<< Day 13](../13_Day_List_comprehension/13_list_comprehension.md) | [Day 15>>](../15_Day_Python_type_errors/15_python_type_errors.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)
- [📘 Day 14](#-day-14)
  - [Higher Order Functions](#higher-order-functions)
    - [Function as a Parameter](#function-as-a-parameter)
    - [Function as a Return Value](#function-as-a-return-value)
  - [Python Closures](#python-closures)
  - [Python Decorators](#python-decorators)
    - [Creating Decorators](#creating-decorators)
    - [Applying Multiple Decorators to a Single Function](#applying-multiple-decorators-to-a-single-function)
    - [Accepting Parameters in Decorator Functions](#accepting-parameters-in-decorator-functions)
  - [Built-in Higher Order Functions](#built-in-higher-order-functions)
    - [Python - Map Function](#python---map-function)
    - [Python - Filter Function](#python---filter-function)
    - [Python - Reduce Function](#python---reduce-function)
  - [💻 Exercises: Day 14](#-exercises-day-14)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)
    - [Exercises: Level 3](#exercises-level-3)

# 📚 第 14 天

## 高阶函数

在 Python 中，函数被视为一等公民，允许您对函数执行以下操作：

- 函数可以接受一个或多个函数作为参数
- 函数可以作为另一个函数的结果返回
- 函数可以被修改
- 函数可以被赋值给变量

在这一节中，我们将涵盖：

1. 处理函数作为参数
2. 返回函数作为另一个函数的返回值
3. 使用 Python 闭包和装饰器

### 函数作为参数

```py
def sum_numbers(nums):  # normal function
    return sum(nums)    # a sad function abusing the built-in sum function :<

def higher_order_function(f, lst):  # function as a parameter
    summation = f(lst)
    return summation
result = higher_order_function(sum_numbers, [1, 2, 3, 4, 5])
print(result)       # 15
```

### 函数作为返回值

```py
def square(x):          # a square function
    return x ** 2

def cube(x):            # a cube function
    return x ** 3

def absolute(x):        # an absolute value function
    if x >= 0:
        return x
    else:
        return -(x)

def higher_order_function(type): # a higher order function returning a function
    if type == 'square':
        return square
    elif type == 'cube':
        return cube
    elif type == 'absolute':
        return absolute

result = higher_order_function('square')
print(result(3))       # 9
result = higher_order_function('cube')
print(result(3))       # 27
result = higher_order_function('absolute')
print(result(-3))      # 3
```

从上面的例子中可以看出，高阶函数根据传递的参数返回不同的函数

## Python 闭包

Python 允许嵌套函数访问封闭函数的外部范围。这被称为 Closure。让我们看看 Python 中的闭包是如何工作的。在 Python 中，闭包是通过将一个函数嵌套在另一个封装函数中，然后返回内部函数来创建的。请参阅下面的示例。

**Example:**

```py
def add_ten():
    ten = 10
    def add(num):
        return num + ten
    return add

closure_result = add_ten()
print(closure_result(5))  # 15
print(closure_result(10))  # 20
```

## Python 装饰器

装饰器是 Python 中的一种设计模式，它允许用户在不修改其结构的情况下向现有对象添加新功能。装饰器通常在要装饰的函数定义之前调用。

### 创建装饰器

要创建一个装饰器函数，我们需要一个带有内部包装函数的 outer 函数。

**例：**

```py
# Normal function
def greeting():
    return 'Welcome to Python'
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper
g = uppercase_decorator(greeting)
print(g())          # WELCOME TO PYTHON

## Let us implement the example above with a decorator

'''This decorator function is a higher order function
that takes a function as a parameter'''
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper
@uppercase_decorator
def greeting():
    return 'Welcome to Python'
print(greeting())   # WELCOME TO PYTHON

```

### 将多个装饰器应用于单个函数

```py

'''These decorator functions are higher order functions
that take functions as parameters'''

# First Decorator
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper

# Second decorator
def split_string_decorator(function):
    def wrapper():
        func = function()
        splitted_string = func.split()
        return splitted_string

    return wrapper

@split_string_decorator
@uppercase_decorator     # order with decorators is important in this case - .upper() function does not work with lists
def greeting():
    return 'Welcome to Python'
print(greeting())   # WELCOME TO PYTHON
```

### 在 Decorator 函数中接受参数

大多数时候，我们需要我们的函数接受参数，因此我们可能需要定义一个接受参数的装饰器。

```py
def decorator_with_parameters(function):
    def wrapper_accepting_parameters(para1, para2, para3):
        function(para1, para2, para3)
        print("I live in {}".format(para3))
    return wrapper_accepting_parameters

@decorator_with_parameters
def print_full_name(first_name, last_name, country):
    print("I am {} {}. I love to teach.".format(
        first_name, last_name, country))

print_full_name("Asabeneh", "Yetayeh",'Finland')
```

## 内置高阶函数

我们在这部分介绍的一些内置高阶函数是 _map（）_、_filter_ 和 _reduce_。
Lambda 函数可以作为参数传递，Lambda 函数的最佳用例是在 map、filter 和 reduce 等函数中。

### Python - 映射函数

map（） 函数是一个内置函数，它接受一个函数和可迭代对象作为参数。

```py
    # syntax
    map(function, iterable)
```

**Example:1**

```py
numbers = [1, 2, 3, 4, 5] # iterable
def square(x):
    return x ** 2
numbers_squared = map(square, numbers)
print(list(numbers_squared))    # [1, 4, 9, 16, 25]
# Lets apply it with a lambda function
numbers_squared = map(lambda x : x ** 2, numbers)
print(list(numbers_squared))    # [1, 4, 9, 16, 25]
```

**Example:2**

```py
numbers_str = ['1', '2', '3', '4', '5']  # iterable
numbers_int = map(int, numbers_str)
print(list(numbers_int))    # [1, 2, 3, 4, 5]
```

**Example:3**

```py
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']  # iterable

def change_to_upper(name):
    return name.upper()

names_upper_cased = map(change_to_upper, names)
print(list(names_upper_cased))    # ['ASABENEH', 'LIDIYA', 'ERMIAS', 'ABRAHAM']

# Let us apply it with a lambda function
names_upper_cased = map(lambda name: name.upper(), names)
print(list(names_upper_cased))    # ['ASABENEH', 'LIDIYA', 'ERMIAS', 'ABRAHAM']
```

map 实际上所做的是迭代一个列表。例如，它将名称更改为大写并返回一个新列表。

### Python - 过滤函数

filter（） 函数调用指定的函数，该函数为指定的可迭代对象 （list） 的每个项目返回布尔值。它筛选满足筛选条件的项目。

```py
    # syntax
    filter(function, iterable)
```

**Example:1**

```py
# Lets filter only even nubers
numbers = [1, 2, 3, 4, 5]  # iterable

def is_even(num):
    if num % 2 == 0:
        return True
    return False

even_numbers = filter(is_even, numbers)
print(list(even_numbers))       # [2, 4]
```

**Example:2**

```py
numbers = [1, 2, 3, 4, 5]  # iterable

def is_odd(num):
    if num % 2 != 0:
        return True
    return False

odd_numbers = filter(is_odd, numbers)
print(list(odd_numbers))       # [1, 3, 5]
```

```py
# Filter long name
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']  # iterable
def is_name_long(name):
    if len(name) > 7:
        return True
    return False

long_names = filter(is_name_long, names)
print(list(long_names))         # ['Asabeneh']
```

### Python - Reduce 函数

_reduce（）_ 函数在 functools 模块中定义，我们应该从该模块导入它。像 map 和 filter 一样，它需要两个参数，一个 function 和一个 iterable。但是，它不会返回另一个可迭代对象，而是返回单个值。
**例子：1**

```py
numbers_str = ['1', '2', '3', '4', '5']  # iterable
def add_two_nums(x, y):
    return int(x) + int(y)

total = reduce(add_two_nums, numbers_str)
print(total)    # 15
```

## 💻 Exercises: Day 14

```py
countries = ['Estonia', 'Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland']
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### 练习： 级别 1

1. 解释 map、filter 和 reduce 之间的区别。
2. 解释高阶函数、闭包和装饰器之间的区别
3. 在 map、filter 或 reduce 之前定义一个 call 函数，参见示例。
4. 使用 for 循环打印国家/地区列表中的每个国家/地区。
5. 用于打印名称列表中的每个名称。
6. 用于打印数字列表中的每个数字。

### 练习： 级别 2

1. 使用 map 创建一个新列表，方法是将 countries 列表中的每个国家/地区更改为大写
1. 使用地图创建一个新列表，方法是将每个数字更改为数字列表中的正方形
1. 使用 map 将名称列表中的每个名称更改为大写
1. 使用过滤器过滤掉包含 'land' 的国家/地区。
1. 使用 filter 过滤掉正好有 6 个字符的国家/地区。
1. 使用过滤器过滤掉国家/地区列表中包含 6 个或更多字母的国家/地区。
1. 使用过滤器过滤掉以“E”开头的国家/地区
1. Chain two or more list iterators (eg. arr.map(callback).filter(callback).reduce(callback))
1. Declare a function called get_string_lists which takes a list as a parameter and then returns a list containing only string items.
1. Use reduce to sum all the numbers in the numbers list.
1. Use reduce to concatenate all the countries and to produce this sentence: Estonia, Finland, Sweden, Denmark, Norway, and Iceland are north European countries
1. Declare a function called categorize_countries that returns a list of countries with some common pattern (you can find the [countries list](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries.py) in this repository as countries.js(eg 'land', 'ia', 'island', 'stan')).
1. Create a function returning a dictionary, where keys stand for starting letters of countries and values are the number of country names starting with that letter.
2. Declare a get_first_ten_countries function - it returns a list of first ten countries from the countries.js list in the data folder.
1. Declare a get_last_ten_countries function that returns the last ten countries in the countries list.

### 练习： 级别 3

1. 使用 countries_data.py （https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries-data.py） 文件并执行以下任务：
   - 按名称、首都、人口对国家/地区进行排序
   - 按位置整理出使用最多的十种语言。
   - 整理出人口最多的 10 个国家。

🎉 CONGRATULATIONS ! 🎉

[<< Day 13](../13_Day_List_comprehension/13_list_comprehension.md) | [Day 15>>](../15_Day_Python_type_errors/15_python_type_errors.md)