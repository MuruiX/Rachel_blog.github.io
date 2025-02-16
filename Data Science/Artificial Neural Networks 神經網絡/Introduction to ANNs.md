---
LINK:
  - "[[Data Science/Artificial Neural Networks 神經網絡/Introduction to ANNs]]"
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
---

## Machine learning (supervised learning definition)

- Given an input x, find an output y
- Classification: y is one of N classes


![](PICTURE/Introduction%20to%20ANNs/017746f009b6703c107a493d83adc95c_MD5.jpeg)

像Supervised Machine Learning

### Neurons 神經元

![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/9a97a633dc51057232c4895e85dd5372_MD5.jpeg)
生物神經元啟發的計算單元

x1 x2 x3 轉換成vector


在神經網絡中有好幾個函數 $f（x）$  （激活函數）

![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/f01a4d4c3798aaa14114e36573be3353_MD5.jpeg)
對於神經元網絡 可能取決於下游任務




### Multi-layer Neural Networks


![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/3da3846fce2dded04125d066526a24f3_MD5.jpeg)

$y_1$ 是隱藏層 hidden Layer



How many hidden layers do we need?
需要至少一層hidden layer


![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/a4122808dbc994b693a7afdc1e4e6001_MD5.jpeg)
In theory, one hidden layer is enough: two-layer neural networks are universal approximators (they are capable of approximating any continuous function to any desired degree of accuracy). 理論上，一個隱藏層就夠了，兩層神經網路是通用近似器（它們能夠近似任何連續函數到任何想要的精確度）。


![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/fafc045ef2ace1e7bf766cdcd0843742_MD5.jpeg)



### Classification Task


![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/ef56823d84e5c3f66357ee6a1cba22a4_MD5.jpeg)


Training a neural net (for classification)
- Training set: D train = {(x1 ,c 1 ),..., (xn ,c n )}, a set of pair x and its correct class c
- Our neural network has parameters θ (the set of all the weight matrices)
- Minimize the cross-entropy loss (i.e., negative log-likelihood)

$$
J(\theta) = \frac{1}{n} \sum_{i=1}^{n} -\log y_{i,c_i} + \frac{\lambda}{2} \|\theta\|_2^2 \equiv -\frac{1}{n} \sum_{i=1}^{n} \log Pr(c_i|\mathbf{x}_i) + \frac{\lambda}{2} \|\theta\|_2^2
$$


### (Minibatch) Stochastic gradient descent


![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/Pasted%20image%2020250202175250.png)

1. sample a minibatch $D′$ of m examples from the training set $D$,  從小批量訓練 $D'$
2. compute $J(θ)$ on D′, 
3. update the parameters: $θ ← θ − η∂J/∂θ$ （計算這裡）
4. if stopping criteria are not met, jump to step 1 如果未能達到停止條件，請挑出步驟一
### Computing gradients: error back-propagation 誤差反向傳播
- Key: the chain rule: $\frac{\partial y}{\partial x} = \frac{\partial z}{\partial x} \frac{\partial y}{\partial z}$


![](Rachel_blog.github.io/PICTURE/Introduction%20to%20ANNs/82061d08773717ee1da59983f3db33a3_MD5.jpeg)

$$
\frac{\partial J}{\partial y^{(2)}} = \frac{\partial J}{\partial y}
$$
$$
\frac{\partial J}{\partial z^{(2)}} = \frac{\partial J}{\partial y^{(2)}} \frac{\partial y^{(2)}}{\partial z^{(2)}} ; \quad \frac{\partial J}{\partial \mathbf{W}_2} = \frac{\partial J}{\partial z^{(2)}} \mathbf{y}^{(1)T} ; \quad \frac{\partial J}{\partial y^{(1)}} = \mathbf{W}_2^T \frac{\partial J}{\partial z^{(2)}}
$$
$$
\frac{\partial J}{\partial z^{(1)}} = \frac{\partial J}{\partial y^{(1)}} \frac{\partial y^{(1)}}{\partial z^{(1)}} ; \quad \frac{\partial J}{\partial \mathbf{W}_1} = \frac{\partial J}{\partial z^{(1)}} \mathbf{y}^{(0)T} ; \quad \frac{\partial J}{\partial y^{(0)}} = \mathbf{W}_1^T \frac{\partial J}{\partial z^{(1)}}
$$
$$
\frac{\partial J}{\partial \mathbf{x}} = \frac{\partial J}{\partial y^{(0)}}
$$

## Summary
Important parts of a neural network:
- Activation function
- Number of layers
- Training:
	- Loss function
	- Stochastic gradient descent




























