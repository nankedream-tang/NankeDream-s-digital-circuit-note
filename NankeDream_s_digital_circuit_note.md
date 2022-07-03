# 数字电子技术基础

**By NankeDream**

# 〇、绪论

## 1. 数字量和模拟量

- **数字量**：在时间上和数量上都是离散的、不连续的，存在一个最小单位
- 模拟量：数字量以外的物理量

Continuous versus Discrete

- Which are “continuous”?

  Color light Cars Sound Height and weight Dogs Electric current and voltage

- 数字电路和模拟电路

  工作信号、研究的对象、分析/设计方法以及所用的数学工具都有显著的不同

## 2. 什么是电子技术

是研究电子器件及电子器件应用的一门学科

- 电子器件：通过控制器件中电子的运动而进行工作
- 电子技术的发展：集成电路、摩尔定律

## 3. 电子电路的作用

- 处理信息 能量转换

- 模拟电路：用连续的模拟电压/流指来表示信息
- **数字电路**：用一个连续的电压序列来表示信息

Structure 结构

- hierarchical design
- limited complexity at each level
- reusable building blocks

复用：可重复使用的构建模块

Interfaces 接口

- Key elements of system engineering
- Isolate technologies,allow evolution
- Major abstraction mechanism

What makes a good system design?

- minimal mechanism,maximal function
- reliable in a wide range of environments
- accommodates future technical improvements

## 4. Our plan 

- Understand how things work,bottom-up
- Encapsulate(封装) our understanding using appropriate abstractions
- Study organizational principles: abstractions,interfaces,API(Application Programming Interface)
- Roll up our sleeves and design at each level of hierarchy

- Learn engineering tricks
  - History
  - Systematic approaches
  - Algorithms
  - Diagnose,fix,and avoid bugs

# 一、信息与编码

理想的离散是不存在的

## 1. What is "Information"?

### (1) information:

- Knowledge,communicated or received concerning a particular fact or circumstance.

Information resolves uncertainty

- Information is simply that which cannot be predicted. The less predictable a message is the more information it conveys!

### (2) Quantifying Information

Suppose you are faced with N equally probable choices,and I give you a fact that narrows it down to M choices. Then I have given you

- log2(N/M) bits of information 

### (3)  Encoding 编码

