# [王道考研 数据结构](https://www.bilibili.com/video/BV1b7411N798)

## 1. 基本概念

- 基本概念
  - 数据
  - 数据元素、数据项
  - 数据对象、数据结构
  - 数据类型、抽象数据类型（ADT）
- 三要素
  - **逻辑结构**
    - 集合
    - 线性结构
    - 树形结构
    - 图状结构（网状结构）
  - **物理结构**（存储结构）
    - 顺序存储
    - 链式存储
    - 索引存储
    - 散列存储
  - **数据的运算**

逻辑结构：

- 线性结构
- 非线性结构

存储结构：

- 顺序存储
- 非顺序存储

数据的存储结构：

- 如果采用顺序存储，则各个数据元素在物理上必须是联系的；若采用非顺序存储，则各个数据元素在物理上可以是离散的。
- 数据的存储结构会影响存储空间分配的方便程度。
- 数据的存储结构会影响对数据运算的速度。

数据的运算：

- 运算的定义是针对逻辑结构的。
- 运算的实现是针对存储结构的。

数据类型是一个值的集合和定义在此几何上的一组操作的总称。

- 原子类型。其值不可再分的数据类型。
- 结构类型。其值可以再分解为若干成分（分量）的数据类型

抽象数据类型（Abstract Data Type，ADT）是抽象数据组织及与之相关的操作。

抽象数据类型只关心：

- 逻辑结构
- 数据的运算

在讨论一种数据结构时：

1. 定义逻辑结构，数据元素之间的关系
2. 定义数据的运算，针对现实需求，应该对这种逻辑结构进行什么样的运算
3. 确定某种存储结构，实现数据结构，并实现一些对数据结构的基本运算

## 2. 算法

程序 = 数据结构 + 算法

- 数据结构：如何把现实世界的问题信息化，将信息存进计算机。同时还要实现对数据结构的基本操作。
- 算法：如何处理这些信息，以解决解决实际问题。

算法的特性：

- 有穷性：一个算法必须总在执行有穷步之后结束，且每一步都可在有穷时间内完成。
- 确定性：算法中每条指令必须有明确的含义，对于相同的输入只能得到相同输出。
- 可行性：算法中描述的操作都可以通过已经实现的基本运算执行有限次来实现。
- 输入：一个算法有零个或多个输入，这些输入取自于某个特定的对象的集合。
- 输出：一个算法有一个或多个输出，这些输出是与输入有着某种也行关系的量。

算法必须是有穷的，而程序可以是无穷的。

“好”算法的特质：

- 正确性：能正确解决问题。
- 可读性：无歧义地描述每步操作。
- 健壮性：输入非法数据时，算法能够适当地做出反应或进行处理，而不会产生莫名其妙的输出结果。
- 高效率和低存储量需求：执行速度快，时间复杂度低；不费内存，空间复杂度低。

### 2.1. 时间复杂度

时间开销 $T(n)$ 与问题规模 $n$ 的关系。

1. 找到一个基本操作（最深层循环、递归型循环）
2. 分析改基本操作的执行次数 $x$ 与问题规模 $n$ 的关系 $x=f(n)$
3. $x$ 的数量级 $O(x)$ 就是算法时间复杂度 $T(n)$

用 $O$ 表示同阶，同等数量级。即当 $n\to+\infty$ 时，二者之比为常数。

- $T_1(n)=O(n)$
- $T_2(n)=O(n^2)$
- $T_3(n)=O(n^3)$

$$
T(n)=O(f(n))
\iff
\lim \limits_{n\to+\infty} \frac{T(n)}{f(n)}=k
$$

**加法规则**（只保留更高阶的项）：

$$
T(n)
=T_1(n)+T_2(n)
=O(f(n)) + O(g(n))
=O(max(f(n),g(n)))
$$

**乘法规则**：

$$
T(n)
=T_1(n) \times T_2(n)
=O(f(n)) \times O(g(n))
=O(f(n) \times g(n))
$$

举例：

$$
\begin{aligned}
T_3(n)
&=n^3+n^2log_2n \\
&=O(n^3)+O(n^2log_2n) \\
&=O(n^3)
\end{aligned}
$$

算法的时间复杂度（**常对幂指阶**）：

$$
O(1)
\lt
O(log_2n)
\lt
O(n)
\lt
O(nlog_2n)
\lt
O(n^2)
\lt
O(n^3)
\lt
O(2^n)
\lt
O(n!)
\lt
O(n^n)
$$

- 结论一：顺序执行的代码只会影响常数项，可以忽略。
- 结论二：只需挑循环中的一个基本操作，分析它的执行次数与 $n$ 的关系即可。
- 结论三：如果有多层嵌套循环，只需关注最深层循环循环了几次。

查找长度为 $n$ 的数组中的一个元素：

最好情况

$$
T(n)=O(1)
$$

最坏情况

$$
T(n)=O(n)
$$

平均情况：被查找的元素出现在任意位置的概率相同，都为 $\frac{1}{n}$

$$
T(n)
=(1+2+3+...+n) \times \frac{1}{n}
=\frac{1+n}{2}
=O(n)
$$

计算时间复杂度情况：

- 最好时间复杂度
- **最坏时间复杂度**
- **平均时间复杂度**

> 算法的性能问题只有在 $n$ 很大时（$n\to+\infty$）才会暴露出来。

### 2.2. 空间复杂度

空间开销（内存开销） $S(n)$ 与问题规模 $n$ 的关系。

普通程序只需要关注存储空间大小与问题规模相关的变量：

1. 找到所占空间大小与问题规模相关的变量。
2. 分析所占空间 $x$ 与问题规模 $n$ 的关系 $x=f(n)$。
3. $x$ 的数量级 $O(x)$ 就是算法时间复杂度 $S(n)$。

函数递归调用带来的内存开销。（函数调用栈）

空间复杂度 = 递归调用的深度。也有的情况，每一层递归调用的空间大小不一样。

递归程序：

1. 找到递归调用的深度 $x$ 与问题规模 $n$ 的关系 $x=f(n)$。
2. $x$ 的数量级 $O(x)$ 就是算法时间复杂度 $S(n)$。
3. 有的算法各层函数所需的存储空间不同，分析方法略有差别。

加法规则：

$$
O(f(n)) + O(g(n))
=O(max(f(n),g(n)))
$$

乘法规则：

$$
O(f(n)) \times O(g(n))
=O(f(n) \times g(n))
$$

常对幂指阶：

$$
O(1)
\lt
O(log_2n)
\lt
O(n)
\lt
O(nlog_2n)
\lt
O(n^2)
\lt
O(n^3)
\lt
O(2^n)
\lt
O(n!)
\lt
O(n^n)
$$
