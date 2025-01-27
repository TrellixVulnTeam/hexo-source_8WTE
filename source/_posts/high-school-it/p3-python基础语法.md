---
title: "high-school-it-p3: python基础语法"
abbrlink: posts/high-school-it/p3
hidden: false
date: 2022-09-12 11:45:45
top: 7997
tags: [高中信息技术]
keywords: [高中信息技术, python]
---
> 正式的对python语法的学习, 包含常见库函数的使用
<!-- more -->

:::tips
有关python的基本介绍, 比如编译/解释/面向对象, 怎么自己下载python, 请看 [p2: 基础科普与环境搭建](/posts/high-school-it/p2)
:::

# 变量与赋值  
编程不就是为了模拟世界, 求解问题吗? 求解问题都需要什么? 
需要数据, 还需要存放数据的地方, ++变量++, 就是这么一个存放数据的地方  

变量变量, 顾名思义, 指的是可变的量 (有些语言严格区分可变性, 但python里不用在意这么多)  
你可以理解为, 变量, 是一个箱子/寄存器, 装着一些可以运算的数值, 用来求解问题, 模拟现实  

有两个概念:
- 声明变量:  创建变量 (声明一个变量出现了)  
- 赋值: 把一个值装到箱子(变量)里

比如, 一个很简单的例子:  

```python
a = 1
```

这里, 我们声明了一个叫做 a 的变量, 然后把值装到了 a 中, 这就是 声明+赋值  
右边是数值, 左边是变量名, 等号表示把右边的值赋给左边的变量  

你也可以这样:  

```python
a = 1
b = a
```

我们先声明了一个变量a, 值是1, 然后把a放在右边传给了左边的b  
第二行表示, 把a里面的数值取出来, 传给了b  

python支持也支持这样的赋值操作, 甚至可以继续长下去

```python
a = b = c = 1
d = e = f = 2

a,b,c = d,e,f
```

上面的代码中, a,b,c都被初始化为1, def则为2, 然后赋值, 把abc的值变成了2


你还可以这样, 表示把b中的值给a, 把a中的值给b, 达到交换值的效果:  

```python
a = 1
b = 2
a,b = b,a
```

你可能会疑惑:  
当我把b中的值给了a时, a的值不就是2了吗, 此时再把a赋值给b, 那b不还是2吗?  
该想法对应的代码是这样的:  

```python
a = 1
b = 2

a = b
b = a
```

但在交换数值的代码中, 你应该这样理解:  

```python
a = 1
b = 2

_t1 = b
_t2 = a
a = _t1
b = _t2
```

这表示, 进行 `a,b = b,a` 时, 会先把右边的变量给复制(赋值给新的变量)一遍, 再分别赋给a,b  
只不过, 只要我们按照py的语法写, 我们就不需要考虑这么多了, py为我们隐藏了_t1, _t2, 你只需要可以这么写就行了  

现在有没有明白, 为什么大家都说py语法简单呢? 之后还会有很多像这样甜的地方 :)

- - -
# 注释

## 作用
注释, 是以py规定的特殊字符, 而开头的语句, 解释器会无视解析到的注释, 只解析代码  
注释, 能够为阅读代码的人提供思路, 迅速明白这段代码做了什么, 而不用一行一行读代码来明白代码做了什么

举个例子:

```python
a = 1  此时 a 的值为 1
```

```python
a = 1  # 此时 a 的值为 1
```

前者会报错, 因为 "此时 a 的值为 1" 也被解释器当作代码而进行解析, 自然就会报错了  
后者不会报错, 因为解释器解析到 # 开头的那段文字后, 会无视/跳过这段注释  

再举个例子:

```python
# 以下的代码能够获取a,b,c三个变量中的最大值, 并进行输出

a = 1
b = 2
c = 3
max = -1
if a > b > c:
  max = a
elif b > c:
  max = b
else:
  max = c
print(max)
```

瞧, 你看上面的代码时,不用一行一行地去理解这段代码到底是干啥的, 直接看别人给你写的注释, 就能大致明白这段代码的作用了  

## 单/多行注释
python 的注释分为两种, 一种是以单行注释, 一种是多行注释, 直接看例子就明白了  

```python
# 12345
# 上山打老虎
# 老虎打不着
# 打到小松鼠

''' 
12345
上山打老虎
老虎打不着
打到小松鼠
'''
```

以井号开头的是单行注释, 通常用在注释仅仅是一两句话的时候  
如果要注释有很多行, 用以三个引号开头, 三个引号结尾的多行注释更方便 (无论单双引号都可以)