- Encoding describes the process of assigning representations to information
- Choosing an appropriate and efficient encoding is a real engineering challenge
- Impacts design at many levels
  - Mechanism (devices.# of components used)
  - Efficiency (bits used)
  - Reliability (noise)
  - Security (encryption)

example: 2011010909

- 数制：表述数量的规则
- 码制：表示事物的规则

### (4) 我们常用到的：

**十进制 D(Decimal)、二进制 B(Binary)、八进制 O(Octal)、十六进制 H(Hexadecimal)**

## 2. 转换

### (1) 二—十转换

将二进制数展开后按十进制相加，即可得到十进制数

例![d4e0c1b29de11cc42afe2a3dc9e2f3f](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/d4e0c1b29de11cc42afe2a3dc9e2f3f.jpg?raw=true)

### (2) 十—二转换

对于整数部分，将十进制整数不断除以二直到得到0，可依次得到余数（0 or 1），将得到的余数从右向左书写，即可得到二进制数。

例

![](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220628225430.png?raw=true)



对于小数部分，将十进制小数不断乘以二，直到得到1，可依次得到整数部分（0 or 1），将得到的整数部分依次排列，即得到二进制的小数。

例

![QQ截图20220628225625](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220628225625.png?raw=true)

### (3) 二—十六转换

将整数部分与小数部分分别拆分为四个0 or 1一组的数据组，其中若整数部分的位数不是4的倍数，则高位补0，若小数部分的位数不是4的倍数，则低位补0.将每组二进制数用对应的十六进制数代替，可得到一个十六进制数据。

例

![QQ截图20220628231542](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220628231542.png?raw=true)

### (4) 十六—二转换

为二—十六转换的逆过程。

例

![QQ截图20220628231828](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220628231828.png?raw=true)

### (5) 八—二 与 二—八 转换

与十六进制的转换类似，将四位一组变为三位一组，首尾补0.

例![QQ截图20220628232118](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220628232118.png?raw=true)

## 3. 二进制的算数运算

### (1) 算数运算

![QQ截图20220628233626](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220628233626.png?raw=true)

​    二进制数的正负号也是用0/1表示的。

​    在定点运算中，最高位为符号位（0为正。1为负）

​    如 +5 = 0  0101    -5 = 1  0101

​    +5 + -5 = 0 0101 + 1 0101 = ？？

### (2) 反码、补码和补码运算

- 1011 - 0111 = 1011 + 1001 = (1)0100  

  其中，1001 为 -0111 的补码，括号里的 1 为进位，需舍去，对于4位二进制数，基数为16(10000)，所以 1001(9) 恰好是 -0111(-7) 对模 16 的补码。

  对于有效数字（不包括符号位）为 n 位的二进制数 N ，它的补码 (N)comp 表示方法为：

![QQ截图20220630002303](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630002303.png?raw=true)

​        **即正数（符号位为0）的补码与原码相同，负数（符号位为1）的补码为 2^n - N。符号位保持不变。不过这样仍然要做减法，对于更简便的方法：当  N 为负数时，先求出 N的反码 (N)inv , 即保持符号位不变，将数值位逐位求反， 得到反码，然后将反码加 1 ，即可得到二进制负数的补码。**

​                                                                                  ![  ](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630003319.png?raw=true)

例：

![QQ截图20220630003538](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630003538.png?raw=true)

- 对于小数

  **取反加 1 是加在最右边，不是加数值 1 。**

  

- 运算时，若需要添加符号位，则需**留足运算范围**，4 位 ：-8~7；5位：-16~15；6位：-32~31

  在编码取值合适的情况下，两个加数的符号位和来自最高位数字位的进位相加。结果就是和的符号位。

  ![QQ截图20220630011047](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630011047.png?raw=true)

## 4. 码制

用不同数码表示不同事物时遵循的规则，例如：学号、身份证号、车牌号......

- 目前，数字电路中都采用二进制
- 表示数量时称二进制
- 表示事物时称二值逻辑

### (1) Fixed-length encodings  等长编码

- If all choices are equally likely (or we have no reason to expect otherwise), then a fixed-length code is often used. such a code will use at least enough bits to represent the information content. 
- 8421码(BCD代码)、余3码、2421码、5211码、余3循环码

### (2) 格雷码

**每一位的状态变化都按一定顺序循环。编码顺序一次变化，按表中顺序变化时，相邻代码只有一位改变状态**。

![QQ截图20220630104528](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630104528.png?raw=true)

应用：减少编码变化过程中产生的“噪声”，变化快。

### (3) When choices are not equally probable 变长编码 Variable-length encodings

When the choices have different probabilities(pi), you get more information when learning of a unlikely choice than when learning of a likely choice

**出现频率越高的字母用短的编码表示，反之用越长的编码表示**

Use shorter bit sequences for high probability choices, longer sequences for less probable choices

### (4) 哈夫曼编码

如何进行哈夫曼编码？

使用需要传送的字符构造字符集C = {c1, c2, ... cn}，并根据字符出现的频率构建概率集W = {w1, w2, ... wn}。哈夫曼编码的流程如下：

- 将字符集C作为叶子节点
- 将频率集W作为叶子节点的权值
- 使用C和W构造哈夫曼树
- 对哈夫曼树的所有分支，左子树分支编码为0，右子树分支编码为1

通过上述流程，即完成了哈夫曼编码。

例

设定字符集为C = {T1, T2, T3, T4}，对应的频率集为W = {2, 3, 7, 5}，可以构造出下面的哈夫曼树

![v2-495953c0d143c054a19f14d93955832b_1440w](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/v2-495953c0d143c054a19f14d93955832b_1440w.jpg?raw=true)

那么，T1 = 110    T2 = 111    T3 = 0    T4 = 10



# 二、逻辑代数基础

**基本逻辑运算、基本·公式、表示方法、化简**

## 1. 概述

逻辑：事物的因果关系

逻辑运算的数学基础：逻辑代数（布尔）在二值逻辑中的变量取值：0/1

- 1854: George Boole shows that logic is math, not just philosophy!

- Boolean algebra: the mathematics of binary values

- Despite existence of relays and introduction of vacuum tube in 1906. Digital electronics did not emerge for thirty years!

- Claude Shannon notices similarities between Boolean algebra and electronic telephone switches

- Shannon's 1937 MIT Master's Thesis introduces the world to binary digital electronics

  

## 2. 逻辑代数中的三种基本运算

![QQ截图20220630125940](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630125940.png?raw=true)

### (1) 与（AND）

- 条件同时具备，结果发生

- Y = A   AND  B  = A&B = A * B = AB

  | A    | B    | Y    |
  | ---- | ---- | ---- |
  | 0    | 0    | 0    |
  | 0    | 1    | 0    |
  | 1    | 0    | 0    |
  | 1    | 1    | 1    |

### (2) 或（OR）

- 条件之一具备，结果发生

- Y= A OR B = A + B

  | A    | B    | Y    |
  | ---- | ---- | ---- |
  | 0    | 0    | 0    |
  | 0    | 1    | 1    |
  | 1    | 0    | 1    |
  | 1    | 1    | 1    |

### (3) 非(NOT)

- 条件不具备，结果发生

- Y = A' = NOT A

  | A    | Y    |
  | ---- | ---- |
  | 0    | 1    |
  | 1    | 0    |

## 3. 几种常用的复合逻辑运算

![QQ截图20220630130606](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630130606.png?raw=true)

### (1) 与非

- **先 与 后 非**

  | A    | B    | Y    |
  | ---- | ---- | ---- |
  | 0    | 0    | 1    |
  | 0    | 1    | 1    |
  | 1    | 0    | 1    |
  | 1    | 1    | 0    |

### (2) 或非

- **先 或 后 非**

  | A    | B    | Y    |
  | ---- | ---- | ---- |
  | 0    | 0    | 1    |
  | 0    | 1    | 0    |
  | 1    | 0    | 0    |
  | 1    | 1    | 0    |

### (3) 与或非

- **先 与 在 或 后 非**

  | A    | B    | Y1   | C    | D    | Y2   | Y    |
  | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
  | 0    | 0    | 0    | 0    | 0    | 0    | 1    |
  | 0    | 0    | 0    | 0    | 1    | 0    | 1    |
  | 0    | 0    | 0    | 1    | 0    | 0    | 1    |
  | 0    | 0    | 0    | 1    | 1    | 1    | 0    |
  | 0    | 1    | 0    | 0    | 0    | 0    | 1    |
  | 0    | 1    | 0    | 0    | 1    | 0    | 1    |
  | 0    | 1    | 0    | 1    | 0    | 0    | 1    |
  | 0    | 1    | 0    | 1    | 1    | 1    | 0    |
  | 1    | 0    | 0    | 0    | 0    | 0    | 1    |
  | 1    | 0    | 0    | 0    | 1    | 0    | 1    |
  | 1    | 0    | 0    | 1    | 0    | 0    | 1    |
  | 1    | 0    | 0    | 1    | 1    | 1    | 0    |
  | 1    | 1    | 1    | 0    | 0    | 0    | 0    |
  | 1    | 1    | 1    | 0    | 1    | 0    | 0    |
  | 1    | 1    | 1    | 1    | 0    | 0    | 0    |
  | 1    | 1    | 1    | 1    | 1    | 1    | 0    |

### (4) 异或

- **异 就输出 1**

- A' * B +A * B'

  | A    | B    | Y    |
  | ---- | ---- | ---- |
  | 0    | 0    | 0    |
  | 0    | 1    | 1    |
  | 1    | 0    | 1    |
  | 1    | 1    | 0    |

### (5) 同或

- **同 就输出 1 **

- A' * B' + A*B

  | A    | B    | Y    |
  | ---- | ---- | ---- |
  | 0    | 0    | 1    |
  | 0    | 1    | 0    |
  | 1    | 0    | 0    |
  | 1    | 1    | 1    |



## 4. 逻辑代数的基本公式

### (1) 基本公式

![QQ截图20220630134726](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630134726.png?raw=true)

**Important:**

- **(A * B)'  = A' + B'**
- **A + B * C = (A+B) * (A +C)**
- **(A + B)' = A' * B'**

**公式（17）的证明：**

右 = （A + B）*（A + C） = A + A * B + A * C + B * C 

​     = A（1 + B + C）+  B * C

​     = A + B * C = 左

**德 · 摩根定理：**（公式8，18）

### (2) 常用公式

![QQ截图20220630140513](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630140513.png?raw=true)

- 公式22： A + A' * B = (A + A') * (A + B) = 1 * (A + B) = A + B

