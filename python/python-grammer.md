#  简介

## 介绍

- 同样的python代码，可以在不同操作系统运行，只要对应的平台安装了python解释器
- 运行速度慢：解释型语言，代码运行时通过解释器翻译成机器码再执行
- 内存消耗大
- 开源语言，最终的.py文件能被逆向查看，可以将其打包成.exe

## 编译型 vs 解释型

### 编译型

- 同一运行平台，代码只需编译一次，执行效率高
- 跨平台性差，大型项目编译时间长，开发效率低

![image-20260627115908205](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260627115908205.png)

### 解释型

- 逐行运行，不同平台安装对应的解释器即可
- 跨平台性好，无需编译，开发调试灵活高效
- 每次运行都需要重新解释，执行效率低

![image-20260627120127266](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260627120127266.png)



- 基本语法

![image-20260627154405934](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260627154405934.png)

## 入门

### 注释

```python
# 1. 单行注释

"""多行注释：Docstring一般用来函数，类，模块的说明"""
'''另外一种写法'''
print("hello")
```

### 标识符

- 数字，字母，下划线，不能以数字开头，不能包含空格
- 大小写敏感

### 数据类型

- 变量没有类型，数据有类型

```python
# <class 'str'>
print(type("Erick"))
```

```python
# 方便看的一种方式
price = 300000
age = 3_0_0

print(price)
print(age)

# 整数上限：取决于执行代码的计算机的内存和处理能力
a = 9 ** 999
print(a)
```

```python
name = 'erick'
age = 13
address = "北京"

# 字符串拼接
print(f"我是 {name}---{age}={address}")
```

### 输入输出

```python
print("hello,输入你的年龄")
result = input()
print(result)
```

## 流程控制

### if else

```python
age = 10
name = "erick"

if age < 10:
    if name == "erick":
        print("erick-10")
elif age < 20:
    if name == "erick":
        print('lucuy20')

else:
    print("go")
```

### 循环

```python
# while 循环
a = 1
while a < 10:
    print(a)
    a += 1

print("========")

# for 循环
# [3,10),   左边为0时可以省略
for i in range(3, 10):
    print(i)
```

## 函数

- 基本函数

```python
def sleep(name, hours):
    print(f"{name} is going to sleep for {hours} hours")


sleep("Erick", 19)
```

- 关键字参数：具体交给哪个形参

```python
def sleep(name, address, age, time):
    print(f"{name} is {age} years old, will sleep for {time} seconds in {address}.")


sleep(address="beijing", name="erick", age="20", time="200")
```

- 可选参数，参数默认值

```python
def sleep(age, name="erick", ):
    print(f"{name} is {age} years old")
```

## 数据容器

### 列表

- 其实就是数组
- 一个列表里面，可以包含多个不同类型的数据

```python
fruits = ["apple", "banana", "cherry"]
```

### 元祖

- 元素的值不可修改，引用类型可修改

```python
fruits = ("apple", "banana", "cherry")
```

### 集合

- 可变集合SET: 无序，驱虫

```python
fruits = {"apple", "banana", "cherry"}
```

- 不可变集合frozenset

```python
fruits = frozenset({"apple", "banana", "cherry"})
```

### 字典

```python
erick = {"name": "", "age": 25}
print(erick)
print(erick["age"])
```

## 面向对象

- 方法名命名规范：全小写字母，单词之间用下划线 `_` 分隔（snake_case）

### 类

#### 初始化方法

```python
class Person:
    # 构造方法
    def __init__(self, name, age, address):
        self.name = name
        self.age = age
        self.address = address


erick = Person("Erick", 12, "北京")

# 查看地址值: <__main__.Person object at 0x100f9ea50>
print(erick)

# 查看具体某个属性
print(erick.name)

# 增加属性
erick.info = "heihei"

# 查看这个实例所有属性
print(erick.__dict__)

print(type(erick))
```

#### 类方法

```python
class Person:
    # 构造方法
    def __init__(self, name, age, address):
        self.name = name
        self.age = age
        self.address = address

    # 自定义方法
    def sleep(self, info):
        print(self.age, info)

erick = Person("Erick", 12, "北京")

# 调用类的方法
erick.sleep(5)

# 查看这个类的所有属性和方法
print(Person.__dict__)
```

#### 类方法/静态方法

```python
class Person:

    # 类方法: 通过类类调用，cls当前类
    @classmethod
    def run(cls, name):
        print(f"Hello {name}")

    # 静态方法，只接收自定义参数
    @staticmethod
    def say(name):
        print(f"Hello {name}")

    # 构造方法
    def __init__(self, name, age, address):
        self.name = name
        self.age = age
        self.address = address

    # 自定义方法
    def sleep(self, info):
        print(self.age, info)


Person.run("erick")
```

# 模块化

- 自定义模块：本项目中的
- 标准库模块：python自带
- 第三方模块：别的项目中的，安装到本项目中的

## 模块

### 自定义模块

- 本项目中使用的

- import模块名

