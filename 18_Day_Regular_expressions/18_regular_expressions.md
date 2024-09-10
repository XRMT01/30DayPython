<div align="center">
  <h1> 30 Days Of Python: Day 18 - Regular Expressions </h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

  <sub>Author:
  <a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
  <small> First Edition: Nov 22 - Dec 22, 2019</small>
  </sub>
</div>
</div>

[<< 第十七天](../17_Day_Exception_handling/17_exception_handling.md) | [第十九天>>](../19_Day_File_handling/19_file_handling.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 18](#-day-18)
  - [Regular Expressions](#regular-expressions)
    - [The *re* Module](#the-re-module)
    - [Methods in *re* Module](#methods-in-re-module)
      - [Match](#match)
      - [Search](#search)
      - [Searching for All Matches Using *findall*](#searching-for-all-matches-using-findall)
      - [Replacing a Substring](#replacing-a-substring)
  - [Splitting Text Using RegEx Split](#splitting-text-using-regex-split)
  - [Writing RegEx Patterns](#writing-regex-patterns)
    - [Square Bracket](#square-bracket)
    - [Escape character(\\) in RegEx](#escape-character-in-regex)
    - [One or more times(+)](#one-or-more-times)
    - [Period(.)](#period)
    - [Zero or more times(\*)](#zero-or-more-times)
    - [Zero or one time(?)](#zero-or-one-time)
    - [Quantifier in RegEx](#quantifier-in-regex)
    - [Cart ^](#cart-)
  - [💻 Exercises: Day 18](#-exercises-day-18)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)
    - [Exercises: Level 3](#exercises-level-3)

# 📘 第十八天

## 正则表达式

正则表达式或RegEx是一种特殊的文本字符串，有助于在数据中查找模式。RegEx可用于检查不同数据类型中是否存在某种模式。要在python中使用RegEx，首先我们应该导入名为*re*的RegEx模块。
### *re*模块

导入模块后，我们可以使用它来检测或查找模式。

```py
import re
```

### *re*模块中的方法

为了找到一个模式，我们使用不同的*re*字符集，允许在字符串中搜索匹配项。

-*re.match（）*：仅在字符串第一行的开头搜索，如果找到匹配的对象，则返回匹配的对象；否则返回None。
-*re.search*：如果字符串中任何位置都有匹配对象，包括多行字符串，则返回匹配对象。
-*re.findall*：返回一个包含所有匹配项的列表
-*re.split*：获取一个字符串，在匹配点处拆分它，返回一个列表
-*re.sub*：替换字符串中的一个或多个匹配项

#### 匹配

```py
# syntac
re.match(substring, string, re.I)
# substring is a string or a pattern, string is the text we look for a pattern , re.I is case ignore
```

```py
import re

txt = 'I love to teach python and javaScript'
# It returns an object with span, and match
match = re.match('I love to teach', txt, re.I)
print(match)  # <re.Match object; span=(0, 15), match='I love to teach'>
# We can get the starting and ending position of the match as tuple using span
span = match.span()
print(span)     # (0, 15)
# Lets find the start and stop position from the span
start, end = span
print(start, end)  # 0, 15
substring = txt[start:end]
print(substring)       # I love to teach
```

正如你从上面的例子中看到的，我们正在寻找的模式（或子字符串）是*我喜欢教*。如果文本以模式开头，match函数只返回一个对象**。

```py
import re

txt = 'I love to teach python and javaScript'
match = re.match('I like to teach', txt, re.I)
print(match)  # None
```

字符串中没有带*我喜欢教*的字符串，因此没有匹配，match方法返回None。

#### Search

```py
# syntax
re.match(substring, string, re.I)
# substring is a pattern, string is the text we look for a pattern , re.I is case ignore flag
```

```py
import re

txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

# It returns an object with span and match
match = re.search('first', txt, re.I)
print(match)  # <re.Match object; span=(100, 105), match='first'>
# We can get the starting and ending position of the match as tuple using span
span = match.span()
print(span)     # (100, 105)
# Lets find the start and stop position from the span
start, end = span
print(start, end)  # 100 105
substring = txt[start:end]
print(substring)       # first
```

正如你所看到的，搜索比匹配好得多，因为它可以在整个文本中寻找模式。搜索返回一个匹配对象，其中包含找到的第一个匹配项，否则返回*None*。一个更好的*re*函数是*findall*。此函数检查整个字符串中的模式，并以列表形式返回所有匹配项。

#### 使用*findall搜索所有匹配项*

*findall（）*以列表形式返回所有匹配项

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

# It return a list
matches = re.findall('language', txt, re.I)
print(matches)  # ['language', 'language']
```

如您所见，单词*language*在字符串中出现了两次。让我们再练习一些。
现在我们将在字符串中查找Python和Python单词：

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

# It returns list
matches = re.findall('python', txt, re.I)
print(matches)  # ['Python', 'python']

```

由于我们使用了*re.I*，因此包含了小写和大写字母。如果我们没有re.I标志，那么我们将不得不以不同的方式编写我们的模式。让我们来看看：

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

matches = re.findall('Python|python', txt)
print(matches)  # ['Python', 'python']

#
matches = re.findall('[Pp]ython', txt)
print(matches)  # ['Python', 'python']

```

#### 更换子字符串

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

match_replaced = re.sub('Python|python', 'JavaScript', txt, re.I)
print(match_replaced)  # JavaScript is the most beautiful language that a human being has ever created.
# OR
match_replaced = re.sub('[Pp]ython', 'JavaScript', txt, re.I)
print(match_replaced)  # JavaScript is the most beautiful language that a human being has ever created.
```

Let us add one more example. The following string is really hard to read unless we remove the % symbol. Replacing the % with an empty string will clean the text.

```py

txt = '''%I a%m te%%a%%che%r% a%n%d %% I l%o%ve te%ach%ing. 
T%he%re i%s n%o%th%ing as r%ewarding a%s e%duc%at%i%ng a%n%d e%m%p%ow%er%ing p%e%o%ple.
I fo%und te%a%ching m%ore i%n%t%er%%es%ting t%h%an any other %jobs. 
D%o%es thi%s m%ot%iv%a%te %y%o%u to b%e a t%e%a%cher?'''

matches = re.sub('%', '', txt)
print(matches)
```

```sh
I am teacher and I love teaching.
There is nothing as rewarding as educating and empowering people. 
I found teaching more interesting than any other jobs. Does this motivate you to be a teacher?
```

## 使用RegEx Split分割文本

```py
txt = '''I am teacher and  I love teaching.
There is nothing as rewarding as educating and empowering people.
I found teaching more interesting than any other jobs.
Does this motivate you to be a teacher?'''
print(re.split('\n', txt)) # splitting using \n - end of line symbol
```

```sh
['I am teacher and  I love teaching.', 'There is nothing as rewarding as educating and empowering people.', 'I found teaching more interesting than any other jobs.', 'Does this motivate you to be a teacher?']
```

## 编写RegEx模式

要声明字符串变量，我们使用单引号或双引号。声明RegEx变量*r''*。
以下模式仅用小写字母标识苹果，为了使其不区分大小写，我们应该重写我们的模式，或者添加一个标志。

```py
import re

regex_pattern = r'apple'
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. '
matches = re.findall(regex_pattern, txt)
print(matches)  # ['apple']

# To make case insensitive adding flag '
matches = re.findall(regex_pattern, txt, re.I)
print(matches)  # ['Apple', 'apple']
# or we can use a set of characters method
regex_pattern = r'[Aa]pple'  # this mean the first letter could be Apple or apple
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'apple']

```

* []:  A set of characters
  - [a-c] means, a or b or c
  - [a-z] means, any letter from a to z
  - [A-Z] means, any character from A to Z
  - [0-3] means, 0 or 1 or 2 or 3
  - [0-9] means any number from 0 to 9
  - [A-Za-z0-9] any single character, that is a to z, A to Z or 0 to 9
- \\:  uses to escape special characters
  - \d means: match where the string contains digits (numbers from 0-9)
  - \D means: match where the string does not contain digits
- . : any character except new line character(\n)
- ^: starts with
  - r'^substring' eg r'^love', a sentence that starts with a word love
  - r'[^abc] means not a, not b, not c.
- $: ends with
  - r'substring$' eg r'love$', sentence  that ends with a word love
- *: zero or more times
  - r'[a]*' means a optional or it can occur many times.
- +: one or more times
  - r'[a]+' means at least once (or more)
- ?: zero or one time
  - r'[a]?' means zero times or once
- {3}: Exactly 3 characters
- {3,}: At least 3 characters
- {3,8}: 3 to 8 characters
- |: Either or
  - r'apple|banana' means either apple or a banana
- (): Capture and group

![Regular Expression cheat sheet](../images/regex.png)

让我们用例子来澄清上面的元字符

### 方括号

让我们用方括号来括上下壳体

```py
regex_pattern = r'[Aa]pple' # this square bracket mean either A or a
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away.'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'apple']
```

如果我们想寻找香蕉，我们可以写下以下模式：

```py
regex_pattern = r'[Aa]pple|[Bb]anana' # this square bracket means either A or a
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away.'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'banana', 'apple', 'banana']
```

使用方括号和/或运算符，我们设法提取苹果、苹果、香蕉和香蕉。

### RegEx中的转义符（\\）

```py
regex_pattern = r'\d'  # d is a special character which means digits
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2', '0', '1', '9', '8', '2', '0', '2', '1'], this is not what we want
```

### 一次或多次（+）

```py
regex_pattern = r'\d+'  # d is a special character which means digits, + mean one or more times
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2019', '8', '2021'] - now, this is better!
```

### 周期（.）

```py
regex_pattern = r'[a].'  # this square bracket means a and . means any character except new line
txt = '''Apple and banana are fruits'''
matches = re.findall(regex_pattern, txt)
print(matches)  # ['an', 'an', 'an', 'a ', 'ar']

regex_pattern = r'[a].+'  # . any character, + any character one or more times 
matches = re.findall(regex_pattern, txt)
print(matches)  # ['and banana are fruits']
```

### 零次或多次（\*）

零次或多次。该模式可能不会出现，也可能出现多次。

```py
regex_pattern = r'[a].*'  # . any character, * any character zero or more times 
txt = '''Apple and banana are fruits'''
matches = re.findall(regex_pattern, txt)
print(matches)  # ['and banana are fruits']
```

### 零次或一次（？）

零次或一次。该模式可能不会出现，也可能只出现一次。

```py
txt = '''I am not sure if there is a convention how to write the word e-mail.
Some people write it as email others may write it as Email or E-mail.'''
regex_pattern = r'[Ee]-?mail'  # ? means here that '-' is optional
matches = re.findall(regex_pattern, txt)
print(matches)  # ['e-mail', 'email', 'Email', 'E-mail']
```

### RegEx中的量化器

我们可以使用花括号指定在文本中查找的子字符串的长度。让我们想象一下，我们对长度为4个字符的子字符串感兴趣：

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'\d{4}'  # exactly four times
matches = re.findall(regex_pattern, txt)
print(matches)  # ['2019', '2021']

txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'\d{1, 4}'   # 1 to 4
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2019', '8', '2021']
```

### 抓取 ^

- Starts with
  
```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'^This'  # ^ means starts with
matches = re.findall(regex_pattern, txt)
print(matches)  # ['This']
```

- Negation

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'[^A-Za-z ]+'  # ^ in set character means negation, not A to Z, not a to z, no space
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6,', '2019', '8', '2021']
```

## 💻 Exercises: Day 18

### 练习：第一关

 1. 下一段中最常见的单词是什么？

```py
    paragraph = 'I love teaching. If you do not love teaching what else can you love. I love Python if you do not love something which can give you all the capabilities to develop an application what else can you love.
```

```sh
    [
    (6, 'love'),
    (5, 'you'),
    (3, 'can'),
    (2, 'what'),
    (2, 'teaching'),
    (2, 'not'),
    (2, 'else'),
    (2, 'do'),
    (2, 'I'),
    (1, 'which'),
    (1, 'to'),
    (1, 'the'),
    (1, 'something'),
    (1, 'if'),
    (1, 'give'),
    (1, 'develop'),
    (1, 'capabilities'),
    (1, 'application'),
    (1, 'an'),
    (1, 'all'),
    (1, 'Python'),
    (1, 'If')
    ]
```

2. 一些粒子在水平x轴上的位置在负方向上为-12、-4、-3和-1，在原点为0，在正方向上为4和8。从整篇文章中提取这些数字，并找出两个最远粒子之间的距离。

```py
points = ['-12', '-4', '-3', '-1', '0', '4', '8']
sorted_points =  [-12, -4, -3, -1, -1, 0, 2, 4, 8]
distance = 8 -(-12) # 20
```

### 练习：第二关

1. 编写一个模式来标识字符串是否是有效的python变量

    ```sh
    is_valid_variable('first_name') # True
    is_valid_variable('first-name') # False
    is_valid_variable('1first_name') # False
    is_valid_variable('firstname') # True
    ```

### 练习：第三关

1. 清除以下文本。清理后，数一下字符串中最常见的三个单词。

    ```py
    sentence = '''%I $am@% a %tea@cher%, &and& I lo%#ve %tea@ching%;. There $is nothing; &as& mo@re rewarding as educa@ting &and& @emp%o@wering peo@ple. ;I found tea@ching m%o@re interesting tha@n any other %jo@bs. %Do@es thi%s mo@tivate yo@u to be a tea@cher!?'''

    print(clean_text(sentence));
    I am a teacher and I love teaching There is nothing as more rewarding as educating and empowering people I found teaching more interesting than any other jobs Does this motivate you to be a teacher
    print(most_frequent_words(cleaned_text)) # [(3, 'I'), (2, 'teaching'), (2, 'teacher')]
    ```

🎉 CONGRATULATIONS ! 🎉

[<< Day 17](../17_Day_Exception_handling/17_exception_handling.md) | [Day 19>>](../19_Day_File_handling/19_file_handling.md)