- - -
# 基本数据类型
前面说了, 求解问题时, 你需要数据, 还有存放数据的地方  
如何存放数据, 我相信你已经明白了, 现在就要讲数据本身了  

为了模拟现实, py将数据进行了抽象与分类:  


- int: 对应整数  
- float: 对应实数  
- string: 对应文字
- bool: 对应真与假

有了这些 ++基本数据类型++, 我们就能够模拟世界了, 进行抽象, 求解问题了  

举些例子:  
- 我今天吃饭了吗: 用bool来抽象到底吃饭没, True就是吃了, False就是没吃  
- 我的年龄是16岁: 用int来表示 16 这个数字
- 我的名字叫做: 用string来表示 "赵二狗", "Anasdpa" 这样的文字  

同时, 我们还可以用这些 ++基本数据类型++, 构建出 ++复杂数据类型++, 比如, 我想创建一个类型, 叫 student, 表示学生  
你可以这样抽象:  

```python
student {
  age:  int,
  height: float,
  name: string,
  fat_or_not: bool
}
```

py中也有语法, 支持创建自定义的类型, 但不是本系列的重点, 此处仅提一嘴而已

- - -

# 变量命名规范
python中, 变量的命名必须符合规范, 不然直接报错  
在符合规范的同时, 你也应当尽可能地, 让变量名更加清洗直观, 比如年龄用age, 而不是a  

命名规范如下:  
- 变量名由字母, 数字, 下划线组成
- 数字不能在第一位  
- 不能与python中的关键字重名  

以下都是合法的变量名  

```python
a
abada
asd111231
ad190123kkad
asd_asd1_asd2
_123daa
_as11
```

以下是不合法的变量名:  

```python
def
not
in
lambda

1123
123adad
sad;;-``
``?/
',
```

:::tips
**关键字:**  
关键字/保留字, 是python语法中具有特殊含义的东西, 比如for/while/and/or/not/in  
这些都被称作关键字, 一般出现了关键字, 就能用对应的语法, 实现一些效果  
比如for就对应for循环, not就对应逻辑取反, 具有特殊作用
:::

如何判断一个变量名是不是关键字?  
呃...多认识下就知道了... 反正也不可能考没学过的关键字 :)  

- - -

# 运算符与优先级
python 提供了一些运算符, 能够让你进行加减乘除, 逻辑运算之类的操作  
这些运算符, 有各自的优先级, 决定了当运算符有多个时, 应该优先计算哪个  
在以下的图表中, 优先级1是最高, 数字越大优先级越低  

## 算术运算符  
算术运算符, 可以让你对数字类型 (int, float) 进行计算, 得到新的数字  

|运算符|描述|例子|优先级|
|--|--|--|--|
|**|x的y次方|x**y|1|
|*|x乘以y|x*y|2|
|/|x除以y, 产生实数值|x/y|2|
|//|x除以y, 产生整数值|x//y|2|
|%|x除以y, 取余数|x%y|2|
|+|x加y|x+y|3|
|-|x减y|x-y|3|

瞧, 非常符合小学数学的优先级概念, 乘法要比加法先算, 次方要比乘法先算 :)

算术运算符, 可以与赋值运算符相互结合:

```python
a = a + 1

a += 1  # 是上面的等价物
```

类似的, 还有 `-=`, `*=`, `%=`
这种语法在变量名很长时, 会很有用, 不必把变量名写两遍

## 关系运算符
关系运算符, 若关系成立则返回 True, 不然返回 False, 如 `1 < 2` 是 True, 因此又称为 比较运算符  
(关系运算符并不注重优先级, 谁先谁后一眼就看出来了)

|运算符|描述|例子
|--|--|--|
|>| x 大于 y| x > y|
|<| x 小于 y| x < y|
|>=| x 大于等于 y| x >= y|
|<=| x 小于等于 y| x <= y|
|==| x 等于 y| x == y|
|!=| x 不等于 y| x != y|

**注:**  
本博客使用了连体字特性, 因此你看见的>=其实是>号右边跟着=, !=其实是感叹号!后面跟着=, ==其实是两个=

- - -

# 基本数据结构
数据结构, 其实就是数据的存储结构, 根据场景与数据之间的逻辑关系, 设计出的不同复杂程度的结构  

