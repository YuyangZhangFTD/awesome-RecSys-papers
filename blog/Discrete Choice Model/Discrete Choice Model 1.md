# Discrete Choice Model

## Chap1 Introduction

我们的目标是研究：当一个人（agent）面对很多的选择时，行为过程是如何影响最终的决策。
定义可以观测到的影响因素用$x$表示，无法观测的影响因素用$\epsilon$表示，则通过一个函数$y=h(x,\epsilon)$标识用户的选择，这个函数称为行为过程，behavioral process。因为无法观测的变量$\epsilon$所以agent的选择并不是确定的，也无法被准确预测。无法观测的影响因素我们认为它服从一定分布，概率分布为$f(\epsilon)$，则用户behavioral process可以写为$P(y|x)=Prob(\epsilon s.t. h(x,\epsilon)=y)$。定义指示函数$\mathbb{I}[\cdot]$，则有
$$
\begin{aligned}
P(y|x)&=Prob(\mathbb{I}[h(x,\epsilon)=y]=1)\\
&=\int\mathbb{I}[h(x,\epsilon)=y]f(\epsilon)d\epsilon
\end{aligned}
$$
定义效用为
$$
U=\beta'x+\epsilon
$$
当我们假设$\epsilon$ is distributed logistic时，$f(\epsilon)=\frac{e^{-\epsilon}}{(1+e^{-\epsilon})^2}$，累积概率密度为$F(\epsilon)=\frac{1}{1+e^{-\epsilon}}$，则上述概率积分为
$$
\begin{aligned}
P&=\int\mathbb{I}[\beta'x+\epsilon>0]f(\epsilon)d\epsilon\\
&=\int\mathbb{I}[\epsilon>-\beta'x]f(\epsilon)d\epsilon\\
&=\int^{\infty}_{-\beta'x}
f(\epsilon)d\epsilon\\
&=1-F(-\beta'x)\\
&=1-\frac{1}{1+e^{\beta'x}}\\
&=\frac{1}{1+e^{-\beta'x}}
\end{aligned}
$$

## Chap2 Properties of Discrete Choice Models
这张主要讨论所有离散选择模型共有的性质，从选择集（choice set）开始，之后从效用最大行为推导出选择概率，之后展示了如何将individual-level models结合，来进行market-level的预测和如何利用这些模型来对未来进行预测。

### The choice set
用decision-maker表示决策者，用alternatives表示可选决策，可选决策的集合被称为choice set，alternatives必须是相互排斥的，选择一个决策就不能选择另一个，其次，决策必须是详细的，所有的可选都必须涵盖，最后决策必须是有限的。

### Derivation of choice probabilities
一个decision-maker，$n$，面对$J$个可选决策，decision-maker会从中选择效用最大的，$U_{nj},j=1,..,J$，但是这个效用对于decision-maker是已知的，对于研究者却是未知的，decision-maker选择alternative $i$当且仅当$U_{ni}>U_{nj},\forall j\neq i$。
对于研究者，我们可以观测到决策的某些属性，记为$x_{nj}\forall j$，以及decision-maker的一些属性$s_n$，则我们定义一个代表效用（representative utility）为$V_{nj}=V(x_{nj},s_n)$，通常函数$V(\cdot)$由一些研究者确定的未知参数决定。
由于存在无法观测到的影响因素，所以$U_{nj}\neq V_{nj}$，而是应该定义为$U_{nj}=V_{nj}+\epsilon_{nj}$，其中$\epsilon_{nj}$是为包括在$V_{nj}$中的影响因素，因此$\epsilon_{nj}$的属性依，如分布，依赖于研究者对于$V_{nj}$的定义。
通常我们假设其为随机，随机向量$\epsilon_n=\langle\epsilon_1,...,\epsilon_n\rangle$的联合概率密度为$f(\epsilon_n)$，则decision-maker $n$选择alternative $i$的概率为
$$
\begin{aligned}
P_{ni}&=Prob(U_{ni}>U_{nj},\forall j\neq i)\\
&=Prob(V_{ni}+\epsilon_{ni}>V_{nj}+\epsilon_{nj},\forall j\neq i)\\
&=Prob(\epsilon_{nj}-\epsilon_{ni}>V_{ni}-V_{nj},\forall j\neq i)\\
&=\int_\epsilon\mathbb{I}[\epsilon_{nj}-\epsilon_{ni}>V_{ni}-V_{nj},\forall j\neq i]f(\epsilon_n)d\epsilon_n
\end{aligned}
$$
举个例子，一个人可以选择乘车（car）或者乘公交（bus）去上班，研究者观测到时间和花费是这个人会主要考虑的，然而研究者意识到还有很多因素也会影响这个人对于这两种选择的效用，因此研究者定义
$$
\begin{aligned}
V_c=\alpha T_c+\beta M_c\\
V_b=\alpha T_b+\beta M_b
\end{aligned}
$$
其中$T_c$和$M_c$是这个人乘车的时间和花费，$T_b$和$M_b$是乘公交的，系数$\alpha$和$\beta$是已知的或者需要被估计的。
假设我们已知所有参数，并且得到$V_c=4$和$V_b=3$，则对于可观测的影响因素，对于这个人，乘车比乘公交更好，多出一个单位效用。然而这并不是说这个人一定会选择乘车，当为观测到的影响因素产生的效用大于可观测影响因素产生的效用时，就会使这个人选择乘公交，即$\epsilon_b-\epsilon_c>1$时，会选择乘公交。

### Specific models
Logit模型是最被广泛使用的离散选择模型，当每个agent对每个alternatives的选择的无法观测的影响因素满足相互独立的假设时成立，即$\epsilon_{ni}$是独立同分布的时候（极值分布）。这样的假设在某些情况是不恰当的，因为无法观测的影响因素往往是相关联的，比如一个人不喜欢乘坐公交往往也会对地铁有同样的偏好，这样无法观测的影响因素对于公交的影响和对于地铁的影响就有一定关联，独立同分布的假设就不成立了。
广义极值模型（GEV，Generalized Extreme Value）很大程度上可以避免这种问题，GEV有多种形式，但是共同的特点是它允许无法观测的影响因素之间有联系。
Probits模型是基于无法观测的影响因素服从联合正态分布$\epsilon'_n=\langle\epsilon_{n1},...,\epsilon_{nJ}\rangle\sim N(0,\Omega)$，用满秩的协方差矩阵$\Omega$可以刻画变量之间的correlation
and heteroskedasticity。
Mixed logit可以允许无法观测因素服从任意分布，可以分解为两部分，一部分是iid的极值分布，另一部分是有相关性的，这部分可以是任何分布。

### Identification of choice models
效用的大小不重要，效用间的差异比较重要。Only differences in utility matters and the scale of utility is arbitrary.

## Logit

### choice probabilities
当我们假设每个$\epsilon_{nj}$是独立的极值分布时，我们可以用logit model来描述选择模型。
$$
\begin{aligned}
f(\epsilon_{nj})=e^{-\epsilon_{nj}}e^{-e^{-\epsilon_{nj}}}\\
F(-\epsilon_{nj})=e^{-e^{-\epsilon_{nj}}}
\end{aligned}
$$
其方差为$\pi/6$，均值为0。两个极值变量服从logistic分布，$\epsilon^*_{nji}=\epsilon_{nj}-\epsilon_{ni}$，
$$
F(\epsilon^*_{nji})=\frac{\epsilon^*_{nji}}{1+\epsilon^*_{nji}}
$$
decision-maker $n$选择alternative $j$的概率为
$$
\begin{aligned}
P_{ni}&=Prob(V_{ni}+\epsilon_{ni}>V_{nj}+\epsilon_{nj},\forall j\neq i)\\
&=Prob(\epsilon_{nj}<V_{ni}+\epsilon_{ni}-V_{nj},\forall j\neq i)
\end{aligned}
$$
所以有
$$
\begin{aligned}
P_{ni}|\epsilon_{ni}&=\prod_{j\neq i}e^{-e^{-(\epsilon_{ni}+V_{ni}-V_{nj})}}\\
P_{ni}&=\int(\prod_{j\neq i}e^{-e^{-(\epsilon_{ni}+V_{ni}-V_{nj})}})e^{-\epsilon_{ni}}e^{-e^{-\epsilon_{ni}}}d\epsilon_{ni}\\
&=\int^{\infty}_{-\infty}(\prod_{j\neq i}e^{-e^{-(s+V_{ni}-V_{nj})}})e^{-s}e^{-e^{-s}}ds\\
&=\int^{\infty}_{-\infty}(\prod_{j}e^{-e^{-(s+V_{ni}-V_{nj})}})e^{-s}ds\\
&=\int^{\infty}_{-\infty}\exp(-\sum_j e^{-(s+V_{ni}-V_{nj})})e^{-s}ds\\
&=\int^{\infty}_{-\infty}\exp(-e^{-s}\sum_j e^{-(V_{ni}-V_{nj})})e^{-s}ds\\
&=\int^{\infty}_{-\infty}\exp(-t\sum_j e^{-(V_{ni}-V_{nj})})(-dt)\\
&=
\left.\frac{\exp(-t\sum_j e^{-(V_{ni}-V_{nj})})}{-\sum_j e^{-(V_{ni}-V_{nj})}}\right|^{\infty}_0\\
&=\frac{1}{-\sum_j e^{-(V_{ni}-V_{nj})}}\\
&=\frac{ e^{V_{ni}}}{\sum_j e^{V_{nj}}}\\
\end{aligned}
$$
logit模型有以下几个优势：首先它输出的是$[0,1]$的概率，其次所有alternatives的和为1，这表示decision-maker必然会选择一个alternative。

### The scale parameter
如果无法观测的影响因素有方差$\sigma^2*(\pi^2/6)$，则效用应该变为$U_{nj}=V_{nj}/\sigma+\epsilon_{nj}$，
$$
P_{ni}=\frac{e^{V_{ni}/\sigma}}{\sum_j e^{V_{nj}/\sigma}}
$$

### Power and limitations of logit
-  Logit can represent systematic taste variation (that is, taste variation that relates to observed characteristics of the decisionmaker) but not random taste variation (differences in tastes that cannot be linked to observed characteristics)
- The logit model implies proportional substitution across alternatives, given the researcher’s specification of representative utility. To capture more flexible forms of substitution, other models are needed.
- f unobserved factors are independent over time in repeated choice situations, then logit can capture the dynamics of repeated choice, including state-dependence.

