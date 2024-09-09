<div align="center">
  <h1> 30 Days Of Python: Day 17 - Exception Handling </h1>
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

[<< 第十六天](../16_Day_Python_date_time/16_python_datetime.md) | [第十八天 >>](../18_Day_Regular_expressions/18_regular_expressions.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 17](#-day-17)
  - [Exception Handling](#exception-handling)
  - [Packing and Unpacking Arguments in Python](#packing-and-unpacking-arguments-in-python)
    - [Unpacking](#unpacking)
      - [Unpacking Lists](#unpacking-lists)
      - [Unpacking Dictionaries](#unpacking-dictionaries)
    - [Packing](#packing)
    - [Packing Lists](#packing-lists)
      - [Packing Dictionaries](#packing-dictionaries)
  - [Spreading in Python](#spreading-in-python)
  - [Enumerate](#enumerate)
  - [Zip](#zip)
  - [Exercises: Day 17](#exercises-day-17)

# 📘 Day 17

## 异常处理

Python使用_try_和_except_来优雅地处理错误。优雅地退出（或优雅地处理）错误是一种简单的编程习惯用法——程序检测到严重的错误情况并以受控的方式“优雅地退出”。作为优雅退出的一部分，程序通常会向终端或日志打印描述性错误消息，这使我们的应用程序更加健壮。异常的原因通常与程序本身无关。异常的一个例子可能是输入错误、文件名错误、找不到文件、IO设备故障。巧妙地处理错误可以防止我们的应用程序崩溃。

我们在上一节中介绍了不同的Python_error_类型。如果我们在程序中使用_try_和_except_，那么它不会在这些块中引发错误。

![Try and Except](../images/try_except.png)

```py
try:
    code in this block if things go well
except:
    code in this block run if things go wrong
```

**Example:**

```py
try:
    print(10 + '5')
except:
    print('Something went wrong')
```

在上面的例子中，第二个操作数是一个字符串。我们可以将其更改为浮点数或整数，将其与数字相加以使其工作。但如果不做任何更改，将执行第二个块_except_。

**Example:**

```py
try:
    name = input('Enter your name:')
    year_born = input('Year you were born:')
    age = 2019 - year_born
    print(f'You are {name}. And your age is {age}.')
except:
    print('Something went wrong')
```

```sh
Something went wrong
```

在上面的例子中，异常块将运行，我们并不确切知道问题所在。为了分析这个问题，我们可以使用不同的错误类型和except。

在下面的示例中，它将处理错误，并告诉我们产生的错误类型。

```py
try:
    name = input('Enter your name:')
    year_born = input('Year you were born:')
    age = 2019 - year_born
    print(f'You are {name}. And your age is {age}.')
except TypeError:
    print('Type error occured')
except ValueError:
    print('Value error occured')
except ZeroDivisionError:
    print('zero division error occured')
```

```sh
Enter your name:Asabeneh
Year you born:1920
Type error occured
```

在上面的代码中，输出将是_TypeError_
现在，让我们添加一个额外的块：

```py
try:
    name = input('Enter your name:')
    year_born = input('Year you born:')
    age = 2019 - int(year_born)
    print('You are {name}. And your age is {age}.')
except TypeError:
    print('Type error occur')
except ValueError:
    print('Value error occur')
except ZeroDivisionError:
    print('zero division error occur')
else:
    print('I usually run with the try block')
finally:
    print('I alway run.')
```

```sh
Enter your name:Asabeneh
Year you born:1920
You are Asabeneh. And your age is 99.
I usually run with the try block
I alway run.
```

它还将上述代码缩短如下：

```py
try:
    name = input('Enter your name:')
    year_born = input('Year you born:')
    age = 2019 - int(year_born)
    print('You are {name}. And your age is {age}.')
except Exception as e:
    print(e)

```

## Python中的参数打包与解包

我们使用两个运算符：

- \* for tuples
- \*\* for dictionaries

让我们举一个下面的例子。这只需要争论，但我们有清单。我们可以打开列表并更改参数。

### 拆包

#### 拆包清单

```py
def sum_of_five_nums(a, b, c, d, e):
    return a + b + c + d + e

lst = [1, 2, 3, 4, 5]
print(sum_of_five_nums(lst)) # TypeError: sum_of_five_nums() missing 4 required positional arguments: 'b', 'c', 'd', and 'e'
```

当我们运行这段代码时，它会引发一个错误，因为这个函数接受数字（而不是列表）作为参数。让我们拆开/销毁这份清单。

```py
def sum_of_five_nums(a, b, c, d, e):
    return a + b + c + d + e

lst = [1, 2, 3, 4, 5]
print(sum_of_five_nums(*lst))  # 15
```

我们还可以在需要开始和结束的范围内置函数中使用解包。

```py
numbers = range(2, 7)  # normal call with separate arguments
print(list(numbers)) # [2, 3, 4, 5, 6]
args = [2, 7]
numbers = range(*args)  # call with arguments unpacked from a list
print(numbers)      # [2, 3, 4, 5,6]

```

列表或元组也可以像这样解包：

```py
countries = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
fin, sw, nor, *rest = countries
print(fin, sw, nor, rest)   # Finland Sweden Norway ['Denmark', 'Iceland']
numbers = [1, 2, 3, 4, 5, 6, 7]
one, *middle, last = numbers
print(one, middle, last)      #  1 [2, 3, 4, 5, 6] 7
```

#### 打开字典

```py
def unpacking_person_info(name, country, city, age):
    return f'{name} lives in {country}, {city}. He is {age} year old.'
dct = {'name':'Asabeneh', 'country':'Finland', 'city':'Helsinki', 'age':250}
print(unpacking_person_info(**dct)) # Asabeneh lives in Finland, Helsinki. He is 250 years old.
```

### 包装

有时我们永远不知道需要向python函数传递多少个参数。我们可以使用打包方法来允许我们的函数接受无限数量或任意数量的参数。

### 装箱单

```py
def sum_all(*args):
    s = 0
    for i in args:
        s += i
    return s
print(sum_all(1, 2, 3))             # 6
print(sum_all(1, 2, 3, 4, 5, 6, 7)) # 28
```

#### 包装词典

```py
def packing_person_info(**kwargs):
    # check the type of kwargs and it is a dict type
    # print(type(kwargs))
    # Printing dictionary items
    for key in kwargs:
        print(f"{key} = {kwargs[key]}")
    return kwargs

print(packing_person_info(name="Asabeneh",
      country="Finland", city="Helsinki", age=250))
```

```sh
name = Asabeneh
country = Finland
city = Helsinki
age = 250
{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'age': 250}
```

## 在Python中传播

与JavaScript一样，在Python中传播是可能的。让我们在下面的例子中检查一下：

```py
lst_one = [1, 2, 3]
lst_two = [4, 5, 6, 7]
lst = [0, *lst_one, *lst_two]
print(lst)          # [0, 1, 2, 3, 4, 5, 6, 7]
country_lst_one = ['Finland', 'Sweden', 'Norway']
country_lst_two = ['Denmark', 'Iceland']
nordic_countries = [*country_lst_one, *country_lst_two]
print(nordic_countries)  # ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
```

## 枚举

如果我们对列表的索引感兴趣，我们可以使用_enumerate_内置函数来获取列表中每个项目的索引。

```py
for index, item in enumerate([20, 30, 40]):
    print(index, item)
```

```py
for index, i in enumerate(countries):
    print('hi')
    if i == 'Finland':
        print('The country {i} has been found at index {index}')
```

```sh
The country Finland has been found at index 1.
```

## Zip

有时我们想在遍历列表时组合列表。请参阅下面的示例：

```py
fruits = ['banana', 'orange', 'mango', 'lemon', 'lime']                    
vegetables = ['Tomato', 'Potato', 'Cabbage','Onion', 'Carrot']
fruits_and_veges = []
for f, v in zip(fruits, vegetables):
    fruits_and_veges.append({'fruit':f, 'veg':v})

print(fruits_and_veges)
```

```sh
[{'fruit': 'banana', 'veg': 'Tomato'}, {'fruit': 'orange', 'veg': 'Potato'}, {'fruit': 'mango', 'veg': 'Cabbage'}, {'fruit': 'lemon', 'veg': 'Onion'}, {'fruit': 'lime', 'veg': 'Carrot'}]
```

🌕 你下定决心了。你只有17步才能走向伟大。现在做一些锻炼你的大脑和肌肉。

## Exercises: Day 17

1. names=[内陆、瑞典、挪威、丹麦、冰岛、爱沙尼亚、俄罗斯]。打开前五个国家的包装，将其存储在变量nordic_countries中，将爱沙尼亚和俄罗斯分别存储在es和ru中。

🎉 CONGRATULATIONS ! 🎉

[<< Day 16](../16_Day_Python_date_time/16_python_datetime.md) | [Day 18 >>](../18_Day_Regular_expressions/18_regular_expressions.md)
