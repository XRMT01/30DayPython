<div align="center">
  <h1> 30 Days Of Python: Day 22 - Web Scraping </h1>
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

[<< Day 21](../21_Day_Classes_and_objects/21_classes_and_objects.md) | [Day 23 >>](../23_Day_Virtual_environment/23_virtual_environment.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 Day 22](#-day-22)
  - [Python Web Scraping](#python-web-scraping)
    - [What is Web Scrapping](#what-is-web-scrapping)
  - [💻 Exercises: Day 22](#-exercises-day-22)

# 📘 第二十二天

##Python Web抓取

###什么是网络剪贴

互联网上充满了可用于不同目的的大量数据。为了收集这些数据，我们需要知道如何从网站上抓取数据。

网络抓取是从网站中提取和收集数据并将其存储在本地计算机或数据库中的过程。

在本节中，我们将使用beautifulsoup和requests包来抓取数据。我们使用的包版本是beautifulsoup 4。

要开始抓取网站，您需要_requests_、_beautifoulSoup4_和_website_。

```sh
pip install requests
pip install beautifulsoup4
```

要从网站上抓取数据，需要对HTML标签和CSS选择器有基本的了解。我们使用HTML标签、类或/和id定位网站内容。
让我们导入请求和BeautifulSoup模块

```py
import requests
from bs4 import BeautifulSoup
```

让我们为要抓取的网站声明url变量。

```py

import requests
from bs4 import BeautifulSoup
url = 'https://archive.ics.uci.edu/ml/datasets.php'

# Lets use the requests get method to fetch the data from url

response = requests.get(url)
# lets check the status
status = response.status_code
print(status) # 200 means the fetching was successful
```

```sh
200
```

使用beautifulSoup解析页面内容

```py
import requests
from bs4 import BeautifulSoup
url = 'https://archive.ics.uci.edu/ml/datasets.php'

response = requests.get(url)
content = response.content # we get all the content from the website
soup = BeautifulSoup(content, 'html.parser') # beautiful soup will give a chance to parse
print(soup.title) # <title>UCI Machine Learning Repository: Data Sets</title>
print(soup.title.get_text()) # UCI Machine Learning Repository: Data Sets
print(soup.body) # gives the whole page on the website
print(response.status_code)

tables = soup.find_all('table', {'cellpadding':'3'})
# We are targeting the table with cellpadding attribute with the value of 3
# We can select using id, class or HTML tag , for more information check the beautifulsoup doc
table = tables[0] # the result is a list, we are taking out data from it
for td in table.find('tr').find_all('td'):
    print(td.text)
```

如果运行此代码，您可以看到提取已完成一半。你可以继续做，因为这是练习1的一部分。
如需参考，请查阅[beautifulsoup文档](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#quick-开始）

🌕 你很特别，你每天都在进步。你只有八天的时间走向伟大。现在做一些锻炼你的大脑和肌肉。

## 💻 练习：第22天

1. 抓取以下网站并将数据存储为json文件（url='http://www.bu.edu/president/boston-university-facts-stats/').
2. 提取此url中的表(https://archive.ics.uci.edu/ml/datasets.php)并将其更改为json文件
3. 废弃presidents表，将数据存储为json格式(https://en.wikipedia.org/wiki/List_of_presidents_of_the_United_States). 表格结构不太合理，报废可能需要很长时间time.

🎉 CONGRATULATIONS ! 🎉

[<< Day 21](../21_Day_Web_scraping/21_class_and_object.md) | [Day 23 >>](../23_Day_Virtual_environment/23_virtual_environment.md)
