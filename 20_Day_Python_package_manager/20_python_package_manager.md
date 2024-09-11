<div align="center">
  <h1> 30 Days Of Python: Day 20 - PIP </h1>
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

[<< 第十九天](../19_Day_File_handling/19_file_handling.md) | [第十二条 >>](../21_Day_Classes_and_objects/21_classes_and_objects.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 20](#-day-20)
  - [Python PIP - Python Package Manager](#python-pip---python-package-manager)
    - [What is PIP ?](#what-is-pip-)
    - [Installing PIP](#installing-pip)
    - [Installing packages using pip](#installing-packages-using-pip)
    - [Uninstalling Packages](#uninstalling-packages)
    - [List of Packages](#list-of-packages)
    - [Show Package](#show-package)
    - [PIP Freeze](#pip-freeze)
    - [Reading from URL](#reading-from-url)
    - [Creating a Package](#creating-a-package)
    - [Further Information About Packages](#further-information-about-packages)
  - [Exercises: Day 20](#exercises-day-20)

# 📘 第二十条

## Python PIP-Python包管理器

### 什么是 PIP ?

PIP代表首选安装程序。我们使用_pip_来安装不同的Python包。
Package是一个Python模块，可以包含一个或多个模块或其他包。我们可以安装到应用程序中的一个或多个模块是一个包。
在编程中，我们不必编写每个实用程序，而是安装包并将其导入到我们的应用程序中。

### 安装 PIP

如果你没有安装pip，让我们现在安装它。转到终端或命令提示符，复制并粘贴以下内容：

```sh
asabeneh@Asabeneh:~$ pip install pip
```

Check if pip is installed by writing

```sh
pip --version
```

```py
asabeneh@Asabeneh:~$ pip --version
pip 21.1.3 from /usr/local/lib/python3.7/site-packages/pip (python 3.9.6)
```

As you can see, I am using pip version 21.1.3, if you see some number a bit below or above that, means you have pip installed.

Let us check some of the packages used in the Python community for different purposes. Just to let you know that there are lots of packages available for use with different applications.

### 使用pip安装软件包

让我们尝试安装名为numeric python的_numpy_。它是机器学习和数据科学界最受欢迎的软件包之一。

- NumPy是使用Python进行科学计算的基本包。其中包括：
  - 一个强大的N维数组对象
  - 复杂的（广播）功能
  - 用于集成C/C++和Fortran代码的工具
  - 有用的线性代数、傅里叶变换和随机数功能

```sh
asabeneh@Asabeneh:~$ pip install numpy
```

让我们开始使用numpy。打开python交互式shell，编写python，然后按如下方式导入numpy：

```py
asabeneh@Asabeneh:~$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
>>> numpy.version.version
'1.20.1'
>>> lst = [1, 2, 3,4, 5]
>>> np_arr = numpy.array(lst)
>>> np_arr
array([1, 2, 3, 4, 5])
>>> len(np_arr)
5
>>> np_arr * 2
array([ 2,  4,  6,  8, 10])
>>> np_arr  + 2
array([3, 4, 5, 6, 7])
>>>
```

Pandas是一个开源、BSD许可的库，为Python编程语言提供高性能、易于使用的数据结构和数据分析工具。让我们安装numpy的大哥_pandas_：

```sh
asabeneh@Asabeneh:~$ pip install pandas
```

```py
asabeneh@Asabeneh:~$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pandas
```

本节不是关于numpy或pandas的，在这里我们试图学习如何安装包以及如何导入它们。如果需要，我们将在其他部分讨论不同的包。

让我们导入一个网络浏览器模块，它可以帮助我们打开任何网站。我们不需要安装这个模块，它已经默认安装在Python 3中了。例如，如果你想在任何时候打开任意数量的网站，或者你想安排一些事情，可以使用这个_webbrowser_模块。

```py
import webbrowser # web browser module to open websites

# list of urls: python
url_lists = [
    'http://www.python.org',
    'https://www.linkedin.com/in/asabeneh/',
    'https://github.com/Asabeneh',
    'https://twitter.com/Asabeneh',
]

# opens the above list of websites in a different tab
for url in url_lists:
    webbrowser.open_new_tab(url)
```

### 卸载软件包

如果您不想保留已安装的软件包，可以使用以下命令将其删除。 

```sh
pip uninstall packagename
```

### 包装清单

查看我们机器上安装的软件包。我们可以使用pip后跟list。

```sh
pip list
```

### 显示套餐

显示有关程序包的信息

```sh
pip show packagename
```

```sh
asabeneh@Asabeneh:~$ pip show pandas
Name: pandas
Version: 1.2.3
Summary: Powerful data structures for data analysis, time series, and statistics
Home-page: http://pandas.pydata.org
Author: None
Author-email: None
License: BSD
Location: /usr/local/lib/python3.7/site-packages
Requires: python-dateutil, pytz, numpy
Required-by:
```

If we want even more details, just add --verbose

```sh
asabeneh@Asabeneh:~$ pip show --verbose pandas
Name: pandas
Version: 1.2.3
Summary: Powerful data structures for data analysis, time series, and statistics
Home-page: http://pandas.pydata.org
Author: None
Author-email: None
License: BSD
Location: /usr/local/lib/python3.7/site-packages
Requires: numpy, pytz, python-dateutil
Required-by:
Metadata-Version: 2.1
Installer: pip
Classifiers:
  Development Status :: 5 - Production/Stable
  Environment :: Console
  Operating System :: OS Independent
  Intended Audience :: Science/Research
  Programming Language :: Python
  Programming Language :: Python :: 3
  Programming Language :: Python :: 3.5
  Programming Language :: Python :: 3.6
  Programming Language :: Python :: 3.7
  Programming Language :: Python :: 3.8
  Programming Language :: Cython
  Topic :: Scientific/Engineering
Entry-points:
  [pandas_plotting_backends]
  matplotlib = pandas:plotting._matplotlib
```

### PIP 冻结

生成已安装的Python包及其版本，输出适合在需求文件中使用。requirements.txt文件是一个应该包含Python项目中所有已安装Python包的文件。

```sh
asabeneh@Asabeneh:~$ pip freeze
docutils==0.11
Jinja2==2.7.2
MarkupSafe==0.19
Pygments==1.6
Sphinx==1.2.2
```

pip冻结为我们提供了使用、安装的软件包及其版本。我们将其与requirements.txt文件一起用于部署。

### 从URL读取

现在，您已经熟悉了如何在本地计算机上读取或写入文件。有时，我们想从使用url的网站或API阅读。
API代表应用程序接口。它是一种在服务器之间交换结构化数据的方法，主要是json数据。要打开网络连接，我们需要一个名为_requests_的包，它允许打开网络连接并实现CRUD（创建、读取、更新和删除）操作。在本节中，我们将只介绍读取矿石获取CRUD的一部分。

让我们安装 _requests_:

```py
asabeneh@Asabeneh:~$ pip install requests
```

我们将在_requests_模块中看到_get_、_status_code_、_headers_、_text_和_json_方法：
  - _get（）_：打开网络并从url获取数据-它返回一个响应对象
  - _status_code_：获取数据后，我们可以检查操作的状态（成功、错误等）
  - _headers_：检查标头类型
  - _text_：从获取的响应对象中提取文本
  - _json_：提取json数据
让我们从这个网站上读一个txt文件，https://www.w3.org/TR/PNG/iso_8859-1.txt.

```py
import requests # importing the request module

url = 'https://www.w3.org/TR/PNG/iso_8859-1.txt' # text from a website

response = requests.get(url) # opening a network and fetching a data
print(response)
print(response.status_code) # status code, success:200
print(response.headers)     # headers information
print(response.text) # gives all the text from the page
```

```sh
<Response [200]>
200
{'date': 'Sun, 08 Dec 2019 18:00:31 GMT', 'last-modified': 'Fri, 07 Nov 2003 05:51:11 GMT', 'etag': '"17e9-3cb82080711c0;50c0b26855880-gzip"', 'accept-ranges': 'bytes', 'cache-control': 'max-age=31536000', 'expires': 'Mon, 07 Dec 2020 18:00:31 GMT', 'vary': 'Accept-Encoding', 'content-encoding': 'gzip', 'access-control-allow-origin': '*', 'content-length': '1616', 'content-type': 'text/plain', 'strict-transport-security': 'max-age=15552000; includeSubdomains; preload', 'content-security-policy': 'upgrade-insecure-requests'}
```

  - 让我们阅读API。API代表应用程序接口。它是一种在服务器之间交换结构数据的方法，主要是json数据。API示例：https://restcountries.eu/rest/v2/all.让我们使用_requests_模块来阅读这个API。

```py
import requests
url = 'https://restcountries.eu/rest/v2/all'  # countries api
response = requests.get(url)  # opening a network and fetching a data
print(response) # response object
print(response.status_code)  # status code, success:200
countries = response.json()
print(countries[:1])  # we sliced only the first country, remove the slicing to see all countries
```

```sh
<Response [200]>
200
[{'alpha2Code': 'AF',
  'alpha3Code': 'AFG',
  'altSpellings': ['AF', 'Afġānistān'],
  'area': 652230.0,
  'borders': ['IRN', 'PAK', 'TKM', 'UZB', 'TJK', 'CHN'],
  'callingCodes': ['93'],
  'capital': 'Kabul',
  'cioc': 'AFG',
  'currencies': [{'code': 'AFN', 'name': 'Afghan afghani', 'symbol': '؋'}],
  'demonym': 'Afghan',
  'flag': 'https://restcountries.eu/data/afg.svg',
  'gini': 27.8,
  'languages': [{'iso639_1': 'ps',
                 'iso639_2': 'pus',
                 'name': 'Pashto',
                 'nativeName': 'پښتو'},
                {'iso639_1': 'uz',
                 'iso639_2': 'uzb',
                 'name': 'Uzbek',
                 'nativeName': 'Oʻzbek'},
                {'iso639_1': 'tk',
                 'iso639_2': 'tuk',
                 'name': 'Turkmen',
                 'nativeName': 'Türkmen'}],
  'latlng': [33.0, 65.0],
  'name': 'Afghanistan',
  'nativeName': 'افغانستان',
  'numericCode': '004',
  'population': 27657145,
  'region': 'Asia',
  'regionalBlocs': [{'acronym': 'SAARC',
                     'name': 'South Asian Association for Regional Cooperation',
                     'otherAcronyms': [],
                     'otherNames': []}],
  'subregion': 'Southern Asia',
  'timezones': ['UTC+04:30'],
  'topLevelDomain': ['.af'],
  'translations': {'br': 'Afeganistão',
                   'de': 'Afghanistan',
                   'es': 'Afganistán',
                   'fa': 'افغانستان',
                   'fr': 'Afghanistan',
                   'hr': 'Afganistan',
                   'it': 'Afghanistan',
                   'ja': 'アフガニスタン',
                   'nl': 'Afghanistan',
                   'pt': 'Afeganistão'}}]
```

如果我们正在获取json数据，我们将从响应对象中使用_json（）_方法。对于txt、html、xml和其他文件格式，我们可以使用_text_。

### 创建包

我们根据一些标准将大量文件组织在不同的文件夹和子文件夹中，以便我们可以轻松地找到和管理它们。如您所知，一个模块可以包含多个对象，如类、函数等。一个包可以包含一个或多个相关模块。包实际上是一个包含一个或多个模块文件的文件夹。让我们使用以下步骤创建一个名为mypackage的包：

在30DaysOfPython文件夹中创建一个名为mypacakge的新文件夹
在mypackage文件夹中创建一个空的**__init__**.py文件。
使用以下代码创建模块算术.py和greet.py：

```py
# mypackage/arithmetics.py
# arithmetics.py
def add_numbers(*args):
    total = 0
    for num in args:
        total += num
    return total


def subtract(a, b):
    return (a - b)


def multiple(a, b):
    return a * b


def division(a, b):
    return a / b


def remainder(a, b):
    return a % b


def power(a, b):
    return a ** b
```

```py
# mypackage/greet.py
# greet.py
def greet_person(firstname, lastname):
    return f'{firstname} {lastname}, welcome to 30DaysOfPython Challenge!'
```

您的包的文件夹结构应该如下所示：

```sh
─ mypackage
    ├── __init__.py
    ├── arithmetic.py
    └── greet.py
```

现在，让我们打开python交互式shell并尝试我们创建的包：

```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from mypackage import arithmetics
>>> arithmetics.add_numbers(1, 2, 3, 5)
11
>>> arithmetics.subtract(5, 3)
2
>>> arithmetics.multiple(5, 3)
15
>>> arithmetics.division(5, 3)
1.6666666666666667
>>> arithmetics.remainder(5, 3)
2
>>> arithmetics.power(5, 3)
125
>>> from mypackage import greet
>>> greet.greet_person('Asabeneh', 'Yetayeh')
'Asabeneh Yetayeh, welcome to 30DaysOfPython Challenge!'
>>>
```

正如你所看到的，我们的包装工作得很好。包文件夹包含一个名为**__init__**.py的特殊文件，用于存储包的内容。如果我们将**__init__**.py放在包文件夹中，python start会将其识别为包。
**__init__**.py从其模块中公开指定的资源，以导入到其他python文件中。导入包时，一个空的**__init__**.py文件使所有函数都可用。**__init__**.py对于Python将文件夹识别为包至关重要。

### 关于套餐的更多信息

- 数据库
  - SQLAlchemy 或 SQLObject - 面向对象的访问多种不同数据库系统的工具
    - _pip install SQLAlchemy_
- Web开发
  - Django - 高级Web框架。
    - _pip install django_
  - Flask - 基于Werkzeug和Jinja 2的Python微型框架。（它是BSD授权的）
    - _pip install flask_
- HTML解析器
  - [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - 为快速周转项目如屏幕抓取设计的HTML/XML解析器，能够接受不良的标记。
    - _pip install beautifulsoup4_
  - PyQuery - 实现了Python中的jQuery；据称比BeautifulSoup更快。

- XML处理
  - ElementTree - Element类型是一种简单但灵活的容器对象，旨在内存中存储层次数据结构，如简化的XML信息集。--注意：Python 2.5及更高版本在标准库中包含ElementTree
- 图形用户界面
  - PyQt - 跨平台Qt框架的绑定
  - TkInter - 传统的Python用户界面工具包
- 数据分析、数据科学与机器学习
  - Numpy: Numpy（数值Python）是Python中最受欢迎的机器学习库之一。
  - Pandas: 是一个用于数据分析、数据科学和机器学习的Python库，提供了高级的数据结构和各种分析工具。
  - SciPy: SciPy是一个面向应用开发者和工程师的机器学习库。SciPy库包含了优化、线性代数、积分、图像处理和统计等模块。
  - Scikit-Learn: 它基于NumPy和SciPy，被认为是处理复杂数据的最佳库之一。
  - TensorFlow: 是由Google开发的机器学习库。
  - Keras: 被认为是Python中最酷的机器学习库之一。它提供了一个更简单的表达神经网络的机制。Keras还提供了编译模型、处理数据集、图形可视化等方面的最佳工具。
- 网络
  - requests: 是一个可以用来向服务器发送请求（GET, POST, DELETE, PUT）的包
    - _pip install requests_

🌕 你一直在进步，并且你已经领先了20步迈向伟大的道路上。现在做些锻炼来活动你的大脑和肌肉。

## 练习 : 第二十天

1. 读取这个网址并找出最常出现的10个单词。 romeo_and_juliet = 'http://www.gutenberg.org/files/1112/1112.txt'
2. 读取猫的API并将cats_api = 'https://api.thecatapi.com/v1/breeds'，找到:
   1. 猫的重量在公制单位下的最小值、最大值、平均值、中位数、标准差。
   2. 猫的寿命在年份下的最小值、最大值、平均值、中位数、标准差。
   3. 创建一个关于猫的国家和品种的频率表。
3. 读取[countries API](https://restcountries.eu/rest/v2/all)，并找到
   1. 最大的10个国家
   2. 最常用的语言前10名
   3. 在countries API中的语言总数
4. UCI是最常见的获取数据集的地方之一，适用于数据科学和机器学习。读取UCL的内容 (https://archive.ics.uci.edu/ml/datasets.php)。没有额外的库将会很困难，所以你可以尝试使用BeautifulSoup4来完成。

🎉 CONGRATULATIONS ! 🎉

[<< Day 19](../19_Day_File_handling/19_file_handling.md) | [Day 21 >>](../21_Day_Classes_and_objects/21_classes_and_objects.md)
