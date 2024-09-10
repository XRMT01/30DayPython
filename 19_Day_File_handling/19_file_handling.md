<div align="center">
  <h1> 30 Days Of Python: Day 19 - File Handling </h1>
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

[<< 第十八天](../18_Day_Regular_expressions/18_regular_expressions.md) | [第二十天 >>](../20_Day_Python_package_manager/20_python_package_manager.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 19](#-day-19)
  - [File Handling](#file-handling)
    - [Opening Files for Reading](#opening-files-for-reading)
    - [Opening Files for Writing and Updating](#opening-files-for-writing-and-updating)
    - [Deleting Files](#deleting-files)
  - [File Types](#file-types)
    - [File with txt Extension](#file-with-txt-extension)
    - [File with json Extension](#file-with-json-extension)
    - [Changing JSON to Dictionary](#changing-json-to-dictionary)
    - [Changing Dictionary to JSON](#changing-dictionary-to-json)
    - [Saving as JSON File](#saving-as-json-file)
    - [File with csv Extension](#file-with-csv-extension)
    - [File with xlsx Extension](#file-with-xlsx-extension)
    - [File with xml Extension](#file-with-xml-extension)
  - [💻 Exercises: Day 19](#-exercises-day-19)
    - [Exercises: Level 1](#exercises-level-1)
    - [Exercises: Level 2](#exercises-level-2)
    - [Exercises: Level 3](#exercises-level-3)

# 📘 第十九天

## 文件处理

到目前为止，我们已经看到了不同的Python数据类型。我们通常以不同的文件格式存储数据。除了处理文件外，我们还将在本节中看到不同的文件格式（.txt、.json、.xml、.csv、.tsv、excel）。首先，让我们熟悉如何处理常见文件格式（.txt）的文件。

文件处理是编程的一个重要部分，它允许我们创建、读取、更新和删除文件。在Python中，我们使用_open（）_内置函数来处理数据。

```py
# Syntax
open('filename', mode) # mode(r, a, w, x, t,b)  could be to read, write, update
```

-“r”-读取-默认值。打开文件进行读取，如果文件不存在，则返回错误
-“a”-附加-打开文件进行附加，如果文件不存在，则创建该文件
-“w”-写入-打开文件进行写入，如果文件不存在，则创建该文件
-“x”-创建-创建指定的文件，如果文件存在，则返回错误
-“t”-文本-默认值。文本模式
-“b”-二进制-二进制模式（例如图像）

### 打开文件进行阅读

_open_的默认模式是读取，因此我们不必指定“r”或“rt”。我在files目录中创建并保存了一个名为reading_file_example.txt的文件。让我们看看它是如何做到的：

```py
f = open('./files/reading_file_example.txt')
print(f) # <_io.TextIOWrapper name='./files/reading_file_example.txt' mode='r' encoding='UTF-8'>
```

正如你在上面的例子中看到的，我打印了打开的文件，它给出了一些关于它的信息。打开的文件有不同的读取方法：_read（）_、_readline_、_read lines_。打开的文件必须使用_close（）_方法关闭。

-_read（）_：将整个文本作为字符串读取。如果我们想限制要读取的字符数，可以通过向*read（number）*方法传递int值来限制它。

```py
f = open('./files/reading_file_example.txt')
txt = f.read()
print(type(txt))
print(txt)
f.close()
```

```sh
# output
<class 'str'>
This is an example to show how to open a file and read.
This is the second line of the text.
```

让我们打印文本文件的前10个字符，而不是打印所有文本。

```py
f = open('./files/reading_file_example.txt')
txt = f.read(10)
print(type(txt))
print(txt)
f.close()
```

```sh
# output
<class 'str'>
This is an
```

-_readline（）_：只读第一行

```py
f = open('./files/reading_file_example.txt')
line = f.readline()
print(type(line))
print(line)
f.close()
```

```sh
# output
<class 'str'>
This is an example to show how to open a file and read.
```

-_readlines（）_：逐行读取所有文本并返回行列表

```py
f = open('./files/reading_file_example.txt')
lines = f.readlines()
print(type(lines))
print(lines)
f.close()
```

```sh
# output
<class 'list'>
['This is an example to show how to open a file and read.\n', 'This is the second line of the text.']
```

另一种将所有行作为列表获取的方法是使用_splitlines（）_： 

```py
f = open('./files/reading_file_example.txt')
lines = f.read().splitlines()
print(type(lines))
print(lines)
f.close()
```

```sh
# output
<class 'list'>
['This is an example to show how to open a file and read.', 'This is the second line of the text.']
```

打开文件后，我们应该关闭它。忘记关闭它们的可能性很高。有一种使用_with_打开文件的新方法，它会自动关闭文件。让我们用_with_方法重写前面的例子：

```py
with open('./files/reading_file_example.txt') as f:
    lines = f.read().splitlines()
    print(type(lines))
    print(lines)
```

```sh
# output
<class 'list'>
['This is an example to show how to open a file and read.', 'This is the second line of the text.']
```

### 打开文件进行写入和更新

要写入现有文件，我们必须在_open（）_函数中添加一个mode作为参数：

-“a”append将追加到文件末尾，如果文件没有追加，则创建一个新文件。
-“w”-write-如果创建的文件不存在，将覆盖任何现有内容。

让我们将一些文本附加到我们一直在读取的文件中：

```py
with open('./files/reading_file_example.txt','a') as f:
    f.write('This text has to be appended at the end')
```

如果文件不存在，下面的方法会创建一个新文件：

```py
with open('./files/writing_file_example.txt','w') as f:
    f.write('This text will be written in a newly created file')
```

### 删除文件

我们在上一节中已经看到了如何使用_os_模块创建和删除目录。现在，如果我们想删除一个文件，我们可以使用_os_模块。

```py
import os
os.remove('./files/example.txt')

```

如果文件不存在，remove方法将引发错误，因此最好使用以下条件：

```py
import os
if os.path.exists('./files/example.txt'):
    os.remove('./files/example.txt')
else:
    print('The file does not exist')
```

## 文件类型

### 扩展名为txt的文件

扩展名为_txt_的文件是一种非常常见的数据形式，我们在上一节中已经介绍过。让我们转到JSON文件

### 扩展名为json的文件

JSON代表JavaScript对象表示法。实际上，它是一个字符串化的JavaScript对象或Python字典。

_Example:_

```py
# dictionary
person_dct= {
    "name":"Asabeneh",
    "country":"Finland",
    "city":"Helsinki",
    "skills":["JavaScrip", "React","Python"]
}
# JSON: A string form a dictionary
person_json = "{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'skills': ['JavaScrip', 'React', 'Python']}"

# we use three quotes and make it multiple line to make it more readable
person_json = '''{
    "name":"Asabeneh",
    "country":"Finland",
    "city":"Helsinki",
    "skills":["JavaScrip", "React","Python"]
}'''
```

### 将JSON转换为字典

要将JSON转换为字典，首先我们导入JSON模块，然后使用_loads_方法。

```py
import json
# JSON
person_json = '''{
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}'''
# let's change JSON to dictionary
person_dct = json.loads(person_json)
print(type(person_dct))
print(person_dct)
print(person_dct['name'])
```

```sh
# output
<class 'dict'>
{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'skills': ['JavaScrip', 'React', 'Python']}
Asabeneh
```

### 将字典更改为JSON

要将字典更改为JSON，我们使用JSON模块中的_dumps_方法。

```py
import json
# python dictionary
person = {
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}
# let's convert it to  json
person_json = json.dumps(person, indent=4) # indent could be 2, 4, 8. It beautifies the json
print(type(person_json))
print(person_json)
```

```sh
# output
# when you print it, it does not have the quote, but actually it is a string
# JSON does not have type, it is a string type.
<class 'str'>
{
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": [
        "JavaScrip",
        "React",
        "Python"
    ]
}
```

### 另存为JSON文件

我们还可以将数据保存为json文件。让我们使用以下步骤将其保存为json文件。对于编写json文件，我们使用json.dump（）方法，它可以接受字典、输出文件、ensure_ascii和indent。

```py
import json
# python dictionary
person = {
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}
with open('./files/json_example.json', 'w', encoding='utf-8') as f:
    json.dump(person, f, ensure_ascii=False, indent=4)
```

在上面的代码中，我们使用了编码和缩进。缩进使json文件易于阅读。

### 扩展名为csv的文件

CSV代表逗号分隔的值。CSV是一种简单的文件格式，用于存储表格数据，如电子表格或数据库。CSV是数据科学中非常常见的数据格式。

**示例：**

```csv
“姓名”、“国家”、“城市”、“技能”
“Asabeneh”、“芬兰”、“赫尔辛基”、“JavaScript”
```

**示例：**

```py
import csv
with open('./files/csv_example.csv') as f:
    csv_reader = csv.reader(f, delimiter=',') # w use, reader method to read csv
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f'Column names are :{", ".join(row)}')
            line_count += 1
        else:
            print(
                f'\t{row[0]} is a teachers. He lives in {row[1]}, {row[2]}.')
            line_count += 1
    print(f'Number of lines:  {line_count}')
```

```sh
# output:
Column names are :name, country, city, skills
        Asabeneh is a teacher. He lives in Finland, Helsinki.
Number of lines:  2
```

### 扩展名为xlsx的文件

要读取excel文件，我们需要安装_xlrd_包。我们将在介绍使用pip安装软件包后再介绍这一点。

```py
import xlrd
excel_book = xlrd.open_workbook('sample.xls)
print(excel_book.nsheets)
print(excel_book.sheet_names)
```

### 扩展名为xml的文件

XML是另一种看起来像HTML的结构化数据格式。在XML中，标签不是预定义的。第一行是XML声明。person标签是XML的根。该人具有性别属性。
**示例：XML**

```xml
<?xml version="1.0"?>
<person gender="female">
  <name>Asabeneh</name>
  <country>Finland</country>
  <city>Helsinki</city>
  <skills>
    <skill>JavaScrip</skill>
    <skill>React</skill>
    <skill>Python</skill>
  </skills>
</person>
```

For more information on how to read an XML file check the [documentation](https://docs.python.org/2/library/xml.etree.elementtree.html)

```py
import xml.etree.ElementTree as ET
tree = ET.parse('./files/xml_example.xml')
root = tree.getroot()
print('Root tag:', root.tag)
print('Attribute:', root.attrib)
for child in root:
    print('field: ', child.tag)
```

```sh
# output
Root tag: person
Attribute: {'gender': 'male'}
field: name
field: country
field: city
field: skills
```

🌕 You are making a big progress. Maintain your momentum, keep the good work. Now do some exercises for your brain and muscles.

## 💻 Exercises: Day 19

### 练习：第一关

1. 编写一个函数，计算文本中的行数和字数。所有文件都在data文件夹中：
a） 读取obama_speech.txt文件并计算行数和单词数
b） 读取michele_obama_speech.txt文件并计算行数和单词数
c） 读取donald_speech.txt文件并计算行数和单词数
d） 读取melina_trump_speech.txt文件并计算行数和单词数
2. 读取data目录中的countries _data.json数据文件，创建一个查找十种最常用语言的函数

   ```py
   # Your output should look like this
   print(most_spoken_languages(filename='./data/countries_data.json', 10))
   [(91, 'English'),
   (45, 'French'),
   (25, 'Arabic'),
   (24, 'Spanish'),
   (9, 'Russian'),
   (9, 'Portuguese'),
   (8, 'Dutch'),
   (7, 'German'),
   (5, 'Chinese'),
   (4, 'Swahili'),
   (4, 'Serbian')]

   # Your output should look like this
   print(most_spoken_languages(filename='./data/countries_data.json', 3))
   [(91, 'English'),
   (45, 'French'),
   (25, 'Arabic')]
   ```

3. 读取data目录中的countries _data.json数据文件，创建一个函数，创建人口最多的十个国家的列表

   ```py
   # Your output should look like this
   print(most_populated_countries(filename='./data/countries_data.json', 10))

   [
   {'country': 'China', 'population': 1377422166},
   {'country': 'India', 'population': 1295210000},
   {'country': 'United States of America', 'population': 323947000},
   {'country': 'Indonesia', 'population': 258705000},
   {'country': 'Brazil', 'population': 206135893},
   {'country': 'Pakistan', 'population': 194125062},
   {'country': 'Nigeria', 'population': 186988000},
   {'country': 'Bangladesh', 'population': 161006790},
   {'country': 'Russian Federation', 'population': 146599183},
   {'country': 'Japan', 'population': 126960000}
   ]

   # Your output should look like this

   print(most_populated_countries(filename='./data/countries_data.json', 3))
   [
   {'country': 'China', 'population': 1377422166},
   {'country': 'India', 'population': 1295210000},
   {'country': 'United States of America', 'population': 323947000}
   ]
   ```

### 练习：第二关

4. 从email_exchange_big.txt文件中提取所有收到的电子邮件地址作为列表。
5. 找出英语中最常见的单词。调用函数find_most_common_words的名称，它将接受两个参数——一个字符串或一个文件和一个正整数，表示单词的数量。您的函数将返回一个按降序排列的元组数组。检查输出

```py
    # Your output should look like this
    print(find_most_common_words('sample.txt', 10))
    [(10, 'the'),
    (8, 'be'),
    (6, 'to'),
    (6, 'of'),
    (5, 'and'),
    (4, 'a'),
    (4, 'in'),
    (3, 'that'),
    (2, 'have'),
    (2, 'I')]

    # Your output should look like this
    print(find_most_common_words('sample.txt', 5))

    [(10, 'the'),
    (8, 'be'),
    (6, 'to'),
    (6, 'of'),
    (5, 'and')]
```

6. 使用函数find_most_frequent_words查找：
a） [奥巴马演讲]中最常用的十个词(https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/obama_speech.txt)
b） [米歇尔演讲]中最常用的十个词(https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/michelle_obama_speech.txt)
c） [特朗普演讲]中最常用的十个词(https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/donald_speech.txt)
d） [梅琳娜演讲]中最常用的十个词(https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/melina_trump_speech.txt)
7. 编写一个python应用程序来检查两个文本之间的相似性。它接受一个文件或字符串作为参数，并将评估两个文本的相似性。例如，检查[Michelle的]成绩单之间的相似性(https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/michelle_obama_speech.txt)和[梅丽娜的](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/melina_trump_speech.txt)演讲。您可能需要几个函数，清理文本的函数（clean_text），删除支持词的函数（remove_support_words），最后检查相似性的函数（check_text_similarity）。[停用词]列表(https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/stop_words.py)位于数据目录中
8. 在romeo_and_juliet.txt中查找重复次数最多的10个单词
9. 阅读[黑客新闻csv](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/hacker_news.csv)文件并找出：
a） 统计包含python或python的行数
b） 统计包含JavaScript、JavaScript或JavaScript的行数
c） 统计包含Java而非JavaScript的行数

### 练习：第三关

🎉 CONGRATULATIONS ! 🎉

[<< Day 18](../18_Day_Regular_expressions/18_regular_expressions.md) | [Day 20 >>](../20_Day_Python_package_manager/20_python_package_manager.md)