举个例子, 有种数据结构, 叫做 `队列 (Queue)`, 其实模拟的就是日常生活中排队的场景, 对数据进行存储:  
在排队时, 来得越早离开越早, 来得越晚离开越晚, 这不难理解  
此时的队列, 就是一个 `单向队列`, 只允许在一端删除元素(排队的人买好东西走了), 另一端增加数据(新来个排队的)  

根据不同的场景, 不同的逻辑关系, 需要使用不同的方式存储数据, 这种方式, 便是数据结构  
当然, 我们此处仅学习基本数据结构  

## 列表
列表(list) 仅表示装着一定数量元素的序列, 可以通过 索引(index) 访问元素    

### 单索引  
我们可以通过单个索引, 访问对应的单个元素  

举个例子:  

```python
# 有着 3 个元素的列表
list = [300, 400, 500]

# 通过索引, 访问元素 (索引从 0 开始)
list[0] # 300
list[1] # 400
list[2] # 500
```

list 可以通过 index 来访问元素, 那么如果 index 过大呢, 比如下面这样:  

```python
# 有着 3 个元素的列表
list = [300, 400, 500]
list[3]
```

脑子想一想都知道一定会报错:  

```bash
  list[3]
  ~~~~^^^
IndexError: list index out of range
```

果不其然, 解释器告诉我们了报错信息, 提示 "列表的索引越界了"  
如果一个列表的长度length = n, 那么 index 自然要 <= n-1 (从0开始哦~~)

:::tips
**扩展: 为何 index 从 0 开始?**  
因为, 所谓的index, 代表的概念, 其实是 `偏移量`  
实际上, py中的列表, 其元素的内存地址是连续的, 创建一个新的列表时, 会先申请一块内存空间, 用来存放元素  
用下标得到元素时, 实际是通过下标, 计算该元素的对应内存地址, 进行访问, 那么, 如何计算的呢?  

你可以这样理解:  
一个长度为 3(有 3 个元素)的列表, 拥有 3 块内存空间  
你可以从左向右, 画 3 个紧挨在一起的格子, 列表本身, 就代表着这 3 个格子

列表本身的内存地址, 其实就相当于第一个元素的内存地址, 你可以想象为第一个格子  
如何访问第 1 个格子? 第一个格子向右跳 0 格  
如何访问第 2 个格子? 第二个格子向右跳 1 格  
如何访问第 3 个格子? 第三个格子向右跳 2 格  


现在懂了吧? 下标其实就是偏移量, 代表的是 `相对于第 1 个格子偏移了多少格`  
要访问第几个格子, 直接加上偏移量即可 (比如 `list[0]` 偏移了0, 是第一个元素)

如果你非要把下标从 1 开始, 那就得这样:  
list[1] 代表第 1 个元素, 但相对于第一个元素的偏移量还是0  
于是在根据下标1, 求第一个元素时, 偏移量就是 `1 - 1 = 0`  
同理, 根据下标2, 求第二个元素时, 偏移量就是 `2 - 1 = 1`  
同理, 嗯举下标index, 求第 index 个元素时, 偏移量就是 `index - 1`  

如果你每次计算偏移量, 都得计算一遍 index-1, 次数一多起来不就会降低效率?  
现代计算机其实可以忽略这点影响, 但早期计算机可是一寸内存一寸金, 这个习惯自然而然地被保留下来了  
~~(好吧, 原因其实真的只是因为习俗)~~

而且在设计算法, 并且需要考虑下标的边界问题时, 下标从0开始会很方便  
:::

py 中还存在 `负索引` 的语法糖, 也就是用负数来充当索引, 此时, 下标从右往左, 从 -1 依次递减  
比如 `ls[-1]`, 就代表倒数第一个元素, `ls[-2]` 就代表倒数第二个元素  

此时, `ls[-1]`, 就相当于 `ls[len(ls) - 1]` ( len(ls) 表示得到列表ls的长度 )

### 切片
切片, 能通过索引与冒号, 创建一个区间, 访问一定范围内, 列表的多个元素  

举个例子:  

```python
numbers = [201, 202, 203, 204]  # 定义列表
numbers[0:4] # [201, 202, 203, 204]
numbers[0:2] # [201, 202]
```

在上面的例子中, 我们通过索引+冒号, 创建了一个左开右闭的区间, 访问索引在该区间内的所有元素  
如 `0:4` 代表 [0, 1, 2, 3], 再如 `0:2`, 代表 [0, 1]
我们通过 `list[m:n]`, 得到了一个子列表, 只要索引在 `[m, n) (左开右闭区间)` 内, 就会被放入这个子列表  



- - -

## 字典