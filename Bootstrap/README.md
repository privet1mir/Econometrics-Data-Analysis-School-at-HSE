# Bootstrap

In this [project](https://github.com/privet1mir/Econometrics-Data-Analysis-School-at-HSE/blob/main/Bootstrap/Bootstrap.ipynb) I have implemented two tasks connected with the bootstrap. 

## Bootstrap from scratch. Laplace distribution parameters estimation. 

Laplace distribution has two parameters $\mu$ and $b$:

$$
f(x|\mu, b) = \frac{1}{2b}\exp(-\frac{|x - \mu|}{b})
$$

We can estimate such parameters in the way: 

Firstly sample n subsamples with a return from our sample and estimate $\hat{\mu}$ each of the subsamples using MLE estimation, which for [Laplace distribution](https://en.wikipedia.org/wiki/Laplace_distribution):

$$\hat{\mu_i} = \mathrm{median}(x_i)$$

$x_i \in$  $i-$ subsample, and final $\mu$ of our initial sample we can estimate as the mean of n-subsamples:

$$\mu = \frac{1}{n}\sum_{i=1}^{n} \hat{\mu_i}$$


We can do the same thing for $\hat{b}$:
$$\hat{b_i} = \frac{1}{k} \sum_{i = 1}^{k} |x_i - \hat{\mu}^k|$$
k - size of subsample. $\hat{\mu}^k$ - it's median.

Estimation of $b$ we can find as:

$$b = \frac{1}{n}\sum_{i=1}^{n} \hat{b_i}$$

---

We can see that our estimation $\mu$ is truly: $$\mu_{real} = 5 \text{ versus } \mu_{estimated} \approx 4.86$$

We can say the same thing of $b$: $$b_{real} = 3 \text{ versus } b_{estimated} \approx 3.01$$

---
## Working with real data. Confidence intervals construction using bootstrap. 

<img src=https://wp.dailybruin.com/images/2019/08/gap-years--910x1024.png width="500" height="500">

We explore will the person will go to college or not. We can imagine that his grades can influence this.

<img src=https://github.com/privet1mir/Econometrics-Data-Analysis-School-at-HSE/blob/main/Bootstrap/density%20graph.png width="500">

After construction the confidence intervals we can see the final result: 

```
conf interval for average students score: from 87.4914045 to 88.11904950000002
conf interval for average gaps score: from 84.2109955 to 84.57082000000001
```