- 公式25： A * B + A' * C + (A + A') * B * C = A * B+A * B * C+A' * C+A' * B * C = A * B + A * C'

- 公式26： A * (A * B)' = A * (A' + B') = A * B'

​                        A' * (A * B) '= (A + A * B)' = A'

## 5. 逻辑代数的基本定理

### (1) 代入定理

- **在任何一个包含A的逻辑等式中，若以另外一个逻辑式代入式中A的位置，则等式依然成立** 。
- 相当于数学中的**“换元”**，可以使逻辑公式千变万化。

### (2) 反演定理

- **对于任意一个逻辑式Y，若将其中所有的“ * ”换成“ + ”，“ + ”换成“ * ”，0换成1，1换成0，原变量换成反变量，反变量换成原变量，则得到的结果就是 Y‘ 。**
- 反演定理位求取已知逻辑式的反逻辑式提供了方便。
- 仍需遵守“先括号，然后乘，最后加”的运算优先顺序。
- 不属于单个变量上的反号应保留不变。

应用举例

Y = A * (B + C) + C * D

Y' = (A' + B' * C') * (C' + D')

- 反演定理在数字电路实现过程中意义不大

### (3) 对偶定理

- 若两逻辑式相等，则它们的对偶式也相等，这既是对偶定理。

