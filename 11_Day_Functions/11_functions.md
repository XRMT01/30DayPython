<div align="center">
  <h1> 30 天 Python：第十一天 - Functions</h1>
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

[<< 第十天](../10_Day_Loops/10_loops.md) | [第十二天 >>](../12_Day_Modules/12_modules.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 第十一天](#-第十一天)
  - [函数](#函数)
    - [定义一个函数](#定义一个函数)
    - [声明和调用一个函数](#声明和调用一个函数)
    - [无参数的函数](#无参数的函数)
    - [返回值的函数 - 第一部分](#f返回值的函数 - 第一部分)
    - [声明带有参数的函数](#声明带有参数的函数)
    - [使用关键字和值传递参数](#使用关键字和值传递参数)
    - [返回值的函数 - 第二部分](#返回值的函数 - 第二部分)
    - [带有默认参数的函数](#f带有默认参数的函数)
    - [可变数量的参数](#可变数量的参数)
    - [函数中的默认参数和可变数量的参数](#函数中的默认参数和可变数量的参数)
    - [将函数作为另一个函数的参数](#将函数作为另一个函数的参数)
  - [💻 练习：第十一天](#练习：第十一天)
    - [练习：一级](#练习：一级)
    - [练习：二级](#练习：二级)
    - [练习：三级](#练习：三级)

# 📘 Day 11

## 函数

到目前为止，我们已经看到了许多内置的 Python 函数。在这一节中，我们将重点介绍自定义函数。什么是函数？在开始创建函数之前，让我们先了解什么是函数以及为什么我们需要它们。

### Defining a Function

函数是一个可重用的代码块或编程语句，旨在执行特定任务。为了定义或声明一个函数，Python提供了_def_关键字。以下是定义函数的语法。只有当函数被调用或调用时，才会执行函数代码块。

### Declaring and Calling a Function

当我们创建一个函数时，我们称之为声明函数。当我们开始使用it时，我们称之为*调用*或*调用*函数。函数可以声明有或没有参数。

```py
# syntax
# Declaring a function
def function_name():
    codes
    codes
# Calling a function
function_name()
```

### Function without Parameters

函数可以在没有参数的情况下声明。

**Example:**

```py
def generate_full_name ():
    first_name = 'Asabeneh'
    last_name = 'Yetayeh'
    space = ' '
    full_name = first_name + space + last_name
    print(full_name)
generate_full_name () # calling a function

def add_two_numbers ():
    num_one = 2
    num_two = 3
    total = num_one + num_two
    print(total)
add_two_numbers()
```

### Function Returning a Value - Part 1

函数也可以返回值，如果函数没有return语句，则函数的值为None。让我们使用return重写上述函数。从现在开始，当我们调用函数并打印它时，我们会从函数中获取一个值。

```py
def generate_full_name ():
    first_name = 'Asabeneh'
    last_name = 'Yetayeh'
    space = ' '
    full_name = first_name + space + last_name
    return full_name
print(generate_full_name())

def add_two_numbers ():
    num_one = 2
    num_two = 3
    total = num_one + num_two
    return total
print(add_two_numbers())
```

### Function with Parameters

在函数中，我们可以传递不同的数据类型（数字、字符串、布尔值、列表、元组、字典或集合）作为参数

- 单参数：如果我们的函数有一个参数，我们应该用一个参数调用我们的函数

```py
  # syntax
  # Declaring a function
  def function_name(parameter):
    codes
    codes
  # Calling function
  print(function_name(argument))
```

**Example:**

```py
def greetings (name):
    message = name + ', welcome to Python for Everyone!'
    return message

print(greetings('Asabeneh'))

def add_ten(num):
    ten = 10
    return num + ten
print(add_ten(90))

def square_number(x):
    return x * x
print(square_number(2))

def area_of_circle (r):
    PI = 3.14
    area = PI * r ** 2
    return area
print(area_of_circle(10))

def sum_of_numbers(n):
    total = 0
    for i in range(n+1):
        total+=i
    print(total)
print(sum_of_numbers(10)) # 55
print(sum_of_numbers(100)) # 5050
```

- 双参数：函数可能有也可能没有一个或多个参数。一个函数也可能有两个或多个参数。如果我们的函数有参数，我们应该用参数调用它。让我们检查一个有两个参数的函数:

```py
  # syntax
  # Declaring a function
  def function_name(para1, para2):
    codes
    codes
  # Calling function
  print(function_name(arg1, arg2))
```

**Example:**

```py
def generate_full_name (first_name, last_name):
    space = ' '
      full_name = first_name + space + last_name
      return full_name
print('Full Name: ', generate_full_name('Asabeneh','Yetayeh'))

def sum_two_numbers (num_one, num_two):
    sum = num_one + num_two
    return sum
print('Sum of two numbers: ', sum_two_numbers(1, 9))

def calculate_age (current_year, birth_year):
    age = current_year - birth_year
    return age;

print('Age: ', calculate_age(2021, 1819))

def weight_of_object (mass, gravity):
    weight = str(mass * gravity)+ ' N' # the value has to be changed to a string first
    return weight
print('Weight of an object in Newtons: ', weight_of_object(100, 9.81))
```

### Passing Arguments with Key and Value

如果我们传递带有键和值的参数，则参数的顺序无关紧要。

```py
# syntax
# Declaring a function
def function_name(para1, para2):
    codes
    codes
# Calling function
print(function_name(para1 = 'John', para2 = 'Doe')) # the order of arguments does not matter here
```

**Example:**

```py
def print_fullname(firstname, lastname):
    space = ' '
    full_name = firstname  + space + lastname
    print(full_name)
print(print_fullname(firstname = 'Asabeneh', lastname = 'Yetayeh'))

def add_two_numbers (num1, num2):
    total = num1 + num2
    print(total)
print(add_two_numbers(num2 = 3, num1 = 2)) # Order does not matter
```

### Function Returning a Value - Part 2

如果我们没有用函数返回值，那么我们的函数默认返回_None_。要使用函数返回值，我们使用关键字_return_后跟我们返回的变量。我们可以从函数中返回任何类型的数据。

- Returning a string:
**Example:**

```py
def print_name(firstname):
    return firstname
print_name('Asabeneh') # Asabeneh

def print_full_name(firstname, lastname):
    space = ' '
    full_name = firstname  + space + lastname
    return full_name
print_full_name(firstname='Asabeneh', lastname='Yetayeh')
```

- Returning a number:

**Example:**

```py
def add_two_numbers (num1, num2):
    total = num1 + num2
    return total
print(add_two_numbers(2, 3))

def calculate_age (current_year, birth_year):
    age = current_year - birth_year
    return age;
print('Age: ', calculate_age(2019, 1819))
```

- Returning a boolean:
  **Example:**

```py
def is_even (n):
    if n % 2 == 0:
        print('even')
        return True    # return stops further execution of the function, similar to break 
    return False
print(is_even(10)) # True
print(is_even(7)) # False
```

- Returning a list:
  **Example:**

```py
def find_even_numbers(n):
    evens = []
    for i in range(n + 1):
        if i % 2 == 0:
            evens.append(i)
    return evens
print(find_even_numbers(10))
```

### Function with Default Parameters

有时，当我们调用函数时，我们会将默认值传递给参数。如果我们在调用函数时不传递参数，则将使用它们的默认值。

```py
# syntax
# Declaring a function
def function_name(param = value):
    codes
    codes
# Calling function
function_name()
function_name(arg)
```

**Example:**

```py
def greetings (name = 'Peter'):
    message = name + ', welcome to Python for Everyone!'
    return message
print(greetings())
print(greetings('Asabeneh'))

def generate_full_name (first_name = 'Asabeneh', last_name = 'Yetayeh'):
    space = ' '
    full_name = first_name + space + last_name
    return full_name

print(generate_full_name())
print(generate_full_name('David','Smith'))

def calculate_age (birth_year,current_year = 2021):
    age = current_year - birth_year
    return age;
print('Age: ', calculate_age(1821))

def weight_of_object (mass, gravity = 9.81):
    weight = str(mass * gravity)+ ' N' # the value has to be changed to string first
    return weight
print('Weight of an object in Newtons: ', weight_of_object(100)) # 9.81 - average gravity on Earth's surface
print('Weight of an object in Newtons: ', weight_of_object(100, 1.62)) # gravity on the surface of the Moon
```

### Arbitrary Number of Arguments

如果我们不知道传递给函数的参数数量，我们可以通过在参数名称前添加\*来创建一个可以接受任意数量参数的函数。

```py
# syntax
# Declaring a function
def function_name(*args):
    codes
    codes
# Calling function
function_name(param1, param2, param3,..)
```

**Example:**

```py
def sum_all_nums(*nums):
    total = 0
    for num in nums:
        total += num     # same as total = total + num 
    return total
print(sum_all_nums(2, 3, 5)) # 10
```

### Default and Arbitrary Number of Parameters in Functions

```py
def generate_groups (team,*args):
    print(team)
    for i in args:
        print(i)
print(generate_groups('Team-1','Asabeneh','Brook','David','Eyob'))
```

### Function as a Parameter of Another Function

```py
#You can pass functions around as parameters
def square_number (n):
    return n * n
def do_something(f, x):
    return f(x)
print(do_something(square_number, 3)) # 27
```

🌕 到目前为止，你取得了相当大的成就。继续前进！你刚刚完成了第11天的挑战，你正朝着伟大的方向前进11步。现在做一些锻炼你的大脑和肌肉。

## Testimony
Now it is time to express your thoughts about the Author and 30DaysOfPython. You can leave your testimonial on this [link](https://testimonify.herokuapp.com/)

## 💻 Exercises: Day 11

### Exercises: Level 1

1.声明一个函数_add_two_numbers_。它接受两个参数，并返回一个和。
2.圆的面积计算如下：面积=πx r x r。写一个函数来计算_Area_of_circle_。
3.编写一个名为add_all_nums的函数，该函数接受任意数量的参数并对所有参数求和。检查所有列表项是否都是数字类型。如果没有，请给出合理的反馈。
4.温度（°C）可使用以下公式转换为°F：°F=（°C x 9/5）+32。编写一个函数，将°C转换为°F，_convert_cellsius_to-fahrenheit_。
5.编写一个名为check season的函数，它接受一个月份参数并返回季节：秋季、冬季、春季或夏季。
6.编写一个名为calculate_slope的函数，返回线性方程的斜率
7.二次方程计算如下：ax²+bx+c=0。编写一个函数来计算二次方程的解集_solve_quadratic_eqn_。
8.声明一个名为print_list的函数。它接受一个列表作为参数，并打印出列表中的每个元素。
9.声明一个名为reverse_list的函数。它接受一个数组作为参数，并返回数组的逆（使用循环）。

```py
print(reverse_list([1, 2, 3, 4, 5]))
# [5, 4, 3, 2, 1]
print(reverse_list1(["A", "B", "C"]))
# ["C", "B", "A"]
```

10.声明一个名为capitale_list_items的函数。它接受一个列表作为参数，并返回一个大写的项目列表
11.声明一个名为add_item的函数。它需要一个列表和一个项目参数。它返回一个列表，并在末尾添加项目。

```py
food_staff = ['Potato', 'Tomato', 'Mango', 'Milk'];
print(add_item(food_staff, 'Meat'))     # ['Potato', 'Tomato', 'Mango', 'Milk','Meat'];
numbers = [2, 3, 7, 9];
print(add_item(numbers, 5))      [2, 3, 7, 9, 5]
```

12.声明一个名为remove_item的函数。它需要一个列表和一个项目参数。它返回一个列表，其中删除了项目。

```py
food_staff = ['Potato', 'Tomato', 'Mango', 'Milk'];
print(remove_item(food_staff, 'Mango'))  # ['Potato', 'Tomato', 'Milk'];
numbers = [2, 3, 7, 9];
print(remove_item(numbers, 3))  # [2, 7, 9]
```

13.声明一个名为sum_of_numbers的函数。它接受一个数字参数，并将该范围内的所有数字相加

```py
print(sum_of_numbers(5))  # 15
print(sum_all_numbers(10)) # 55
print(sum_all_numbers(100)) # 5050
```

14.声明一个名为sum_of_odds的函数。它接受一个数字参数，并将该范围内的所有奇数相加。
15.声明一个名为sum_of_even的函数。它需要一个数字参数
它将该范围内的所有偶数相加。

### Exercises: Level 2

1.声明一个名为evens_and_odds的函数。它接受一个正整数作为参数，并计算数字中的偶数和赔率。

```py
    print(evens_and_odds(100))
    # The number of odds are 50.
    # The number of evens are 51.
```

1.调用你的函数factorial，它接受一个整数作为参数，并返回该数字的阶乘
2.调用你的函数_is_empty_，它接受一个参数，并检查它是否为空
3.编写接受列表的不同函数。他们应该计算_man、calculate_mdian、calculite_mode、calculated range、calculate variance和calculate_std（标准偏差）。

### Exercises: Level 3

1.编写一个名为is_prime的函数，它检查一个数字是否为素数。
2.编写一个函数，检查列表中的所有项目是否都是唯一的。
3.编写一个函数，检查列表中的所有项目是否具有相同的数据类型。
4.编写一个函数，检查提供的变量是否是有效的python变量
5.转到数据文件夹并访问countries-data.py文件。
-创建一个名为most_spoken_languages的函数。它应该按降序返回世界上10或20种最常用的语言
-创建一个名为most_populated_countries的函数。它应该按降序返回10或20个人口最多的国家。

🎉 CONGRATULATIONS ! 🎉

[<< 第十天](../10_Day_Loops/10_loops.md) | [第十二天 >>](../12_Day_Modules/12_modules.md)
