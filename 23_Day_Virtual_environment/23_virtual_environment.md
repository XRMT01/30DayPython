<div align="center">
  <h1> 30 Days Of Python: Day 23 - Virtual Environment </h1>
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

[<< 第二十二天](../22_Day_Web_scraping/22_web_scraping.md) | [第二十四天 >>](../24_Day_Statistics/24_statistics.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 第二十三天](#-day-23)
  - [Setting up Virtual Environments](#setting-up-virtual-environments)
  - [💻 Exercises: Day 23](#-exercises-day-23)

# 📘 Day 23

## 设置虚拟环境

从项目开始，最好有一个虚拟环境。虚拟环境可以帮助我们创建一个孤立或独立的环境。这将有助于我们避免项目之间的依赖关系冲突。如果你在终端上写pip freeze，你会在电脑上看到所有安装的软件包。如果我们使用virtualenv，我们将只访问特定于该项目的包。打开终端并安装virtualenv

```sh
asabeneh@Asabeneh:~$ pip install virtualenv
```

在30DaysOfPython文件夹中创建一个flask_project文件夹。

安装virtualenv包后，转到项目文件夹，通过编写以下命令创建虚拟环境：

For Mac/Linux:
```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project\$ virtualenv venv

```

For Windows:
```sh
C:\Users\User\Documents\30DaysOfPython\flask_project>python -m venv venv
```

我更喜欢称这个新项目为venv，但可以随意用不同的名字来命名。让我们检查venv是否是使用ls（或windows命令提示符的dir）命令创建的。

```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ ls
venv/
```

让我们通过在项目文件夹中编写以下命令来激活虚拟环境。

For Mac/Linux:
```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ source venv/bin/activate
```
在Windows中激活虚拟环境可能非常依赖于Windows Power shell和git bash。

For Windows Power Shell:
```sh
C:\Users\User\Documents\30DaysOfPython\flask_project> venv\Scripts\activate
```

对于Windows Git bash：
```sh
C:\Users\User\Documents\30DaysOfPython\flask_project> venv\Scripts\. activate
```

编写激活命令后，您的项目目录将以venv开头。请参阅下面的示例。

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$
```

现在，让我们通过编写pip freeze来检查此项目中的可用包。您将看不到任何包裹。

我们要做一个Flask 应用程序项目，所以让我们为这个项目安装Flask 应用程序包。

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ pip install Flask
```

现在，让我们编写pip freeze来查看项目中已安装的软件包列表：

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ pip freeze
Click==7.0
Flask==1.1.1
itsdangerous==1.1.0
Jinja2==2.10.3
MarkupSafe==1.1.1
Werkzeug==0.16.0
```

完成后，您应该使用_deactivate_编辑活动项目。

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython$ deactivate
```

安装了使用Flask 应用程序需的模块。现在，您的项目目录已准备好进行Flask 应用程序项目。您应该将venv包含到.gitignore文件中，而不是将其推送到github。

## 💻 练习: Day 23

1. 基于上述示例，使用虚拟环境创建项目目录。

🎉 CONGRATULATIONS ! 🎉

[<< Day 22](../22_Day_Web_scraping/22_web_scraping.md) | [Day 24 >>](../24_Day_Statistics/24_statistics.md)