- 对偶式

  对于任何一个逻辑式，若将其中所有的“ * ”换成“ + ”，“ + ”换成“ * ”，0换成1，1换成0，则得到一个新的逻辑式Yd，这个Yd就称为Y的对偶式，互为对偶式。

- Y = A * (B + C)        Yd = A + B * C

  Y = (A * B + C * D)'         Yd = ( (A + B) * (C + D) )'

  Y = A * B + (C + D)'        Yd = (A + B) * (C * D)'

## 6. 逻辑函数及其描述方法

### (1) 逻辑函数

- 逻辑函数    Y = F(A,B,C, ......)

  若以逻辑变量为输入，运算结果为输出，则输入变量值确定以后，输出的取值也随之而定，输入输出之间是一种函数关系。

### (2) 逻辑函数的描述方法

- 真值表、逻辑式、逻辑图、波形图、卡诺图、EDA中的硬件描述语言。
- 各种方法之间可以相互转换（同一种逻辑关系在不同情况下的编码方式）。

#### i 描述方法

**真值表**

<img src="https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220630152113.png?raw=true" />

- 输入变量要遍历所有可能的输入变量的取值组合，输出变量可以是多输出。

**逻辑式**

- 将输入输出之间的逻辑关系用**与或非**的运算式表示就得到逻辑式。

**逻辑图**

- 用逻辑图形符号表示逻辑运算关系，与逻辑电路的实现相对应。

**波形图**（时序图）

- 将输入变量所有取值可能与对应输出时间按时间顺序排列起来画成时间波形。

