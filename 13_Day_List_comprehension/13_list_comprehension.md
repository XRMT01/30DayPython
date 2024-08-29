<div align="center">
  <h1> 30 Days Of Python: Day 13 - List Comprehension</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

<sub>Author:
<a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
<small> Second Edition: July, 2021</small>
</sub>

</div>
</div>

[<< Day 12](../12_Day_Modules/12_modules.md) | [Day 14>>](../14_Day_Higher_order_functions/14_higher_order_functions.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 13](#-day-13)
  - [List Comprehension](#list-comprehension)
  - [Lambda Function](#lambda-function)
    - [Creating a Lambda Function](#creating-a-lambda-function)
    - [Lambda Function Inside Another Function](#lambda-function-inside-another-function)
  - [💻 Exercises: Day 13](#-exercises-day-13)

# 📘 Day 13

## 列表推导式

Python 中的列表推导式是从序列创建列表的一种紧凑方式。这是创建新列表的捷径。列表推导比使用 for 循环处理列表要快得多。

```py
# syntax
[i for i in iterable if expression]
```

**示例：1**

例如，如果要将字符串更改为字符列表。您可以使用几种方法。让我们看看其中的一些：

```py
# One way
language = 'Python'
lst = list(language) # changing the string to list
print(type(lst))     # list
print(lst)           # ['P', 'y', 't', 'h', 'o', 'n']

# Second way: list comprehension
lst = [i for i in language]
print(type(lst)) # list
print(lst)       # ['P', 'y', 't', 'h', 'o', 'n']

```

**示例：2**

例如，如果您想生成一个数字列表

```py
# Generating numbers
numbers = [i for i in range(11)]  # to generate numbers from 0 to 10
print(numbers)                    # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# It is possible to do mathematical operations during iteration
squares = [i * i for i in range(11)]
print(squares)                    # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# It is also possible to make a list of tuples
numbers = [(i, i * i) for i in range(11)]
print(numbers)                             # [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]

```

**示例：3**

列表推导式可以与 if 表达式结合使用


```py
# Generating even numbers
even_numbers = [i for i in range(21) if i % 2 == 0]  # to generate even numbers list in range 0 to 21
print(even_numbers)                    # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

# Generating odd numbers
odd_numbers = [i for i in range(21) if i % 2 != 0]  # to generate odd numbers in range 0 to 21
print(odd_numbers)                      # [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
# Filter numbers: let's filter out positive even numbers from the list below
numbers = [-8, -7, -3, -1, 0, 1, 3, 4, 5, 7, 6, 8, 10]
positive_even_numbers = [i for i in range(21) if i % 2 == 0 and i > 0]
print(positive_even_numbers)                    # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

# Flattening a three dimensional array
list_of_lists = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened_list = [ number for row in list_of_lists for number in row]
print(flattened_list)    # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Lambda 函数

Lambda 函数是一个没有名称的小型匿名函数。它可以接受任意数量的参数，但只能有一个表达式。Lambda 函数类似于 JavaScript 中的匿名函数。当我们想在另一个函数中编写一个匿名函数时，我们需要它。
### 创建 Lambda 函数

要创建 lambda 函数，我们使用 _lambda_ 关键字，后跟一个参数，后跟一个表达式。请参阅下面的语法和示例。Lambda 函数不使用 return，但它显式返回表达式。
```py
# syntax
x = lambda param1, param2, param3: param1 + param2 + param2
print(x(arg1, arg2, arg3))
```

**Example:**

```py
# Named function
def add_two_nums(a, b):
    return a + b

print(add_two_nums(2, 3))     # 5
# Lets change the above function to a lambda function
add_two_nums = lambda a, b: a + b
print(add_two_nums(2,3))    # 5

# Self invoking lambda function
(lambda a, b: a + b)(2,3) # 5 - need to encapsulate it in print() to see the result in the console

square = lambda x : x ** 2
print(square(3))    # 9
cube = lambda x : x ** 3
print(cube(3))    # 27

# Multiple variables
multiple_variable = lambda a, b, c: a ** 2 - 3 * b + 4 * c
print(multiple_variable(5, 5, 3)) # 22
```

### Lambda 函数在另一个函数中

在另一个函数中使用 lambda 函数。

```py
def power(x):
    return lambda n : x ** n

cube = power(2)(3)   # function power now need 2 arguments to run, in separate rounded brackets
print(cube)          # 8
two_power_of_five = power(2)(5) 
print(two_power_of_five)  # 32
```

🌕 继续努力。保持势头，天空是极限！您刚刚完成了第 13 天的挑战，距离通往伟大的道路还有 13 步。现在为您的大脑和肌肉做一些锻炼。

## 💻 练习：第 13 天

1. 使用列表推导式仅过滤列表中的负值和零
   ```py
   numbers = [-4, -3, -2, -1, 0, 2, 4, 6]
   ```
2.将以下列表列表拼合为一维列表：

   ```py
   list_of_lists =[[[1, 2, 3]], [[4, 5, 6]], [[7, 8, 9]]]

   output
   [1, 2, 3, 4, 5, 6, 7, 8, 9]
   ```

3. 使用列表推导式创建以下 Tuples 列表：
   ```py
   [(0, 1, 0, 0, 0, 0, 0),
   (1, 1, 1, 1, 1, 1, 1),
   (2, 1, 2, 4, 8, 16, 32),
   (3, 1, 3, 9, 27, 81, 243),
   (4, 1, 4, 16, 64, 256, 1024),
   (5, 1, 5, 25, 125, 625, 3125),
   (6, 1, 6, 36, 216, 1296, 7776),
   (7, 1, 7, 49, 343, 2401, 16807),
   (8, 1, 8, 64, 512, 4096, 32768),
   (9, 1, 9, 81, 729, 6561, 59049),
   (10, 1, 10, 100, 1000, 10000, 100000)]
   ```
4. 将以下列表拼合为新列表：
   ```py
   countries = [[('Finland', 'Helsinki')], [('Sweden', 'Stockholm')], [('Norway', 'Oslo')]]
   output:
   [['FINLAND','FIN', 'HELSINKI'], ['SWEDEN', 'SWE', 'STOCKHOLM'], ['NORWAY', 'NOR', 'OSLO']]
   ```
5. 将以下列表更改为词典列表：
   ```py
   countries = [[('Finland', 'Helsinki')], [('Sweden', 'Stockholm')], [('Norway', 'Oslo')]]
   output:
   [{'country': 'FINLAND', 'city': 'HELSINKI'},
   {'country': 'SWEDEN', 'city': 'STOCKHOLM'},
   {'country': 'NORWAY', 'city': 'OSLO'}]
   ```
6. 将以下列表列表更改为串联字符串列表：
   ```py
   names = [[('Asabeneh', 'Yetayeh')], [('David', 'Smith')], [('Donald', 'Trump')], [('Bill', 'Gates')]]
   output
   ['Asabeneh Yetaeyeh', 'David Smith', 'Donald Trump', 'Bill Gates']
   ```
7.编写一个 lambda 函数，该函数可以求解线性函数的斜率或 y 截距。

🎉 CONGRATULATIONS ! 🎉

[<< Day 12](../12_Day_Modules/12_modules.md) | [Day 14>>](../14_Day_Higher_order_functions/14_higher_order_functions.md)
