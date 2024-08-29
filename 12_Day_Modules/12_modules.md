<div align="center">
  <h1> 30 Days Of Python: Day 12 - Modules </h1>
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

[<< Day 11](../11_Day_Functions/11_functions.md) | [Day 13>>](../13_Day_List_comprehension/13_list_comprehension.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 12](#-day-12)
  - [Modules](#modules)
    - [What is a Module](#what-is-a-module)
    - [Creating a Module](#creating-a-module)
    - [Importing a Module](#importing-a-module)
    - [Import Functions from a Module](#import-functions-from-a-module)
    - [Import Functions from a Module and Renaming](#import-functions-from-a-module-and-renaming)
  - [Import Built-in Modules](#import-built-in-modules)
    - [OS Module](#os-module)
    - [Sys Module](#sys-module)
    - [Statistics Module](#statistics-module)
    - [Math Module](#math-module)
    - [String Module](#string-module)
    - [Random Module](#random-module)
  - [💻 Exercises: Day 12](#-exercises-day-12)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)
    - [Exercises: Level 3](#exercises-level-3)

# 📘 Day 12

## 模块

### 什么是模块

模块是一个包含一系列代码或一组函数的文件，这些代码或函数可以被包含到应用程序中。一个模块可以是一个包含单一变量、一个函数或一大段代码的文件。

### 创建模块

要创建一个模块，我们需要将代码写在一个 Python 脚本中，并将其保存为 .py 文件。在你的项目文件夹中创建一个名为 mymodule.py 的文件。让我们在这个文件中写一些代码。

```py
# mymodule.py file
def generate_full_name(firstname, lastname):
    return firstname + ' ' + lastname
```

Create main.py file in your project directory and import the mymodule.py file.

### Importing a Module

要导入这个文件，我们使用 import 关键字和文件名
```py
# main.py file
import mymodule
print(mymodule.generate_full_name('Asabeneh', 'Yetayeh')) # Asabeneh Yetayeh
```

### Import Functions from a Module

我们可以在一个文件中拥有多个函数，并且我们可以以不同的方式导入所有的函数

```py
# main.py file
from mymodule import generate_full_name, sum_two_nums, person, gravity
print(generate_full_name('Asabneh','Yetayeh'))
print(sum_two_nums(1,9))
mass = 100;
weight = mass * gravity
print(weight)
print(person['firstname'])
```

### 从模块导入函数并重命名

在导入时，我们可以重命名模块的名称。

```py
# main.py file
from mymodule import generate_full_name as fullname, sum_two_nums as total, person as p, gravity as g
print(fullname('Asabneh','Yetayeh'))
print(total(1, 9))
mass = 100;
weight = mass * g
print(weight)
print(p)
print(p['firstname'])
```

## 导入内置模块

就像其他编程语言一样，我们也可以通过使用 import 关键字来导入文件/函数。让我们导入我们最常用的常见模块。一些常见的内置模块包括：math、datetime、os、sys、random、statistics、collections、json 和 re。

### OS 模块

使用 Python 的 os 模块，可以自动执行许多操作系统任务。Python 中的 OS 模块提供了用于创建目录、更改当前工作目录、删除目录（文件夹）、获取其内容、更改和识别当前目录等功能。

```py
# import the module
import os
# Creating a directory
os.mkdir('directory_name')
# Changing the current directory
os.chdir('path')
# Getting current working directory
os.getcwd()
# Removing directory
os.rmdir()
```

### Sys 模块

sys 模块提供了用于操作 Python 运行时环境不同部分的函数和变量。sys.argv 函数返回一个列表，其中包含了传递给 Python 脚本的命令行参数。列表中的第 0 个元素总是脚本的名字，第 1 个元素是从命令行传入的参数。
script.py 文件示例：

```py
import sys
#print(sys.argv[0], argv[1],sys.argv[2])  # this line would print out: filename argument1 argument2
print('Welcome {}. Enjoy  {} challenge!'.format(sys.argv[1], sys.argv[2]))
```

现在为了检查这个脚本是如何工作的，我在命令行中编写了：

```sh
python script.py Asabeneh 30DaysOfPython
```

The result:

```sh
Welcome Asabeneh. Enjoy  30DayOfPython challenge! 
```

一些有用的 sys 命令：

```py
# to exit sys
sys.exit()
# To know the largest integer variable it takes
sys.maxsize
# To know environment path
sys.path
# To know the version of python you are using
sys.version
```

### 统计模块

statistics 模块提供了用于数值数据的数理统计的函数。本模块中定义的常用统计函数：_mean_、_median_、_mode_、_stdev_ 等。

```py
from statistics import * # importing all the statistics modules
ages = [20, 20, 4, 24, 25, 22, 26, 20, 23, 22, 26]
print(mean(ages))       # ~22.9
print(median(ages))     # 23
print(mode(ages))       # 20
print(stdev(ages))      # ~2.3
```

### 数学模块

包含许多数学运算和常量的模块。

```py
import math
print(math.pi)           # 3.141592653589793, pi constant
print(math.sqrt(2))      # 1.4142135623730951, square root
print(math.pow(2, 3))    # 8.0, exponential function
print(math.floor(9.81))  # 9, rounding to the lowest
print(math.ceil(9.81))   # 10, rounding to the highest
print(math.log10(100))   # 2, logarithm with 10 as base
```

现在，我们已经导入了 math 模块，其中包含许多可以帮助我们进行数学计算的函数。要检查模块有哪些函数，我们可以使用 _help（math）_ 或 _dir（math）_。这将显示模块中的可用功能。如果我们想只从模块中导入一个特定的函数，我们按如下方式导入它：

```py
from math import pi
print(pi)
```

也可以一次导入多个函数

```py

from math import pi, sqrt, pow, floor, ceil, log10
print(pi)                 # 3.141592653589793
print(sqrt(2))            # 1.4142135623730951
print(pow(2, 3))          # 8.0
print(floor(9.81))        # 9
print(ceil(9.81))         # 10
print(math.log10(100))    # 2

```

但是如果我们想导入 math 模块中的所有函数，我们可以使用 * 。

```py
from math import *
print(pi)                  # 3.141592653589793, pi constant
print(sqrt(2))             # 1.4142135623730951, square root
print(pow(2, 3))           # 8.0, exponential
print(floor(9.81))         # 9, rounding to the lowest
print(ceil(9.81))          # 10, rounding to the highest
print(math.log10(100))     # 2
```

当我们导入时，我们还可以重命名函数的名称。

```py
from math import pi as  PI
print(PI) # 3.141592653589793
```

### 字符串 模块

字符串模块是一个用于多种用途的有用模块。下面的示例显示了 string 模块的一些用法。

```py
import string
print(string.ascii_letters) # abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
print(string.digits)        # 0123456789
print(string.punctuation)   # !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
```

### Random Module

到目前为止，您已经熟悉了导入模块。让我们再做一次导入以非常熟悉它。让我们导入 _random_ 模块，它给我们一个介于 0 和 0.9999 之间的随机数......_random_ 模块有很多函数，但在本节中，我们将只使用 _random_ 和 _randint_。

```py
from random import random, randint
print(random())   # it doesn't take any arguments; it returns a value between 0 and 0.9999
print(randint(5, 20)) # it returns a random integer number between [5, 20] inclusive
```

🌕 你要走很远。继续前进！您刚刚完成了第 12 天的挑战，距离通往伟大的道路还有 12 步。现在为您的大脑和肌肉做一些锻炼。

## 💻 练习：第 12 天

### 练习： 级别 1

1. 编写一个生成 6 位/字符random_user_id的函数。
   ```py
     print(random_user_id());
     '1ee33d'
   ```
2. 修改上一个任务。声明一个名为 user_id_gen_by_user 的函数。它不需要任何参数，但它使用 input（） 需要两个输入。其中一个输入是字符数，第二个输入是应该生成的 ID 数。
   
```py
print(user_id_gen_by_user()) # user input: 5 5
#output:
#kcsy2
#SMFYb
#bWmeq
#ZXOYh
#2Rgxf
   
print(user_id_gen_by_user()) # 16 5
#1GCSgPLMaBAVQZ26
#YD7eFwNQKNs7qXaT
#ycArC5yrRupyG00S
#UbGxOFI7UXSWAyKN
#dIV0SSUTgAdKwStr
```

3. 编写一个名为 rgb_color_gen 的函数。它将生成 rgb 颜色（3 个值，每个值范围从 0 到 255）。
   
```py
print(rgb_color_gen())
# rgb(125,244,255) - the output should be in this form
```

### 练习： 级别 2

1. 编写一个函数list_of_hexa_colors该函数在数组中返回任意数量的十六进制颜色（写在 # 之后的六个十六进制数字）。十六进制数字系统由 16 个符号 0-9 和字母表的前 6 个字母 a-f 组成。检查任务 6 以获取输出示例）。
2. 编写一个函数 list_of_rgb_colors 在数组中返回任意数量的 RGB 颜色。
3.编写一个函数 generate_colors 可以生成任意数量的 hexa 或 rgb 颜色。

```py
   generate_colors('hexa', 3) # ['#a3e12f','#03ed55','#eb3d2b'] 
   generate_colors('hexa', 1) # ['#b334ef']
   generate_colors('rgb', 3)  # ['rgb(5, 55, 175','rgb(50, 105, 100','rgb(15, 26, 80'] 
   generate_colors('rgb', 1)  # ['rgb(33,79, 176)']
   ```

### 练习： 级别 3

1. shuffle_list调用你的函数，它采用一个列表作为参数，并返回一个随机列表
2. 编写一个函数，返回一个 0-9 范围内的 7 个随机数数组。所有数字都必须是唯一的。

🎉 CONGRATULATIONS ! 🎉

[<< Day 11](../11_Day_Functions/11_functions.md) | [Day 13>>](../13_Day_List_comprehension/13_list_comprehension.md)