<img src="https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701101617.png?raw=true" />

#### ii 相互转换

- 真值表——逻辑式

  - 找出真值表中使逻辑函数Y = 1 的那些输入变量取值的组合。
  - 每组输入变量取值的组合对应一个乘积项，其中取值为1的写入原变量，取值为0的写入反变量。
  - 将这些乘积项相加，即得到Y的逻辑式

  - 例![QQ截图20220701104433](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701104433.png?raw=true)

    在输入变量取值为一下四种情况时，Y 等于 1：、

    A = 0 、B = 0、 C = 0；A = 0、B = 1、 C = 1；A = 1、 B = 0、 C = 1；A = 1、B = 1、C = 0；

    因此    Y = A' * B' *C' + A' * B * C + A * B' * C + A * B * C'

- 逻辑式——逻辑图

  - 若题目有要求，则需要对逻辑式进行等效处理。

  - 用图形符号代替逻辑式中的运算逻辑符。
  - 从输入到输出逐级写出每个图形符号对应的逻辑运算式。

- 波形图——真值表

  要求波形图是完整的

### (3) 逻辑函数的两种标准形式


#### **最小项m**

- m 是乘积项
- 包含 n 个因子
- n 个变量均以原变量和反变量的形式在m中出现一次
- 对于 n 变量函数有 2^n 个最小项

**例**

- 两变量A、B的最小项

  A' * B', A' * B, A * B', A * B

三变量最小项的编号表

![QQ截图20220701111538](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701111538.png?raw=true)

**性质**

- 在输入变量的任意取值下，有且仅有一个最小项的值为1。
- 全体最小项之和为1。

- 任何两个最小项之积为0。

- 两个相邻最小项之和可以合并，消去一对因子，只留下公共因子。（相邻：仅有一个变量不同的最小项，如：A' * B * C'与A‘ * B * C ）

**逻辑函数最小项之和的形式：**

- 例： Y(A, B, C) = A * B * C' + B * C = A * B * C' + B * C * (A + A') = A * B * C ' + A *  B * C + A' * B * C = SIGEMA m(3, 6, 7)

#### 最大项M

- M 是相加项
- 包含n个因子
- n个变量均以原变量和反变量的形式在M中出现一次

**例**

- 两变量A、B的最大项

  A’ + B‘，A’ + B，A + B‘，A + B

三变量最大项的编号表

![QQ截图20220701113429](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701113429.png?raw=true)

**性质**

- 在输入变量的任何取值下必有一个最大项，而且只有一个最大项的值为0；
- 全体最大项之积为0；
- 任意两个最大项之和为1；
- 只有一个变量不同的最大项的乘积等与各相同变量之和。

**最小项和最大项的关系**

**Mi = mi’**

例如：m0 = A' * B' * C' ，则m0‘ = (A' * B' * C')' = A + B + C = M0



## 7. 逻辑函数的化简方法

- 逻辑函数的最简形式