```python
max_order_amount = 0


def create_order():
    print("create order")


def show_info():
    print("show order info")
```

```python
max_pay_amount = 100


def pay_for_good():
    print("pay for good")


def show_info():
    print("good info")
```

```python
# import引入
import order
import pay

print(order.max_order_amount);
order.create_order()
order.show_info()

print(pay.max_pay_amount)
pay.pay_for_good()
pay.show_info()
```

- import 模块名 as 别名

```python
# import 模块名 as 别名
import order as or_der
import pay as p_ay

print(or_der.max_order_amount)
or_der.create_order()
or_der.show_info()

print(p_ay.max_pay_amount)
p_ay.pay_for_good()
p_ay.show_info()
```

- from 模块名 import 具体内容1，具体内容2: 部分引入

```python
from order import max_order_amount
from pay import show_info, pay_for_good

print(max_order_amount)

pay_for_good()
show_info()
```

- from 模块名 import 具体内容1 as 别名1，具体内容2 as 别名2: 部分引入

```python
from order import max_order_amount as amount
from pay import show_info as show, pay_for_good as pay_lea

print(amount)

pay_lea()
show()
```

### 标准库模块

- 安装python后，python自带的模块: [标准库](https://docs.python.org/zh-cn/3.13/library)

```python
import random
import time

fruits = ["apple", "banana", "orange", "mango"]
print(random.choice(fruits))

time.sleep(1)

print("hi")
```

## 包

- 包含_ _init_ _.py的文件夹，就是一个包
- 包中包含了多个模块
- 一个包中可以包含多个包

### 自定义包

- new Python Package
- 引入方式和模块化类似

![image-20260628113254218](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260628113254218.png)

```python
max_order_amount = 100


def show():
    print("show order")
```

#### _ _init_ _.py

- 是包的初始化文件，在包被导入时，会被自动调用
- 可以编写一些包的初始化逻辑

# 安装

## Python

- 下载对应的python解释器

### MAC

#### 官网 .pkg

- [下载网址](https://www.python.org/downloads/)： 3.13.12，傻瓜式安装即可

![image-20260627152212699](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260627152212699.png)

```bash
# 查看对应的版本
python3 --version

Python 3.13.12

# 如果想使用下面的命令，则去做个映射
sudo echo 'alias python="python3"' >> .zshrc

# 重新打开终端
python --version

# mac上 
# 查看版本： pip和python版本一致
# 不要使用裸pip，避免误调用系统残留的旧版 pip
# 查看python的当前对应解释器的pip的版本： pip会自动和python一起安装
# pip 25.3 from /Library/Frameworks/Python.framework/Versions/3.13/lib/python3.13/site-packages/pip (python 3.13)
python -m pip --version

# 安装全局依赖
python -m pip install numpy
```

## 三方包repo

- 用来存储知名组织或者三方提供的python包

### PYPI

- Python默认的第三方包的存储
- [官方网址](https://pypi.org/)

![image-20260704151658255](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260704151658255.png)

```bash
# 默认最新版本
python -m pip install numpy

# 指定版本
# 终端执行时强烈建议加上引号
python -m pip install "numpy==2.4.6"

# 兼容版本(最推荐)         
# 锁定前两个版本，最后一个版本可变   等价于 >=2.5.0, <2.9.0
python -m pip install "numpy~=2.5.0"

# 安装路径
cd /Library/Frameworks/Python.framework/Versions/3.13/lib/python3.13/site-packages/

# 安装了一个版本，就会把之前的版本卸载掉，不管新装的版本是不是比之前的版本 新或者旧
numpy			               # 主要的包就是这个
numpy-2.4.6.dist-info    # 对该包的一些说明
```

```bash
# 查看当前下载了哪些三方包
python -m pip list

# mac全局配置镜像
 # 方式1:创建目录，如果不存在
mkdir -p ~/.config/pip
 # 写入配置
cat > ~/.config/pip/pip.conf << 'EOF'
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
trusted-host = pypi.tuna.tsinghua.edu.cn
timeout = 60
EOF

 # 方式2:单独配置
python -m pip config set global.index-url https://mirrors.aliyun.com/pypi/simple

# 查看当前镜像地址
python -m pip config list
global.trusted-host='pypi.tuna.tsinghua.edu.cn'

# 使用默认官方地址： 就会删除这个key
python -m pip config unset global.index-url

# 查看某个参数：输出为空
python -m pip config get global.index-url
```

## 环境

- 环境：python解释器 + 依赖包
- 使用 venv来隔离项目环境，使用pip来进行包管理

### 全局环境

- python安装之后的目录，就是称为全局环境

```bash
# 解释器： 二进制文件
/Library/Frameworks/Python.framework/Versions/3.13/bin/python3.13

# 标准库:  随python自带的模块
/Library/Frameworks/Python.framework/Versions/3.13/lib/python3.13

# 第三方模块： pip install默认写入的位置
/Library/Frameworks/Python.framework/Versions/3.13/lib/python3.13/site-packages
```

### 虚拟环境

- 如果安装在全局环境中，不同项目，引入的第三方包不同(互相覆盖)，python解释器版本不同(冲突)
- 必须依赖全局环境创建出，一旦创建出来，所有的东西都是自己的(除了标准库)，但是一旦删了全局环境，虚拟环境就会报错
- 一般虚拟环境解释器===全局环境解释器，所以才会共用标准库，这也是最推荐的一种方式
- 开发、CI、生产三端的 Python 主版本 + 次版本必须严格一致
- 开发python项目，必须使用虚拟环境

#### Pycharm创建

- 选择基于本地安装的python解释器的目录

![image-20260704171641001](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260704171641001.png)

#### 进出虚拟环境

- 方式一：命令行

```bash
# 进入虚拟环境： 进入后可以执行pip install等操作
cd /Users/shuzhan/Desktop/erick-test      # 进入项目目录
source .venv/bin/activate                 # 激活虚拟环境：只能在mac和windows中使用，在windows中无法使用
pip install numpy==2.4.5

# 推出虚拟环境
deactivate 
```

- 方式二：点击进入这个终端，不推荐

![image-20260701074839491](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260701074839491.png)

- .venv不会上传到repo中，只需要把python代码上传到repo中，然后重新创建对应的虚拟环境即可

![image-20260704173324909](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260704173324909.png)

## UV

- Python包管理器和环境管理工具
- 2024年发布的，Astral公司，用Rust编写的
- [官方文档](https://docs.astral.sh/uv/)

### MAC安装

```bash
# 安装
# 安装路径：installing to /Users/shuzhan/.local/bin
curl -LsSf https://astral.sh/uv/install.sh | sh

# 根据提示，配置
source $HOME/.local/bin/env

# 查看版本
uv --version

# 升级版本
uv self update 
```

### UV项目初始化

- UV项目不需要本地提前安装python，只需要uv能联网，就能自己去下载对应的python解释器

```bash
# 初始化项目
uv init --python 3.14                         # 在当前目录文件夹生成项目文件
uv init erick_uv_demo --python 3.14           # 在当前文件夹，创建erick_uv_demo这个目录

# 进入目录
cd erick_uv_demo 

# 添加依赖，自动更新 pyproject.toml + uv.lock）
uv add "numpy==1.26.4"
uv add "pyfiglet==1.0.3"

# 运行脚本：自动激活 .venv, 无需source
uv run python main.py


# uv sync
- 检查 uv.lock和pyproject.toml 是否一致
- 创建/修复虚拟环境 
       - 创建：项目到服务器上后，执行可创建虚拟环境
       - 修复：本地虚拟环境的更新
```

```bash
# 上传到git的清单
- main.py           # 源文件

# 核心配置文件， 定义项目元数据，依赖，构建系统
# 鼓励修改，修改后uv sync
- pyproject.toml   

 # 强烈建议上传，          禁止手动修改
- uv.lock       

#  # 记录了python版本    尽量避免直接修改
- .python-version  
```

![image-20260705005607009](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260705005607009.png)

```bash
# 查看对应的python解释器安装位置
uv python dir
/Users/shuzhan/.local/share/uv/python

# 会有多个不同的版本, 可以在本地安装多个不同的python解释器
cpython-3.13-macos-aarch64-none		cpython-3.14-macos-aarch64-none
cpython-3.13.14-macos-aarch64-none	cpython-3.14.6-macos-aarch64-none
```

```bash
# 切换/更新 python版本
# 更换版本，同时更新pyproject.toml
uv python pin 3.12 --update-requires-python
```

# 发布

## 普通方式

- 包含py文件，requirements.txt

![image-20260704190800301](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260704190800301.png)

```bash
# 1. 获取三方依赖清单
# 进入当前项目结构中  /Users/shuzhan/Desktop/erick_demo
pip freeze > requirements.txt

# 2. 把erick.py和requirements.txt上传到linux中
# 在linux上创建目录
mkdir -p ~/projects/erick_demo

# 把erick.py和requirements.txt上传到linux中的这个目录中

# 3  创建虚拟环境      进入对应的目录结构
python3.13 -m venv .venv     # .venv  虚拟环境的名字

# 4. 激活虚拟环境
source .venv/bin/activate

# (.venv) root@iZ2ze8m1xo3ifsqlz6d6sgZ:~/projects/erick_demo# 

# 5. 安装依赖
# pip 26.1.2 from /root/projects/erick_demo/.venv/lib/python3.13/site-packages/pip (python 3.13)
pip --version     

# 安装依赖
pip install -r requirements.txt           # -r： requirements

# 6. 运行脚本
python erick.py
```

## UV



# 包管理器

![image-20260701081725863](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260701081725863.png)

## conda

- 是Anaconda公司创建的，一个用于python包管理的工具，类似于pip
- conda环境中可以使用pip，但建议先用conda装底层依赖，再用pip补充python包，不要随意反复交替使用

![image-20260701081939037](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260701081939037.png)

### 下载

- [官网链接](https://www.anaconda.com/download/success)

![image-20260702120216367](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260702120216367.png)