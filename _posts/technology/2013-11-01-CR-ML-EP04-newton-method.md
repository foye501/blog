---
layout: default
title: 机器学习CR-EP04：牛顿方法【存疑】
---
这节课的主要内容包括：
1. 逻辑回归中的牛顿方法(Newton Method)
2. 指数分布族(Exponential Family)
3. 广义线性模型(Generalized Linear Models)

Andrew先回顾了上节课讲的逻辑回归方法，在逻辑回归方法中，即便是优化了计算（不遍历数据集而是使用某个数据元素来更新θ_{i}），他的速度也是不快的。而下面要讲的一种新的方法的收敛速度更快，这就是：

##### 牛顿方法(Newton Method)

牛顿方法是也是先选择某个初始值θ_{0}，根据该点在数据集连线上的切线与x轴相交的位置作为下一个点，也就是θ_{1}...专业，迭代几次之后，就可以看到数据很快的收敛到了0处。

嗯，此处省略大量推导步骤。

##### 小总结

在之前的所有计算中，对于P(y|x;θ)：

* 如果对于y∈R，符合高斯分布，则使用最小二乘法(Least Squares)；
* 如果对于y∈\{0,1\}，符合伯努利分布，则使用逻辑回归(Logistic Regression)。

那么，我们现在要证明，最小二乘法和逻辑回归是一类更广泛的算法的特例！（真是越广泛越牛逼！）

##### 指数分布族(Exponential Family)

要证明最小二乘法和逻辑回归是一类更广泛的算法的特例，首先我们要证明高斯分布和伯努利分布是指数分布族的特例。

指数分布族的式子不好打出来，就不打了，是一个关于a, b, T三个参数的分布函数。具体的看笔记本。证明过程一大堆，最终可以将高斯分布和伯努利分布的表达式转换为指数分布族的形式，只不过他们的a, b, T不同。好了，证明完毕！

##### 广义线性模型(Generalized Linear Models)

有了指数分布族的基础，我们可以来看广义线性模型。这里需要先做三个假设：

1. 认为分布y|x;θ符合指数分布族分布，也就是ExpFamily；
2. 对于给定的x，我们的目标是得到输出为：E\[T(y)|x\]，其中，我们want：h(x) = E\[T(y)|x\]。不过，在一般情况下（包含上面的高斯分布和伯努利分布），T(y) = y。
3. 假定η和x之间的关系是线性的，则有：η = θ^{T}x。

有了这三个假设，我们再次对伯努利分布和高斯分布进行推导，可以得到从广义线性模型推出来的形式就是逻辑回归和线性回归的表达式。

推导过程略！（看的概率渣真痛苦！）

课堂最后，Andrew讲了下广义线性模型的最复杂的一个例子，也就是多项式分布的广义线性模型推广。是挺复杂的：先做了一些符号和概念的定义，之后将多项式分布写成指数分布族的形式，然后将多项式分布写成GLM形式。这种算法叫做Softmax Regression，被认为是Logistic Regression的推广。Logistic Regression是解决二分类问题，而Softmax Regression解决k分类问题。