Y1 = A * B * C + B' * C + A * C * D = (A * B + B') * C+A * C * D = (A + B') * C + A * C * D = A * C * (1 + D) + B' * C

Y2 = A * C + B' * C

- 最简与或：

  包含的乘积项已经最少，每个乘积项的因子也最少，称为最简的与或逻辑式

### (1) 公式化简法

- 反复应用基本公式和常用公式，消去多余的乘积项和多余的因子，求得最简形式

1. 并项法：利用 A * B + A * B' = A

![QQ截图20220701133636](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701133636.png?raw=true)

![QQ截图20220701133445](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701133445.png?raw=true)

2. 吸收法：利用 A + A * B = A

![QQ截图20220701133758](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701133758.png?raw=true)

3. 消项法：利用 A * B + A' * C + B * C = A * B + A' * C  以及  A * B + A' * C + B * C * D = A * B + A' * C

   ![QQ截图20220701134055](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701134055.png?raw=true)

4. 消因子法：利用 A + A’ * B = A + B

![QQ截图20220701134310](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701134310.png?raw=true)

![QQ截图20220701134237](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701134237.png?raw=true)

5. 配项法：

   i 利用 A + A = A

![QQ截图20220701134809](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701134809.png?raw=true)



​        ii 利用 A + A' = 1

![QQ截图20220701135048](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701135048.png?raw=true)

![QQ截图20220701135055](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701135055.png?raw=true)

### (2) 卡诺图化简法

#### 卡诺图

- **实质：将逻辑函数的最小项之和以图形的方式表示出来**

- 以 2^n个小方块分别代表 n 变量的所有最小项，并将它们排列成矩阵，而且使几何位置相邻的两个最小项在逻辑上也是相邻的（只有一个变量不同），就得到表示 n 变量全部最小项的卡诺图

二到五变量最小项的卡诺图

![QQ截图20220701140925](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701140925.png?raw=true)

- **几何相邻性，即几何位置上相邻，左右上下**
- **对称相邻性，即图形中对称位置的单元是相邻的**

图b是由图a以最右边为轴对称过去的，相对称的两个单元格是相邻的，同理，图c是由图b对称过去的，上下对称，图d是在图c基础上对称过去的，原本的对称关系还在，新增了一面与一面的对称搞关系，左右中间的四个也具有对称关系。

#### 用卡诺图表示逻辑函数

- **将函数表示为最小项之和的形式 SIGEMA mi**
- **在卡诺图上与这些最小项对对应的位置上填入一，其余地方填0**

例 

![QQ截图20220701144401](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701144401.png?raw=true)

首先将 Y 化为最小项之和的形式

![QQ截图20220701144446](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701144446.png?raw=true)

画出四变量最小项的卡诺图，在对应于函数式中各最小项的位置上填入1，其余位置上填入0，就得到函数 Y 的卡诺图：

![QQ截图20220701144456](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701144456.png?raw=true)

- **其实可以不用将 Y 化为最小项之和，可以直接根据原始式填卡诺图**

tip：只有0/1，千万别2

#### 用卡诺图化简逻辑函数

- **依据：具有相邻性的最小项可合并，消去不同的因子**

- **最小项的相邻性可以从图形中直观地反映出来**

- **合并最小项的原则：**
  - **两个相邻的最小项可合并为一项，消去一对因子**
  - **四个排成矩形的相邻最小项可合并为一项，消去两对因子**
  - **八个相邻最小项可合并为一项，消去三对因子**

- **化简步骤：**
  - **用卡诺图表示逻辑函数**
  - **找出可合并的最小项**
  - **合并后的项中只包含矩形中的公共因子**
  - **化简后的乘积项相加**（化简结果不唯一，但项数为一且最小）

- **化简原则**
  - **化简后的乘积项应包含函数式的所有最小项，即覆盖图中所有的1**
  - **乘积项的数目最少，即围成的矩形最少**
  - **每个乘积项因子最少，即围成的矩形最大、**
  - **每个圈要有一个其专属的新鲜的独属于自己的“1”**

![QQ截图20220701153508](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701153508.png?raw=true)

例：![QQ截图20220701154640](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701154640.png?raw=true)

画出卡诺图，并画出合并方案：

![QQ截图20220701154721](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701154721.png?raw=true)

得到结果：Y = A * B‘ + A’ * C + B * C‘         

例：![QQ截图20220701155431](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701155431.png?raw=true)

画出卡诺图，并画出合并方案：

![QQ截图20220701155538](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220701155538.png?raw=true)

得到结果：Y = A + D'

- **当发现卡诺图中1很多，那么我们可以把圈“1”改为圈“0”，即把”1“视为“0”，把“0”视为“1”，这样做出的结果取反（利用摩根定理）即可得到结果。**

### 	(3) Q - M法

- 卡诺图和公式法在遇到逻辑变量比较多的情况下很难操作。

- Q - M法适用于编制计算机辅助化简程序，而卡诺图法和公式法没有固定的过程，不适合计算机化简。



## 8. 具有无关项的逻辑函数及其化简



### (1) 约束项、任意项和逻辑函数式中的无关项

- 约束项：在逻辑函数中，某些输入变量的取值（取值组合）受到实际背景的限制而不能出现，那么其对应的最小项恒等于0

- 任意项：在输入变量的某些取值下，其最小项的取值为1/0不影响逻辑函数的值

- 约束项和任意项统称为逻辑函数中的无关项，可以写入可以删除



### (3) 无关项在化简逻辑函数中的应用

- 加入的无关项应与函数式中尽可能多的最小项（包括原有的最小项和已写入的无关项）具有逻辑相邻性
- 合并最小项时，把卡诺图中的X作为1还是0，应以得到的相邻最小项举行组合最大，而且矩形组合数目最少为原则

例：化简具有约束的逻辑函数

![QQ截图20220702121357](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702121357.png?raw=true)

![QQ截图20220702121414](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702121414.png?raw=true)

![QQ截图20220702121325](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702121325.png?raw=true)

改用卡诺图：

![QQ截图20220702122418](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702122418.png?raw=true)

画出卡诺图：

![QQ截图20220702122458](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702122458.png?raw=true)

![QQ截图20220702122517](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702122517.png?raw=true)



## 9. 多输出逻辑函数的化简

- 在化简一组具有相同输入变量的逻辑函数时，可以在卡诺图分组时，尽量多地画出各个卡诺图中相同的公共项，这样得到的逻辑函数可能不是最简的，但在实现逻辑电路时，可以使输出有共同的输入，减少门电路和连线的数目。

例：![QQ截图20220702134330](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702134330.png?raw=true)

![QQ截图20220702134347](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702134347.png?raw=true)

![QQ截图20220702134401](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702134401.png?raw=true)





# 三、门电路

## 1.概述

- Why digital？

  Because it keeps the contracts simple! The price we pay for this robustness:

  All the information that we transfer between modules is only 1 crummy bit!

- Keep in mind that the world is not digital, we would simply like to engineer it to behave that way. Furthermore, we must use real physical phenomena to implement digital designs!

- Using Voltages "Digitally"
  - Key idea: don't allow "0" to be mistaken for a "1" or vice versa
  - Use the same "uniform representation convention" for every component and wire in our digital system to implement devices with high reliability, we outlaw "close calls" via a representation convention which forbids a range of voltages between "0" and "1"

- The digital abstraction
  - Making bits concrete
  - What makes a good bit
  - Getting bits under contract

- 门电路：实现基本运算、复合运算的单元电路，如与门、与非门、或门......
  - 正逻辑：高电平表示1，低电平表示0
  - 负逻辑：高电平表示0，低电平表示1

- 获得高、低电平的的基本原理：高/低电平都允许有一定的变化范围

![QQ截图20220702150008](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702150008.png?raw=true)



## 2. 半导体二极管门电路

- 二极管开关电路：

  ![QQ截图20220702155107](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702155107.png?raw=true)

- 数字电路中二极管的伏安特性及近似方法：

![QQ截图20220702155022](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702155022.png?raw=true)

### (1) 二极管与门

- 电路图：(Vcc = 5V)

  ![QQ截图20220702155412](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702155412.png?raw=true)

- 逻辑电平及真值表

  ![QQ截图20220702155709](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220702155709.png?raw=true)

- 缺点：

  - 输出的高低点电平和输入的高低电平不相等，不能将输出作为下一个的输入
  - 当输出端对地接上负载电阻时，负载电阻的改变有时会影响输出的高电平，带负载能力差


### (3) 二极管或门

- 电路图：![QQ截图20220703101053](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703101053.png?raw=true)

- 逻辑电平及真值表

<img src="https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703101131.png?raw=true" style="zoom:80%;" />



- 二极管或门同样存在着输出点评偏移的问题，只适用于集成电路内部的逻辑单元，无法制作具有标准化输出电平的集成电路

## 3. CMOS门电路（C：Complementary）

### (1) MOS管复习

- MOS管的结构和符号（以N沟道增强型为例）

![QQ截图20220703103723](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703103723.png?raw=true)

- 源极S(Source)、漏极(Drain)、栅极(Gate)

- MOS管的输入输出特性（N沟道增强型，共源）

  - 漏极-源极间为输入回路，加上电压Vgs后不会有栅极电流。

  - 输出特性：

    虚线左边为可变电阻区，Vgs一定时，Id与Vds之比近似为常数

    虚线右边为恒流区，Id大小基本由Vgs决定

![QQ截图20220703105303](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703105303.png?raw=true)

- MOS管的基本开关电路（以N沟道增强型为例）
  - V1 = Vgs < Vgsth 时，MOS工作在截止区，只要负载电组Rd远小于MOS截止内阻，输出即为高电平Voh，约为Vdd，相当于断开的开关
  - V1 > Cgsth 且 Vds较高时，MOS工作在恒流区，电路工作在放大状态
  - V1 继续升高，只要Rd 》Ron，输出端将为低电平Vol，约为0，MOS管的D-S间相当于闭合开关
  - 只要电路参数选择合理，就可以做到输入为低电平时MOS截止，开关电路输出高电平，输入为低电平时，MOS导通，开关电路输出低电平

 ![QQ截图20220703135404](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703135404.png?raw=true)



- MOS管的开关等效电路
  - MOS截止时D-S内阻非常大，视为断路
  - MOS导通时D-S内阻很小，1k以内，不能不计
  - C1几皮法，负载电容不可避免

![QQ截图20220703140116](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703140116.png?raw=true)

- MOS管的四种类型

1. **N沟道增强型**

2. **P沟道增强型**，工作时使用负电源，开启电压Vgsth为负值。当V1 = 0时，MOS管不导通，输出低电平Vol，只要Rd远小于MOS管截止内阻，则Vol约为-Vdd；当V1 < Vgsth时，MOS管导通，输出为高电平Voh，只要Rd远大于MOS管的导通内阻Ron，则Voh约为0

![QQ截图20220703142605](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703142605.png?raw=true)

![QQ截图20220703142620](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703142620.png?raw=true)

![QQ截图20220703144031](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703144031.png?raw=true)

3. N沟道耗尽型，在Vgs = 0时到导电沟道就已经存在，Vgs为正时沟道变宽，Id增大，Vgs为负时沟道变窄，Id减小，直到Vgs小于某一负电压值Vgsoff时，导电沟道才消失，MOS截止，Vgsoff称为夹断电压
4. P沟道耗尽型，在Vgs = 0时到导电沟道就已经存在，Vgs为负时沟道变宽，Id的绝对值增大，Vgs为正时沟道变窄，Id的绝对值减小，当Vgs的正电压大于夹断电压Vgsoff时，导电沟道消失，管子截止。

![QQ截图20220703145249](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703145249.png?raw=true)



### (3) CMOS 反相器的电路结构和工作原理

- CMOS反相器结构与电路图

![QQ截图20220703153002](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703153002.png?raw=true)

当 V1 = 0 时，T1 导通，导通内阻很低，T2 截止，内阻很高，输出为高电平.Voh = Vdd；当V1 = Vdd时，T1 截止而T2导通，输出为低电,Vol = 0。输入输出为逻辑**非**的关系，称为非门或反相器。

- 电压传输特性和电流传输特性

​                                                                        <img src="https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703161722.png?raw=true" alt="QQ截图20220703161722" style="zoom:80%;" />![QQ截图20220703161733](https://github.com/nankedream-tang/NankeDream-s-digital-circuit-note/blob/main/Pictures/QQ%E6%88%AA%E5%9B%BE20220703161733.png?raw=true)

很明显，我们一般利用其电压传输特性，更接近理想的开关开关特性，而不利用电流传输特性，在BC段工作时，器件可能会因功耗过大而损坏











































