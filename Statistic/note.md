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
