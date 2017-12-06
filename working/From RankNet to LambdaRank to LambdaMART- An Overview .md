# From RankNet to LambdaRank to LambdaMART: An Overview 

## RankNet

RankNet的核心做法在于训练底层模型对于物品相关性的评分
$$
s_i=f(x_i)
$$
顶层的loss计算采用
$$
P_{ij}=P(U_i>U_j)=\frac{1}{1+e^{-\sigma(s_i-s_j)}}
$$
然后来优化最大似然，对其取负之后作为loss
$$
C=-P_{ij}\log P_{ij}-(1-P_{ij})\log(1-P_{ij})
$$
对于任意查询，我们认为相关性有三种情况$S_{ij}\in\{0,-1,+1\}$ ，分别表示更相关、同等重要和不如三种比较情况，则
$$
P_{ij}=\frac{1}{2}(1+S_{ij})
$$
然后我们的loss就变成
$$
C=\frac{1}{2}(1-S_{ij})\sigma(s_i-s_j)+log(1+e^{-\sigma(s_i-s_j)})
$$
当$S_{ij}=1$ 时
$$
C=log(1+e^{-\sigma(s_i-s_j)})
$$
$S_{ij}=-1$ 时
$$
C = log(1+e^{-\sigma(s_j-s_i)})
$$
当$S_{ij}=0$ 时，cost为$\log2$ ，这样就节省了很多计算，当计算梯度的时候
$$
\frac{\partial C}{\partial s_i}=\sigma(\frac{1}{2}(1-S_{ij})-\frac{1}{1+e^{\sigma(s_i-s_j)}})=-\frac{\partial C}{\partial s_j}
$$
底层计算相关性评分的模型参数迭代为
$$
w_k\rightarrow w_k-\eta\frac{\partial C}{\partial w_k}=
w_k-\eta(\frac{\partial C}{\partial s_i}\frac{\partial s_i}{\partial w_k}+\frac{\partial C}{\partial s_j}\frac{\partial s_J}{\partial w_k})
$$

## Factoring RankNet

对于RankNet计算时，会有
$$
\begin{aligned}
\frac{\partial C}{\partial w_k}
&=\frac{\partial C}{\partial s_i}\frac{\partial s_i}{\partial w_k}+\frac{\partial C}{\partial s_j}\frac{\partial s_J}{\partial w_k}\\
&=\sigma(\frac{1}{2}(1-S_{ij})-\frac{1}{1+e^{\sigma(s_i-s_j)}})
(\frac{\partial s_i}{\partial w_k}-\frac{\partial s_J}{\partial w_k})\\
&=\lambda_{ij}(\frac{\partial s_i}{\partial w_k}-\frac{\partial s_J}{\partial w_k})
\end{aligned}
$$
其中
$$
\lambda_{ij}=\sigma(\frac{1}{2}(1-S_{ij})-\frac{1}{1+e^{\sigma(s_i-s_j)}})
$$
对于训练样本，我们可以做所有的计算之后再更新一次参数
$$
\delta w_k=-\eta\sum_{\{i,j\}\in I}(\lambda_{ij}\frac{\partial s_i}{\partial w_k}-\lambda_{ij}\frac{\partial s_j}{\partial w_k})=-\eta\sum_i\lambda_i\frac{\partial s_i}{\partial w_k}\\\
\lambda_i=\sum_{j:\{i,j\}\in I}\lambda_{ij}-\sum_{j:{j,i}\in I}\lambda_{ij}
$$
这样做就可以加速RankNet的训练速度。

## LambdaRank





## IR Measures

### DCG@T

$$
\text{DCG@T}=\sum_{i=1}^T\frac{2^{l_i}-1}{\log(1+i)}
$$

其中$l_i$ 是第$i$ 个物品，$l_i\in\{0,1,2,3,4\}$ 通常采用5个级别的相关性。

### NDCG@T

$$
\text{NDCG@T}=\frac{\text{DCG@T}}{\max\text{DCG@T}}
$$

### ERR

$$
\text{ERR}=\sum^n_{r=1}\frac{1}{r}\prod^{r-1}_{i=1}(1-R_i)
$$

其中
$$
R_i=\frac{2^{l_i}-1}{2^{l_m}}
$$
这个$R_i$ 表示用户在位置$i$ 处找到文档的概率。