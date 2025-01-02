# statistical concept 統計學概念

## PMF and CDF

PMF定義的值是P(X=x)，而CDF定義的值是P(X <= x)，x為所有的實數線上的點。

### probability mass function (PMF) 概率質量函數

$$
pX(x)=P(X=x)
$$

是離散隨機變數在各個特定取值上的概率。有時也被稱為**離散密度函數**。

概率密度函數通常是*定義離散隨機分佈的主要方法*，

並且此類函數存在於其定義域是：

1. 離散的純量變數
2. 多遠隨機變數

[維基百科](https://zh.wikipedia.org/zh-tw/%E6%A6%82%E7%8E%87%E8%B4%A8%E9%87%8F%E5%87%BD%E6%95%B0)

### Cumulative distribution function(CDF)累積分佈函數

$$
FX(x)=P(X<=x)
$$

也叫概率分佈函數或分佈函數

是概率密度函數的**積分**

能夠完整的描述一個實隨機變數X的概率分佈

[維基百科](https://zh.wikipedia.org/zh-tw/%E7%B4%AF%E7%A7%AF%E5%88%86%E5%B8%83%E5%87%BD%E6%95%B0)

## probability density function（PDF）概率密度函數

[PDF](https://www.geeksforgeeks.org/probability-density-function/)

[概率密度函數（Probability Density Function， PDF）-CSDN博客](https://blog.csdn.net/YHKKun/article/details/137404224)

## Central Limits 中央界限

Support we have a set of independent random variables $X_{i}$ for $i=1,....,n$ with:

$Mean(X_{i})=\mu$        $Var(X_{i})=V$       for all $i$

Then as $n$ becomes large, the sum:

$$
S_{m}=\sum\limits_{i = 1}^n {{X_i} \to {\rm N}(n\mu ,nV)}
$$

**tends to become normally distributed.**

### Absence of Central Limits

**Another case is where the moments are not defined / infinite 另一種情況是力矩不確定或無限大**

# Randomness 隨機性

## Motivation 動機

Three main ways that random comes into data science:

1. The data themselves are often best understood as random 數據本身通常最好被理解為隨機
2. **When we want to reason under **subjective uncertainty **(for example in Bayesian approaches) then unknown quantities can be represented as random. Often when we make predictions they will be **probabilitic 當我們主管不確定性的情況下進行推理時，可以將未知量表示為隨機量，當我們進行預測時，他們將是概率性的
3. Many of the most effective / efficient / commonly‑used algorithms in data science—typically called Monte Carlo algorithms—exploit randomness. 蒙特卡洛算法

- Unpredictable 不可預測性
- Subjective uncertainty 主管不確定性

## The logistic map 邏輯地圖（單峰映象）

是一個二次多項式映射(遞歸關係)经常作为典型范例来说明复杂的混沌现象是如何从非常简单的非线性动力学方程中产生的。

is an example of deterministic chaos 是確定性混沌的一個例子 but whose results are apparently not easy to predict. 結果不容易被預測

它在一定程度上是一个时间离散的人口统计模型

Logistic模型可以描述生物種群的演化，它可以表示成一維非線性迭代方程 $x_{n+1}=rx_{n}(1-x_{n})$

其中 $𝑥_{𝑛}$  表示种群的个数，第一项表示第n+1代与第n代成正比，第二项表示环境因素对种群繁殖数目的限制。当然我们已经假定$𝑥$ 大于零且小于一,$𝑟$大于零且小于四（显然）。他们之间的函数关系为抛物线型。这是一种典型的负反馈机制（单峰），logistic模型是二次函数关系，当然我们还可以设定为sin之类的函数。因为单峰是一种最简单，也是自然界最常见的一种负反馈机制

Math:

$$
\displaystyle{ x(t+1)=\mu x(t)(1-x(t)) }
$$

其中，t为迭代时间步，对于任意的t，x(t)∈[0,1]，μ为一可调参数，为了保证映射得到的x(t)始终位于[0,1]内，则μ∈[0,4]。x(t)为在t时刻种群占最大可能种群规模的比例（即现有人口数与最大可能人口数的比率）。当变化不同的参数μ时，该方程会展现出不同的动力学极限行为（即当t趋于无穷大，x(t)的变化情况），包括：稳定点（即最终x(t)始终为同一个数值）、周期（x(t)会在2个或者多个数值之间跳跃)、以及混沌（x(t)的终态不会重复，而会等概率地取遍某区间）。

当μ超过[1,4]时，就会发生混沌现象。该非线性差分方程意在观察两种情形:
• 当人口规模很小时，人口将以与当前人口成比例的速度增长进行繁殖。
• 饥饿(与密度有关的死亡率) ，其增长率将以与环境的”承受能力”减去当前人口所得值成正比的速度下降

然而，Logistic映射作为一种人口统计模型，存在着一些初始条件和参数值(如μ >4)为某值时所导致的混沌问题。这个问题在较老的瑞克模型中没有出现，该模型也展示了混沌动力学。

$0<=μ<=1$:

![1735432764631](image/note/1735432764631.png)

$1<μ<3$:

![1735432855695](image/note/1735432855695.png)

从图中得知：

当$μ$在1到2之间，种群数量会很快接近 $ \frac{μ−1}{μ}$ ,不论最初种群为何值
当$μ$在2到3之间，人口数在经历一段时间的波动后会趋于稳定值 $\frac{μ−1}{μ}$,其收敛速度满足线性变化。但当μ=3时，比线性收敛还要缓慢。

事实上，只要μ < 3 μ<3μ<3，系统都会收敛到一个不动点，而这个不动点的数值可以通过求解下列方程而得到：

$$
X^{*}=\mu x^{*}(1-x^{*})
$$

不同参数 μ \muμ下的极限行为
不论μ取任意值，最多有一个稳定的周期。 如果存在一个稳定的周期，那么它是全局稳定的，吸引了几乎所有的点。一些具有周期稳定循环的μ在某些时候会有无穷多个不同周期的不稳定循环。

为了概括上述各种数值模拟试验的结果，我们用下面的相图来表示不同μ值对应的极限行为

### Feigenbaum图

![1735433138747](image/note/1735433138747.png)

### Code operation 實現操作

```python
# Define a function that does one step of the logistic map
def logisticMap(x,r):
    return r*x*(1.0-x)
```

```python
# Construct an orbit of the logistic map
nSteps = 100
t = range(0,(nSteps + 1))
r = 3.9
x = np.zeros(nSteps + 1) # initialise the result as a vector of zeroes 從0開始
x[0] = 0.1 # Choose the initial condition
for i in range(1,(nSteps + 1)):
    x[i] = logisticMap(x[i-1],r)
```

```python
# Plot the results of the previous step
plt.plot(t, x, '-', linewidth=1,color='black')
plt.scatter( t, x, color="darkviolet" ) # add dots at the points
plt.title('Logistic Map: r=' + str(r))
plt.xlabel('Step, n')
plt.ylabel('x(n)')
plt.show()
```

![1735475233662](image/note/1735475233662.png)

[Logistic Mapping - Encyclopedia - Complex Systems|Artificial Intelligence|Complex Science|Complex Networks|Self-Organizing](https://wiki.swarma.org/index.php?title=Logistic%E6%98%A0%E5%B0%84#.5Bmath.5D.5Cdisplaystyle.7B_0.E2.89.A4.CE.BC.E2.89.A41_.7D.5B.2Fmath.5D)

[物流圖 - 維琪百科，自由的百科全書 --- Logistic map - Wikipedia](https://en.wikipedia.org/wiki/Logistic_map)

[Logicstic映射](https://blog.csdn.net/qq_41137110/article/details/115249684)

[Logistic映射（编程训练） - 知乎](https://zhuanlan.zhihu.com/p/578152437)

[Logistic.nb.pdf](https://abel.math.harvard.edu/archive/118r_spring_99/doc/proj/2/Logistic.nb.pdf)

## entropy 熵

另一种方法是利用计算机外部因素来产生随机性， 例如鼠标点击的位置和时间。 在此， 我们将考虑把代码运行的时间作为外部因素

即使用系统时钟当前时间的小数点后六位数字（分辨率为微秒）

R和Matlab 使用軟件包提供隨機數生成的函數

## Estimation of $π$ **using Monte Carlo methods**

假設我們將 $\pi$ 定義為半徑為1的圓的面積根據其定義來估算這個數字，

we will pick random values of $x$ and $y$ independently from a uniform distribution between 0 and **1**, then let the random variable $Z$ equal 1 if the point $(x, y)$ falls within the quarter-circle shown and 0 otherwise. This $Z$ allows us to make an estimate of $π$ **in that its expected value, $E[Z] = π/4$**. We can then define a random variable **A**n to be the average of $n$ **independent samples of $Z$**. Formally:

$$
{{\rm{A}}_n} = \frac{1}{n}\sum\limits_{i = 1}^n {{Z_i} = \frac{\pi }{4} + {\varepsilon _n}}
$$

### Code operation

To deal with this, we'll repeat the experiment $m$ times and make a list of all the estimates

we get. We'll then arrange these results in ascending order and throw away a certain fraction $\alpha$ of the largest and smallest results. The remaining values should provide decent upper and lower bounds for an interval containing $\pi$.

```python
m = 100 # Number of estimates taken
n = 80000 # Number of points used in each estimate
```

If we increase $n$ above, we should get a more accurate estimates of $\pi$ each tme we run the experiment, while if we increase $m$, we'll get more accurate estimates of the endpoints of an interval containing $\pi$.

```python
#Generate a set of m estimates of the area of a unit-radius quarter-circle
np.random.seed(42) # Seed the random number generator
A = np.zeros(m) # A will hold our m estimates
for i in range(0,m):
    for j in range(0,n):
        # Generate an (x, y) pair in the unit square
        x = np.random.rand()
        y = np.random.rand()
    
        # Decide whether the point lies in or on
        # the unit circle and set Z accordingly
        r = x**2 + y**2
        if ( r <= 1.0):
            Z = 1.0
        else:
            Z = 0
        
        # Add up the contribution to the current estimate
        A[i] = A[i] + Z
       
    # Convert the sum we've built to an estimate of pi
    A[i] = 4.0 * A[i] / float( n )
```

```python
# Calculate approximate 95% confidence interval for pi based on our Monte Carlo estimates
pi_estimates = np.sort(A)
piLower = np.percentile(pi_estimates,2.5)
piUpper = np.percentile(pi_estimates,97.5)
print(f'We estimate that pi lies between {piLower:.3f} and {piUpper:.3f}.')
```

# standard distribution

## Bernoulli 伯努利分佈

$$
P(X=x) = p^{x}(1-p)^{1-x}, x = 0, 1; 0 < p < 1
$$

only have two choices(binary situations). 只有兩個結果 例如成功失敗 硬幣正反面

****Random Variable (X):**** In the context of Bernoulli Distribution, X represents the variable that can take the values 1 or 0, denoting the number of successes occurring.

****Bernoulli Trial:**** An individual experiment or trial with only two possible outcomes.

****Bernoulli Parameter:**** This refers to the probability of success (p) in a Bernoulli Distribution.

Mean:

$$
E[X] = μ = p
$$

Variance:

$$
Var[X] = E[X^{2}] - (E[X])^2
      \\ =σ2 = p(1 - p) \ or\  pq
$$

###### **Applications of Bernoulli Distribution in Business Statistics**

****1. Quality Control:**** In manufacturing, every product undergoes quality checks. Bernoulli Distribution helps assess whether a product passes (success) or fails (failure) the quality standards. By analysing the probability of success, manufacturers can evaluate the overall quality of their production process and make improvements.

****2. Market Research:**** Bernoulli Distribution is useful in surveys and market research when dealing with yes/no questions. ****For instance,**** when surveying customer satisfaction, responses are often categorised as satisfied (success) or dissatisfied (failure). Analysing these binary outcomes using Bernoulli Distribution helps companies gauge customer sentiment.

****3. Risk Assessment:**** In the context of risk management, the Bernoulli Distribution can be applied to model events with binary outcomes, such as a financial investment succeeding (success) or failing (failure). The probability of success serves as a key parameter for assessing the risk associated with specific investments or decisions.

****4. Marketing Campaigns:**** Businesses use Bernoulli Distribution to measure the effectiveness of marketing campaigns. ****For instance,**** in email marketing, success might represent a recipient opening an email, while failure indicates not opening it. Analysing these binary responses helps refine marketing strategies and improve campaign success rates.

###### Difference between Bernoulli Distribution and Binomial Distribution 伯努利分佈和二項分佈的區分

The Bernoulli Distribution and the Binomial Distribution are both used to model random experiments with *binary outcomes*, but they differ in how they handle multiple trials or repetitions of these experiments. 同樣是對具有二元結果的隨機實驗進行建模，但在處理多次實驗的方式上有所不同

| Basis                                 | Bernoulli Distribution                              | Binomial Distribution                                                                                             |
| ------------------------------------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| ****Number of Trials****  | Single trial                                        | Multiple trials                                                                                                   |
| ****Possible Outcomes**** | 2 outcomes (1 for success, 0 for failure)           | Multiple outcomes (e.g., success or failure)                                                                      |
| ****Parameter****         | Probability of success is p                         | Probability of success in each trial is p and the number of trials is n                                           |
| ****Random Variable****   | X can only be 0 or 1                                | X can be any non-negative integer (0, 1, 2, 3, ...)                                                               |
| ****Purpose****           | Describes single trial events with success/failure. | Models the number of successes in multiple trials.                                                                |
| ****Example****           | Coin toss (Heads/Tails), Pass/Fail, Yes/No, etc.    | Counting the number of successful free throws in a series of attempts, number of defective items in a batch, etc. |

PMFs:

![1735310609676](image/note/1735310609676.png)

CDFs:

![1735312750410](image/note/1735312750410.png)

[伯努利分佈特性](https://www.geeksforgeeks.org/bernoulli-distribution-in-business-statistics-mean-and-variance/)

## Binomia

represent outcome of a single random 'trial', 它是一種離散分佈

- $n$ is the number of trials 例如民意調查樣本
- $0 \le K \le n$ is the number of successes 成功次數 例如潛在選民表示會投票給我們的候選人的次數
- $q$ is the (typically unknown) 支持我方候選人的選民比例

PMF:

$$


$$

![1735314063328](image/note/1735314063328.png)

CDF:

![1735314709953](image/note/1735314709953.png)

## Poison 泊鬆分佈

PMF:

$$
P(X = k) = {p_k} = {P_o}(k|\lambda ) = \frac{{{\lambda ^k}}}{{k!}}{e^{ - \lambda }}
$$

Mean:

$$
Mean(X)= \lambda
$$

Variance:

$$
Var(X)=\lambda
$$

PMF:

![1735311473403](image/note/1735311473403.png)

CMF:

![1735311555474](image/note/1735311555474.png)

## Beta：

**most commonly used to represent uncertainty in probabilities or proportions** 常用於表示概率或比例的不確定性

Probability density function:

$$
f(x) = Beta(x|\alpha ,\beta ) = B_{\alpha ,\beta }^{ - 1}{x^{\alpha  - 1}}{(1 - x)^{\beta  - 1}}dx
$$

for  $ x \in [0,1] $ and positive  $\alpha ,\beta $

The factor $B_{\alpha ,\beta }^{ - 1}$  is a normalizing constant

It’s chosen so that  $P(0 ≤ x ≤ 1) = 1$ and there is no simple expression for it. Instead, it’s defined as an integral:

$$
{B_{\alpha ,\beta }} = \int_0^1 {{x^{\alpha  - 1}}{{(1 - x)}^{\beta  - 1}}dx}
$$

The mean of the Beta distribution is:

$$
Mean(X)=\frac{\alpha }{{\alpha  + \beta }}
$$

Variance:

$$
Var(X)=\frac{{\alpha \beta }}{{{{(\alpha  + \beta )}^2}(1 + \alpha  + \beta )}}
$$

![1735314804579](image/note/1735314804579.png)

CDF

![1735315209527](image/note/1735315209527.png)

Application

![1735315241672](image/note/1735315241672.png)

## Gamma

is ofen used to model times between events

$$
f(x) = Gamma(x|\kappa ,\theta ) = \frac{1}{{\Gamma (\kappa ){\theta ^\kappa }}}{x^{\kappa  - 1}}{e^{ - x/\theta }}
$$

for positive $x$ and positive $\kappa$, $ \theta$

Mean:

$$
Mean(X)=\kappa \theta
$$

Variance

$$
Var(X)=\kappa \theta^2
$$

PDF

![1735315266727](image/note/1735315266727.png)

CDF

![1735315273039](image/note/1735315273039.png)

## Normal

The Normal **(also called the **Gaussian高斯**) distribution is continuous, with probability density function**

$$
f(x) = {\rm N}(x|\mu ,{\theta ^2}) = \frac{1}{{\sqrt {2\pi {\sigma ^2}} }}{e^{ - \frac{{{{(\chi  - \mu )}^2}}}{{2{\sigma ^2}}}}}
$$

Mean

$$
Mean(X)= \mu
$$

Variance

$$
Var(X)=\sigma^{2}
$$

### **Arithmetic with normally-distributed variables**

Suppose we have two random variables, **X**1 and **X**2 that are independent and are both normally distributed with means **µ**1 and **µ**2 **and variances **σ**12 **and **σ**2 2**, respectively.

#### $W=X_{1}+X_{2}$

will also be normally distributed

mean:

$$
{\mu_{W}}={\mu_{1}} + {\mu_{2}}
$$

variance:

$$
{\sigma^{2}_{W}}={\sigma^{2}_{1}}+{\sigma^{2}_{2}}
$$

#### $Y=aX_{1}+b$

will also be normally distributed

mean:

$$
\mu_{Y}=a\mu_{1}+b
$$

variance:

$$
\sigma^{2}_{Y}=a^{2}\sigma^{2}_{1}
$$

**PDF**

![1735315324363](image/note/1735315324363.png)

CDF

![1735315329536](image/note/1735315329536.png)

## **Cauchy 柯西分佈**

The Cauchy **distribution has probability density function**

$$
f(x) = \frac{1}{{\pi s(1 + {{((x - t)/s)}^2})}}
$$

$s$ is positive $t$ is parameter can be any parameters

**It has “heavy tails”, which means that large values are so common that the Cauchy distribution lacks a well-defined mean and variance!**

But the parameter $t$ **gives the location of the mode and median, which are well-defined.**

The parameter $s$ **determines the ‘width’ of the distribution as measured using e.g. the distances between percentiles, which are also well defined.**

PDF

![1735315340154](image/note/1735315340154.png)

CDF

![1735315356626](image/note/1735315356626.png)

# EDA: Exploratory data analysis

motivation:

    EDA is about getting an intuitive understanding of the data, and as such different people will find different techniques useful.

## Data quality

The first thing understand is where the data come from and how accurate they are. 數據的來源和準確性

### star rating 星級評級

This is based on experience rather than any formal theory：

- 4： Numbers we can believe. Examples: official statistics(官方統計數據); well controlled laboratory experiments
- 3： Numbers that are reasonably accurate. Examples: well conducted surveys / samples; field measurements; less well controlled experiments.
- 2：Numbers that could be out by quite a long way. Examples: poorly conducted surveys / samples; measurements of very noisy systems
- 1： Numbers that are unreliable. Examples: highly biased / unrepresentative surveys / samples; measurements using biased / low-quality equipment
- 0： Numbers that have just been made up. Examples: urban legends / memes; fabricated experimental data

## Univariate Data Vectors

univariate case: one measurement per ‘thing’ 每個變量都單獨探索

Mathematically, we represent a univariate dataset as a length-n vector:

$$
x = (x_{1},x_{2},...,x_{n})
$$

The sample mean of a function f (x) is

$$
\left\langle {{\rm{f}}(x)} \right\rangle  = \frac{1}{n}\sum\limits_{i = 1}^n {f({x_i}) = \frac{1}{n}[f({x_1}) + f({x_2}) + .... + f({x_n})]}
$$

## Visualisation and Information

There is an important distinction in visualisations between

- Lossless(無損) ones from which, if viewed at sufficiently high resolution, one could recover the original dataset
- Lossy(有損) ones, where a given plot would be consistent with many different raw datasets

Typically for complex data, choosing the lossy visualistaion that loses the ‘right’ information is key to successful visualisation.

# Summary Statistics

## Measures of Central Tendency 集中趨勢測度

Often, we are interested in what a typical value of the data;


- The mean of the data is:

$$
Mean(x)=\left\langle {\rm{x}} \right\rangle  = \frac{1}{n}\sum\limits_{i = 1}^n {{x_i}}
$$

- The median of the data is the value that sits in the middle when the data are sorted by value
- A mode in data is a value of $x$ that is ‘more common’ than those around it, or a ‘local maximum’ in the density.
  - **For discrete data[离散数据] this can be *uniquely* determined as the most common value**
  - **For** **continuous data,** modes need to be ***estimated***, one aspect of a major strand in data science, estimating distributions.


### Visualising

For the data, we estimate from the kernel density that there is one mode, and its location and calculate the mean and median directly


> Example: 
>
> The data are **right-skewed(右偏的)**, and as a consequence of this the mode is smallest and the mean is largest – we will consider this further; (note that for a normal distribution all would be equal.)


## Variance


|   特性   |           有偏差方差           |        無偏差方差        |
| :------: | :----------------------------: | :----------------------: |
|   分母   |               n               |           n-1           |
| 應用場景 |        描述樣本的離散型        |      估計總體的方差      |
|   偏差   |  對總體方差的估計存在低估偏差  | 對總體方差的估計是無偏的 |
| 應用場景 | 數據分析、機器學習中的樣本優化 |   統計學中總體方差估計   |

**何时使用？**

* **有偏差方差** ：在机器学习中，通常计算样本的有偏差方差（分母为 nn**n**），因为重点在于优化模型对样本的适配性，而非推断总体。
* **无偏差方差** ：在统计学和推断中，需要用无偏差方差（分母为 n−1n-1**n**−**1**），因为它更准确地估计总体参数。




$$
\begin{array}{ccccc}
Var(x) = \left\langle {{{(x - \left\langle x \right\rangle )}^2}} \right\rangle\\
= \frac{1}{n}\sum\limits_{i = 1}^n {{{({x_i} - \left\langle x \right\rangle )}^2}}\\
=\frac{1}{n}\sum\limits_{i = 1}^n {({x^2}_i - 2{x_i}\left\langle x \right\rangle  + {{\left\langle x \right\rangle }^2})}\\
=\left( {\frac{1}{n}\sum\limits_{i = 1}^n {x_i^2} } \right) + 2\left( {\frac{1}{n}\sum\limits_{i = 1}^n {{x_i}} } \right)\left\langle x \right\rangle + \frac{1}{n}\left( {\sum\limits_{i = 1}^n 1 } \right){\left\langle x \right\rangle ^2}\\
=\frac{1}{n}\left( {\sum\limits_{i = 1}^n {x_i^2} } \right) - {\left( {\frac{1}{n}\sum\limits_{i = 1}^n {{x_i}} } \right)^2}\\
=\left\langle {{x^2}} \right\rangle  - {\left\langle x \right\rangle ^2}
\end{array}
$$


### Unbiased Variance and Computation 無偏方差


$$
\begin{array}{ccccc}
\widehat {Var}(x)  = \frac{n}{{n - 1}}Var(x) \\
= \frac{1}{{n - 1}}\sum\limits_{i = 1}^n {{{({x_i} - \left\langle x \right\rangle )}^2}}\\
= \frac{1}{{n - 1}}\left( {\sum\limits_{i = 1}^n {x_i^2 - \frac{1}{n}{{\left( {\sum\limits_{i = 1}^n {{x_i}} } \right)}^2}} } \right)
\end{array}
$$


默認情況下， python計算有偏差的，R計算無偏差的


[無偏差樣本](https://en.wikipedia.org/wiki/Variance#Population_variance_and_sample_variance)


## 'Natural' units

there are two commonly-used quantities that have the same units as the data 與數據有相同單位

- mean $\mu = Mean(x)$
- standard deviation $\sigma  = \sqrt {Var(x)}$

These two quantities let us define two transformations commonly applied to data 用於數據轉換

- centring ${y_i} = {x_i} - \mu$     |   $Mean(y) = 0$
- standardisation ${z_i} = \frac{{{y_i}}}{\sigma }$  | $Var(z)=1$


## Higher moments

- In general, the $r$-th moment of the data is 第$r$時刻的數據是 ${m_r} = \left\langle {{x^r}} \right\rangle$
- The $r$-th central moment中心距 of the data is   ${\mu _r} = \left\langle {{{(x - \mu )}^r}} \right\rangle  = \left\langle {{y^r}} \right\rangle$

    where the y’s are the centred versions of the data.

- The $r$-th standardised moment of the data is ${\mu _r} = \left\langle {{{(\frac{{x - \mu }}{\sigma })}^r}} \right\rangle  = \left\langle {{z^r}} \right\rangle  = \frac{{\left\langle {{{\left( {x - \mu } \right)}^2}} \right\rangle }}{{{\sigma ^r}}} = \frac{{{\mu _r}}}{{{\sigma ^r}}}$

In theory, all higher moments are informative about the data, but in practice those with r = 3 and r = 4 are most commonly reported


### standardised moment

$$
{M_k} = \frac{{{\mu _k}}}{{{\sigma ^k}}}=\frac{{{原始矩}}}{{{標準差}}}
$$









# Application

## Linear regression

### **Ordinary Least-Squares (OLS) Regression** 普通最小二乘法回歸

$$
P(y|x) = {\rm N}(x|\mu  = \alpha {\rm{x + }}\beta ,{\sigma ^2})
$$

where $\alpha$ , $\beta $ and $\sigma^{2}$ are parameters to-be-fit

![1735320045922](image/note/1735320045922.png)

an OLS model makes probabilitic predictions: the model syas that $y$ is drawn from a normal distribution whose mean depends on $x$ 該模型認為y取自均值取決於x的正態分佈

## Best  estimate 最佳估計值

$$
{p_A}=k/n
$$

# Packages：

## input data

### Python

```python
f = pd.read_csv('file_path')
```

### R

```r
f <- read.table("file_path", header=TRUE,sep=",")
```

## Data wrangling:

### Python

Pandas, Numpy

```python
import pandas as pd
import numpy as np
```

```python
x=f.mag.values
```



#### Summary Statistics

```
np.mean(x)
```


#### Variance

```python
#Baised
up.var(x)
#Unbiased
np.var(x,ddof=1)
```






### R

dplyr

```R
library(dplyr)
```

```r
x <- f$mag
```



#### Summary Statistics

```R
mean(x)
```


#### Variance

```R
#Unbiased
var(x)
#biased
library(momnets)
moment(x, order=2,central=TRUE)
```





## Visualisation

### Python

Seaborn(based on MatplotLib)

```python
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
sns.histplot(magnitudes, stat='density')
sns.kdeplot(magnitudes)
sns.rugplot(magnitudes)
```

![1735488472345](image/note/1735488472345.png)









### R

GGPlot

```
library(ggplot2)
```

```R
ggplot(earthquake.df, aes(x=mag))+
geom_histogram(aes(y=..density..))+
geom_density()+ xlab("Magnitude")
```

![1735488562842](image/note/1735488562842.png)
